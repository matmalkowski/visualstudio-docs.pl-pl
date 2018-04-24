---
title: Kompilacje przyrostowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17f33be85a5baf35235721c720386dd237d9ec85
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="incremental-builds"></a>Kompilacje przyrostowe
Kompilacje przyrostowe to kompilacje zoptymalizowane w taki sposób, że elementy docelowe, których pliki wyjściowe mają tak samo aktualną zawartość jak pliki wejściowe, nie są wykonywane. Element docelowy może mieć zarówno atrybut `Inputs`, który wskazuje elementy oczekiwane przez element docelowy na wejściu, oraz atrybut `Outputs`, który wskazuje elementy generowane przez element docelowy na wyjściu. Program MSBuild próbuje znaleźć mapowania 1-do-1 między wartościami tych atrybutów. Jeśli istnieje mapowanie 1-do-1, MSBuild porównuje znacznik czasu każdego elementu wejściowego ze znacznikiem czasu odpowiadającego mu elementu wyjściowego. Pliki wyjściowe pozbawione mapowań 1-do-1 są porównywane ze wszystkimi plikami wejściowymi. Element uważa się za aktualny, jeśli plik wyjściowy jest nie starszy niż plik lub pliki wejściowe.  
  
 Jeśli wszystkie elementy wyjściowe są aktualne, program MSBuild pomija element docelowy. To *wzrostowe* docelowego może znacznie zwiększyć szybkość kompilacji. Jeśli tylko niektóre pliki są aktualne, program MSBuild wykonuje element docelowy, ale pomija elementy aktualne. W efekcie wszystkie elementy stają się aktualne. Jest to nazywane *częściowe wzrostowe*.  
  
 Mapowania 1-do-1 są z reguły tworzone wskutek przekształceń elementów. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).  
  
 Rozważmy następujący element docelowy.  
  
```xml  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Zbiór plików reprezentowanych przez typ elementu `Compile` jest kopiowany do katalogu kopii zapasowych. Pliki kopii zapasowej mają rozszerzenie .bak. Jeśli pliki reprezentowane przez typ elementu `Compile` lub odpowiadające im pliki kopii zapasowej nie zostaną usunięte lub zmodyfikowane po uruchomieniu elementu docelowego będącego kopią zapasową, wtedy ten element jest pomijany w kolejnych kompilacjach.  
  
## <a name="output-inference"></a>Wnioskowanie danych wyjściowych  
 Program MSBuild porównuje atrybuty `Inputs` i `Outputs` elementu docelowego w celu ustalenia, czy element docelowy ma zostać wykonany. Najlepiej, aby zestaw plików istniejących po ukończeniu kompilacji przyrostowej pozostawał bez zmian niezależnie od tego, czy skojarzone z nimi elementy docelowe zostały wykonane. Ponieważ właściwości i elementy tworzone lub zmieniane przez zadania mogą wpływać na kompilację, program MSBuild musi wywnioskować ich wartość, nawet gdy dotyczący ich element docelowy jest pomijany. Jest to nazywane *output wnioskowania*.  
  
 Istnieją trzy przypadki:  
  
-   Element docelowy ma atrybut `Condition`, którego wynikiem jest wartość `false`. W tym przypadku element docelowy nie jest wykonywany i nie ma wpływu na kompilację.  
  
-   Element docelowy ma nieaktualne dane wyjściowe i jest wykonywany w celu ich aktualizacji.  
  
-   Element docelowy nie ma żadnych nieaktualnych danych wyjściowych, dlatego jest pomijany. Program MSBuild oblicza element docelowy, po czym wprowadza zmiany w elementach i właściwościach tak, jakby element został wykonany.  
  
 Aby umożliwić kompilację przyrostową, zadania muszą dopilnować, aby wartość atrybutu `TaskParameter` każdego elementu `Output` była równa parametrowi wejściowemu zadania. Oto kilka przykładów:  
  
```xml  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Powstaje właściwość Easy, która ma wartość „123” niezależnie od tego, czy element docelowy jest wykonywany czy pomijany.  
  
```xml  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Powstaje typ elementu Simple, który ma dwa elementy — „a.cs” i „b.cs”, niezależnie od tego, czy element docelowy jest wykonywany czy pomijany.  
  
 Począwszy od programu MSBuild 3.5 wnioskowanie danych wyjściowych jest wykonywane automatycznie wobec grup elementów i właściwości w elemencie docelowym. Zadania `CreateItem` nie są wymagane w elemencie docelowym i należy ich unikać. Ponadto zadań `CreateProperty` należy używać w elemencie docelowym tylko w celu określenia, czy został on wykonany.  
  
## <a name="determining-whether-a-target-has-been-run"></a>Ustalanie, czy element docelowy został kiedykolwiek wykonany  
 Z powodu wnioskowania danych wyjściowych należy do elementu docelowego dodać zadanie `CreateProperty`, które będzie badało właściwości i elementy w celu określenia, czy element docelowy został wykonany. Należy do elementu docelowego dodać zadanie `CreateProperty`, a do niego element `Output`, którego parametr `TaskParameter` ma wartość „ValueSetByTask”.  
  
```xml  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Spowoduje to utworzenie właściwości CompileRan i nadanie jej wartości `true`, ale tylko pod warunkiem, że obiekt docelowy jest wykonywany. Jeśli element docelowy jest pomijany, właściwość CompileRan nie powstaje.  
  
## <a name="see-also"></a>Zobacz też  
 [Docelowe elementy](../msbuild/msbuild-targets.md)