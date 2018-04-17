---
title: Definicje elementów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d75af412e3b5f9d1329ea0304cd33725ec7c9b3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="item-definitions"></a>Definicje elementów
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 umożliwia deklaracji statycznych elementów w plikach projektu przy użyciu [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Jednak metadanych można wprowadzić tylko na poziomie elementu, nawet jeśli metadane są identyczne dla wszystkich elementów. Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, element projektu o nazwie [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) pozwala pokonać tego ograniczenia. *ItemDefinitionGroup* pozwala zdefiniować zestaw definicje elementów, które dodają domyślnych wartościach metadanych dla wszystkich elementów w typie nazwanego elementu.  
  
 *ItemDefinitionGroup* element jest wyświetlany natychmiast po [projektu](../msbuild/project-element-msbuild.md) element pliku projektu. Definicje elementów są dostępne następujące funkcje:  
  
-   Można zdefiniować domyślny globalny metadanych dla elementów poza obiektu docelowego. Oznacza to tych samych metadanych ma zastosowanie do wszystkich elementów określonego typu.  
  
-   Typy elementów może mieć wielu definicji. Woluminowi specyfikacje dodatkowe metadane na typ ostatniego specyfikacji pierwszeństwo. \(Metadane następuje kolejności importu następujące właściwości.\)  
  
-   Metadane mogą być dodatku. Na przykład wartości CDefines są zgromadzonych warunkowo, w zależności od właściwości, które zostały ustawione. Na przykład `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Metadane mogą zostać usunięte.  
  
-   Warunki może służyć do kontrolowania włączenia metadanych.  
  
## <a name="item-metadata-default-values"></a>Element metadanych domyślne wartości  
 Metadane elementu, który jest zdefiniowany w ItemDefinitionGroup jest tylko deklarację domyślnej metadanych. Metadane nie ma zastosowania, chyba że zdefiniujesz elementu, który używa ItemGroup zawierają wartości metadanych.  
  
> [!NOTE]
>  W tych przykładach w niniejszym temacie jest wyświetlany ItemDefinitionGroup element, ale jego odpowiedniej definicji ItemGroup zostanie pominięty dla uzyskania przejrzystości.  
  
 Metadane jawnie zdefiniowany w ItemGroup mają pierwszeństwo przed metadanych w ItemDefinitionGroup. Metadane w ItemDefinitionGroup jest stosowane tylko dla niezdefiniowanego metadanych w ItemGroup. Na przykład:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 W tym przykładzie metadanych domyślne "m" jest stosowany do elementu "i", ponieważ metadanych "m" nie jest jawnie zdefiniowany przez element "i". Jednak domyślne metadanych "n" nie ma zastosowania do elementu "i", ponieważ metadane "n" jest już zdefiniowana przez element "i".  
  
> [!NOTE]
>  Nazwy elementu XML i parametru jest uwzględniana wielkość\-poufnych. Element metadanych i elementu\/nazwy właściwości nie są wielkość\-poufnych. W związku z tym ItemDefinitionGroup elementów, które mają nazwy, które różnią się tylko wielkością liter powinien być traktowany jako element tego samego ItemGroup.  
  
## <a name="value-sources"></a>Wartość źródła  
 Wartości metadanych, który jest zdefiniowany w ItemDefinitionGroup mogą pochodzić z różnych źródeł, w następujący sposób:  
  
-   Właściwość PropertyGroup  
  
-   Element ItemDefinitionGroup  
  
-   Przekształcenie elementu w elemencie ItemDefinitionGroup  
  
-   Zmienna środowiskowa  
  
-   Global — właściwość \(z wiersza polecenia MSBuild.exe\)  
  
-   Właściwości zastrzeżone  
  
-   Dobrze\-znanych metadanych elementu z ItemDefinitionGroup  
  
-   Sekcja CDATA \< \! \[CDATA\[tutaj niczego nie przeanalizować\]\]\>  
  
> [!NOTE]
>  Metadane elementu z ItemGroup nie jest przydatne w deklaracji ItemDefinitionGroup metadanych, ponieważ elementy ItemDefinitionGroup są przetwarzane przed ItemGroup elementów.  
  
## <a name="additive-and-multiple-definitions"></a>Dodatek a wiele definicji  
 Podczas dodawania definicje lub użyj wielu ItemDefinitionGroups, należy pamiętać o następujących czynności:  
  
-   Specyfikacja dodatkowych metadanych jest dodawana do typu.  
  
-   Specyfikację ostatniego pierwszeństwo.  
  
 Jeśli masz wiele ItemDefinitionGroups każda kolejne specyfikacji dodaje metadanych do poprzedniego definicji. Na przykład:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 W tym przykładzie metadanych "o" jest dodawany do "m" i "n".  
  
 Ponadto można również dodać metadanych uprzednio zdefiniowanej wartości. Na przykład:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 W tym przykładzie uprzednio zdefiniowanej wartości metadanych "m" \(m1\) jest dodawana do nowej wartości \(m2\), dzięki czemu jest końcowa wartość "m1; m2".  
  
> [!NOTE]
>  Może to także wystąpić w tej samej ItemDefinitionGroup.  
  
 Aby zastąpić wcześniej określonych metadanych, ostatni specyfikacji pierwszeństwo. W poniższym przykładzie końcowa wartość metadanych "m" przechodzi od "m1" do "m1a".  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## <a name="using-conditions-in-an-itemdefinitiongroup"></a>Za pomocą warunków w ItemDefinitionGroup  
 Warunki w ItemDefinitionGroup służy do kontrolowania włączenia metadanych. Na przykład:  
  
```xml  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 W takim przypadku metadanych domyślne "m1" w elemencie "i" jest uwzględniona tylko wtedy, gdy wartość właściwości "Konfiguracja" to "Debug".  
  
> [!NOTE]
>  Tylko odwołania do metadanych lokalnych są obsługiwane w warunkach.  
  
 Odwołania do metadanych określonych w starszych ItemDefinitionGroup znajdują się lokalnie do elementu, a nie grupa definicji. Oznacza to, że zakres odwołania są elementu\-określone. Na przykład:  
  
```xml  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i> 
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
  
```  
  
W powyższym przykładzie elementu "i" odwołuje się do elementu "test" w jego stan. Ten warunek nigdy nie będą wartość true, ponieważ program MSBuild interpretuje odwołanie do innego elementu metadanych w ItemDefinitionGroup jako pusty ciąg. W związku z tym "m" można ustawić na "m0."
 
```xml 
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

W powyższym przykładzie "m" może być ustawiona na wartość "m1" jako warunek odwołuje się do elementu "i" w wartości metadanych dla elementu "tak". 
  
## <a name="overriding-and-deleting-metadata"></a>Zastępowanie i usuwanie metadanych  
 Metadanych określonych w ItemDefinitionGroup — element może zostać przesłonięta w późniejszym element ItemDefinitionGroup przez ustawienie wartości metadanych puste. Można również skutecznie usunąć element metadanych przez ustawienie dla niego wartość pustą. Na przykład:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Element "i" nadal zawiera metadanych "m", ale jej wartość jest obecnie pusta.  
  
## <a name="scope-of-metadata"></a>Zakres metadanych  
 ItemDefinitionGroups ma zasięg globalny zdefiniowane i globalnych właściwości wszędzie tam, gdzie są zdefiniowane. Definicje metadanych domyślne w ItemDefinitionGroup można samodzielnie\-referencyjnym. Na przykład następujące używa odwołania proste metadanych:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Można także odwołania kwalifikowaną metadanych:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Jednak następujący ciąg nie jest prawidłowy:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, ItemGroups mogą być również samodzielnie\-referencyjnym. Na przykład:  
  
```xml  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
