---
title: Docelowa kolejność kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5c54fd6406350f5d0ad9620f10eef4fb9a546b4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="target-build-order"></a>Kolejność kompilowania obiektów docelowych
Obiekty docelowe muszą być uporządkowane, jeśli dane wejściowe jeden obiekt docelowy jest zależna od dane wyjściowe inny element docelowy. Aby określić kolejność uruchamiania obiektów docelowych, można użyć tych atrybutów:  
  
-   `InitialTargets`. To `Project` atrybut określa elementy docelowe, które będą uruchamiane, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybutu.  
  
-   `DefaultTargets`. To `Project` atrybut określa, które cele są uruchamiane, jeśli element docelowy nie jest jawnie określona w wierszu polecenia.  
  
-   `DependsOnTargets`. To `Target` atrybut określa elementy docelowe, które należy uruchomić, zanim będzie można uruchomić ten element docelowy.  
  
-   `BeforeTargets` i `AfterTargets`. Te `Target` atrybuty określają, że ten element docelowy powinien być wykonywany przed lub po określone elementy docelowe (MSBuild 4.0).  
  
 Element docelowy nigdy nie jest uruchamiane dwa razy podczas kompilacji, nawet jeśli zależy od niego kolejnych docelowego w kompilacji. Po uruchomieniu elementu docelowego jej udziału kompilacja zostanie zakończona.  
  
 Obiekty docelowe może mieć `Condition` atrybutu. Jeśli jest określony warunek `false`, element docelowy nie jest wykonywane i nie ma wpływu na kompilacji. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
## <a name="initial-targets"></a>Cele początkowe  
 `InitialTargets` Atrybutu [projektu](../msbuild/project-element-msbuild.md) element określa elementy docelowe, które będą uruchamiane, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w `DefaultTargets` atrybutu. Początkowe cele są zwykle używane do sprawdzania błędów.  
  
 Wartość `InitialTargets` atrybut może być rozdzielone średnikami, uporządkowanych lista elementów docelowych. Poniższy przykład określa, że `Warm` docelowy działa, a następnie `Eject` docelowy działa.  
  
```xml  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Projekty zaimportowany może mieć własne `InitialTargets` atrybutów. Wszystkie elementy docelowe początkowej są zagregowane razem i są uruchamiane w kolejności.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Określ którego docelowego do kompilacji pierwszej](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="default-targets"></a>Domyślne elementy docelowe  
 `DefaultTargets` Atrybutu [projektu](../msbuild/project-element-msbuild.md) element określa, które docelowej lub miejsc docelowych są wbudowane, jeśli element docelowy nie jest jawnie określona w wierszu polecenia.  
  
 Wartość `DefaultTargets` atrybut może być rozdzielone średnikami, uporządkowaną listę domyślne elementy docelowe. Poniższy przykład określa, że `Clean` docelowy działa, a następnie `Build` docelowy działa.  
  
```xml  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Można zastąpić domyślne elementy docelowe przy użyciu **/target** przełącznik w wierszu polecenia. Poniższy przykład określa, że `Build` docelowy działa, a następnie `Report` docelowy działa. Po określeniu obiektów docelowych w ten sposób wszystkie domyślne elementy docelowe są ignorowane.  
  
 `msbuild /target:Build;Report`  
  
 Jeśli został określony zarówno początkowej elementów docelowych i domyślne elementy docelowe, a jeśli nie określono elementów docelowych wiersza polecenia, program MSBuild uruchamia celów początkowych najpierw, a następnie wykonuje domyślne elementy docelowe.  
  
 Projekty zaimportowany może mieć własne `DefaultTargets` atrybutów. Pierwszy `DefaultTargets` napotkano atrybut określa, które domyślne elementy docelowe zostaną uruchomione.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Określ którego docelowego do kompilacji pierwszej](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="first-target"></a>Pierwszy element docelowy  
 Jeśli nie ma żadnych początkowe cele, domyślne elementy docelowe lub wiersza polecenia obiekty docelowe, MSBuild uruchamiane pierwszy element docelowy napotkania w pliku projektu lub żadnego projektu importowanych plików.  
  
## <a name="target-dependencies"></a>Miejsce docelowe zależności  
 Obiekty docelowe, można opisać relacji zależności ze sobą. `DependsOnTargets` Atrybut wskazuje, że element docelowy jest zależny od innych celów. Na przykład  
  
```xml  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 MSBuild informuje, że `Serve` zależy od docelowego `Chop` docelowych i `Cook` docelowych. Uruchamia program MSBuild `Chop` docelowego, a następnie uruchamia `Cook` docelowy przed uruchomieniem `Serve` docelowej.  
  
## <a name="beforetargets-and-after-targets"></a>BeforeTargets i po elementów docelowych  
 W wersji 4.0 MSBuild, można określić kolejność docelowych przy użyciu `BeforeTargets` i `AfterTargets` atrybutów.  
  
 Rozważmy poniższy skrypt.  
  
```xml  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Aby utworzyć cel pośredniego `Optimize` , na którym działają `Compile` target, ale przed wysłaniem `Link` docelowych, Dodaj następujący element docelowy dowolne miejsce w `Project` elementu.  
  
```xml  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## <a name="determining-the-target-build-order"></a>Określenie kolejności kompilacji docelowej  
 MSBuild określa kolejność kompilowania obiektów docelowych w następujący sposób:  
  
1.  `InitialTargets` obiekty docelowe są uruchamiane.  
  
2.  Obiekty docelowe w wierszu polecenia przez **/target** przełącznika są uruchamiane. Jeśli określono elementów docelowych w wierszu polecenia, a następnie `DefaultTargets` uruchamiane są elementy docelowe. Jeśli nie będzie obecne, pierwszy element docelowy napotkano jest uruchamiany.  
  
3.  `Condition` Atrybut docelowy jest obliczane. Jeśli `Condition` atrybut jest obecny i daje w wyniku `false`, element docelowy nie jest wykonywane i nie ma dalszych wpływu na kompilacji.

    Obiekty docelowe, które listy warunkowego obiekt docelowy `BeforeTargets` lub `AfterTargets` nadal wykonywać w określonej kolejności.
  
4.  Przed wykonaniem docelowy jego `DependsOnTargets` uruchamiane są elementy docelowe.  
  
5.  Przed wykonaniem docelowy żadnych docelowych który jest wyświetlany w `BeforeTargets` atrybutu jest uruchamiany.  
  
6.  Przed wykonaniem docelowy jego `Inputs` atrybutu i `Outputs` atrybutu są porównywane. Jeśli program MSBuild określi, że wszystkie pliki wyjściowe są nieaktualne względem odpowiedni plik wejściowy lub plików, a następnie MSBuild wykonuje element docelowy. W przeciwnym razie programu MSBuild pomija obiektu docelowego.  
  
7.  Po obiektu docelowego jest wykonywane lub pominięta, wszelkie docelowego, który jest wyświetlany w `AfterTargets` atrybutu jest uruchamiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Docelowe elementy](../msbuild/msbuild-targets.md)