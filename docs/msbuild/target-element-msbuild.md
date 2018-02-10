---
title: "TARGET — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fe87cf8af6c5c2cbb63153f0d82988bd44800519
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="target-element-msbuild"></a>Target — Element (MSBuild)
Zawiera zestaw zadań związanych z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonania po kolei.  

 \<Project>  
 \<Docelowy >  

## <a name="syntax"></a>Składnia  

```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <OnError... />  
</Target>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany.<br /><br /> Nazwa elementu docelowego.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Jeśli wyrażenie `false`, element docelowy nie zostanie wykonany treści docelowej lub obiektów docelowych, które są ustawiane w `DependsOnTargets` atrybutu. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wejściowe do tego obiektu docelowego. Wiele plików są oddzielone średnikami. Sygnatury czasowe plików będą porównywane ze znacznikami czasu plików w `Outputs` ustalenie, czy `Target` jest aktualny. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md), [porady: tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md), i [przekształca](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Atrybut opcjonalny.<br /><br /> Pliki, które formujących produkty wyjściowe do tego obiektu docelowego. Wiele plików są oddzielone średnikami. Sygnatury czasowe plików będą porównywane ze znacznikami czasu plików w `Inputs` ustalenie, czy `Target` jest aktualny. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md), [porady: tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md), i [przekształca](../msbuild/msbuild-transforms.md).|  
|`Returns`|Atrybut opcjonalny.<br /><br /> Zestaw elementów, które będą dostępne do zadań, które wywołują ten element docelowy, na przykład zadania programu MSBuild. Wiele obiektów docelowych są oddzielone średnikami. Jeśli nie mają elementów docelowych w pliku `Returns` atrybutów wyjściowych atrybuty są używane zamiast niej w tym celu.|  
|`KeepDuplicateOutputs`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, wiele odwołań do tego samego elementu w element docelowy zwraca są rejestrowane.  Domyślnie ten atrybut jest `false`.|  
|`BeforeTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych.  W przypadku wskazuje, że ten element docelowy powinien być wykonywany przed określonego obiektu docelowego lub miejsc docelowych. Dzięki temu Autor projektu rozszerzyć bez bezpośrednie modyfikowanie istniejącego zestawu elementów docelowych. Aby uzyskać więcej informacji, zobacz [kolejność kompilacji docelowej](../msbuild/target-build-order.md).|  
|`AfterTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych. W przypadku wskazuje, że ten element docelowy powinny być uruchamiane po określonego obiektu docelowego lub miejsc docelowych. Dzięki temu Autor projektu rozszerzyć bez bezpośrednie modyfikowanie istniejącego zestawu elementów docelowych. Aby uzyskać więcej informacji, zobacz [kolejność kompilacji docelowej](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Atrybut opcjonalny.<br /><br /> Obiekty docelowe, które należy wykonać, można było wykonać ten element docelowy lub analizy zależności najwyższego poziomu mogą wystąpić. Wiele obiektów docelowych są oddzielone średnikami.|  
|`Label`|Atrybut opcjonalny.<br /><br /> Identyfikator, który można identyfikacji lub porządkowania elementów systemu i użytkownika.|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Zadanie](../msbuild/task-element-msbuild.md)|Tworzy i wykonuje wystąpienia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań. Element docelowy może być zero lub więcej zadań.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Zawiera zestaw zdefiniowanych przez użytkownika `Property` elementów. W programie .NET Framework 3.5, `Target` element może zawierać `PropertyGroup` elementów.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Zawiera zestaw zdefiniowanych przez użytkownika `Item` elementów. W programie .NET Framework 3.5, `Target` element może zawierać `ItemGroup` elementów. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).|  
|[OnError —](../msbuild/onerror-element-msbuild.md)|Powoduje, że jeden lub więcej celów do wykonania, jeśli `ContinueOnError` atrybut jest ErrorAndStop (lub `false`) dla zadania nie powiodło się. Może wynosić zero lub więcej `OnError` elementy w element docelowy. Jeśli `OnError` elementy są obecne, muszą one być ostatnich elementów w `Target` elementu.<br /><br /> Aby uzyskać informacje o `ContinueOnError` atrybutów, zobacz [Task — Element (MSBuild)](../msbuild/task-element-msbuild.md).|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  

## <a name="remarks"></a>Uwagi  
 Pierwszy element docelowy do wykonania jest określona w czasie wykonywania. Obiekty docelowe może być zależny od innych celów. Na przykład cel wdrożenia jest zależny od docelowej dla kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Aparat wykonuje zależności w kolejności, w jakiej występują w `DependsOnTargets` atrybutu od lewej do prawej. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).  

 Element docelowy jest wykonywane tylko raz podczas kompilacji, nawet wtedy, gdy więcej niż jeden element docelowy ma zależność od niej.  

 Jeśli element docelowy jest pominięta, ponieważ jego `Condition` atrybutu daje w wyniku `false`, mogą być wykonywane nadal, jeśli jest wywoływana w dalszej części kompilacji i jej `Condition` daje w wyniku atrybutu `true` w tym czasie.  

 Przed MSBuild 4 `Target` zwrócone wszystkie elementy, które zostały określone w `Outputs` atrybutu.  Aby to zrobić, MSBuild musiał Rejestruj, w przypadku żądanego zadania później w kompilacji, ich. Ponieważ nie było w żaden sposób, aby wskazać, które obiekty docelowe ma wyjść, które wymagają wywołań, MSBuild zgromadzonych wszystkie elementy ze wszystkich `Outputs` na wszystkich wywoływane `Target`s. To prowadzić do skalowania problemów dla kompilacji, które ma dużą liczbę elementów danych wyjściowych.  

 Jeśli użytkownik określi `Returns` na dowolnym `Target` element w projekcie, a następnie tylko te `Target`s, który ma `Returns` atrybutu rejestrowanie tych elementów.  

 A `Target` może zawierać zarówno `Outputs` atrybutu i `Returns` atrybutu.  `Outputs`jest używany z `Inputs` do ustalenia, czy element docelowy jest aktualny. `Returns`, jeśli jest obecny, wartość przesłania `Outputs` ustalenie, elementy, które są zwracane do wywoływania.  Jeśli `Returns` nie jest obecny, następnie `Outputs` będą dostępne dla kodu wywołującego, z wyjątkiem w tym przypadku opisanego wcześniej.  

 Przed MSBuild 4, który wtedy `Target` dołączony wiele odwołań do tego samego elementu w jego `Outputs`, zduplikowane pozycje są rejestrowane. W bardzo dużych kompilacji, który ma dużą liczbę wyjść i wiele zależnościami projektu, spowodowałoby dużej ilości pamięci do niewykorzystana, ponieważ zduplikowane elementy nie zostały użycia. Gdy `KeepDuplicateOutputs` atrybut ma ustawioną `true`, te duplikaty są rejestrowane.  

## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład `Target` element, który wykonuje `Csc` zadań.  

```xml  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Zobacz też  
 [Obiekty docelowe](../msbuild/msbuild-targets.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
