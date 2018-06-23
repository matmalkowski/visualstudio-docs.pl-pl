---
title: Przekształcenia w programie MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 49044f620b928a60417e48cf368ec0d8ae1dcc85
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325299"
---
# <a name="msbuild-transforms"></a>Przekształcenia w programie MSBuild
Transformacja jest jeden do jednego konwersji jeden element listy do innej. Oprócz włączenia projektu można przekonwertować elementu listy, transformacji umożliwia cel, aby zidentyfikować bezpośredniego mapowania między jej danych wejściowych i wyjściowych. W tym temacie opisano transformacji i w jaki sposób [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa ich do kompilacji projektów bardziej efektywnie.  
  
## <a name="transform-modifiers"></a>Przekształć modyfikatorów  
Transformacje nie są dowolne, ale są ograniczone przez specjalnej składni, w którym wszystkie Modyfikatory przekształcenia musi być w formacie %(*ItemMetaDataName*). Wszystkie metadane elementu może służyć jako modyfikator transformacji. W tym metadane dobrze znanego elementu, który jest przypisany do każdego elementu, jeśli została ona utworzona. Aby uzyskać listę metadane dobrze znanego elementu, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
W poniższym przykładzie lista *.resx* plików jest przekształcana na listę *.resources* plików. Modyfikator transformacji %(filename) określa, że każdy *.resources* plik ma taką samą nazwę jak odpowiadający mu *.resx* pliku.  
  
```xml  
@(RESXFile->'%(filename).resources')  
```

Na przykład, jeśli elementy na liście element @(RESXFile) są *Form1.resx*, *Form2.resx*, i *Form3.resx*, na liście przekształcone dane wyjściowe będą  *Form1.resources*, *Form2.resources*, i *Form3.resources*.  

> [!NOTE]
>  Możesz określić niestandardowe separatora listy po przekształceniu elementu w taki sam sposób określ separatora listy standardowych elementów. Na przykład można rozdzielić listy po przekształceniu elementu za pomocą przecinka (,) zamiast domyślnego średnika (;), należy użyć następującego kodu XML:  
> `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`
  
## <a name="using-multiple-modifiers"></a>Przy użyciu wielu modyfikatorów  
 Wyrażenie do przekształcenia może zawierać wiele modyfikatorów, które mogą być łączone w dowolnej kolejności i można powtarzać. W poniższym przykładzie nazwę katalogu, który zawiera pliki jest zmieniany, ale pliki zachować oryginalne rozszerzenie nazwy, a nazwa pliku.  
  
```xml  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Na przykład, jeśli elementy, które są zawarte w `RESXFile` listy elementów są *Project1\Form1.resx*, *Project1\Form2.resx*, i *Project1\Form3.text*, dane wyjściowe na liście przekształcone będzie *Toolset\Form1.resx*, *Toolset\Form2.resx*, i *Toolset\Form3.text*.  
  
## <a name="dependency-analysis"></a>Analizy zależności  
 Transformacje zagwarantować mapowanie jeden do jednego między listy elementów po przekształceniu i oryginalnej listy elementów. W związku z tym, jeśli element docelowy tworzy dane wyjściowe, które są przekształceniami danych wejściowych, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analizowanie sygnatury czasowe z wejściami i wyjściami i zdecyduj, czy pominąć, kompilacji lub częściowo odbudować obiektu docelowego.  
  
 W [zadanie kopiowania](../msbuild/copy-task.md) w poniższym przykładzie każdy plik w `BuiltAssemblies` listy elementów mapy do pliku w folderze docelowym zadania przy użyciu przekształcenie w `Outputs` atrybutu. Jeśli plik w `BuiltAssemblies` elementu zmiany listy `Copy` zadanie jest uruchamiane tylko w przypadku zmienionego pliku i wszystkie inne pliki są pomijane. Aby uzyskać więcej informacji na temat analizy zależności i sposobu korzystania z transformacji, zobacz [porady: tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md).  
  
```xml  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu, który używa transformacji. W tym przykładzie przyjęto założenie, że istnieje tylko jeden plik XSD w katalogu c:\sub0\sub1\sub2\sub3 i że katalog roboczy jest c:\sub0.  
  
### <a name="code"></a>Kod  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Instrukcje: Kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md)