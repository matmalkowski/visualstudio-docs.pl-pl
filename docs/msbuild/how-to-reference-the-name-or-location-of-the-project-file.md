---
title: "Porady: odwołanie do nazwy lub lokalizacji pliku projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 9186b98b482b101254e70def9285d9bbad2ca254
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Porady: odwołanie do nazwy lub lokalizacji pliku projektu
W pliku projektu bez konieczności tworzenia własnych właściwości można użyć nazwy lub lokalizacji projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]Udostępnia właściwości zastrzeżone odwołujące się do nazwy pliku projektu i inne właściwości związanych z projektem. Aby uzyskać więcej informacji na właściwości zastrzeżone, zobacz [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Przy użyciu MSBuildProjectName właściwość  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]zawiera niektóre zastrzeżone właściwości, które można użyć w plikach projektu bez definiując je za każdym razem. Na przykład właściwość zastrzeżone `MSBuildProjectName` zawiera odwołanie do nazwy pliku projektu.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Aby użyć MSBuildProjectName właściwość  
  
-   Odwoływać się do właściwości w pliku projektu z notacji $ (), tak samo jak dowolnej właściwości. Na przykład:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Zaletą korzystania zarezerwowanej właściwości jest to, że zmiany nazwy pliku projektu są automatycznie włączone. Przy następnym uruchomieniu, skompiluj projekt, plik wyjściowy będzie zawierał nową nazwę żadne dalsze działania wymagane ze strony użytkownika.  
  
> [!NOTE]
>  Właściwości zastrzeżone nie można ponownie zdefiniować w pliku projektu.  
  
## <a name="example"></a>Przykład  
 Następujący przykładowy plik projektu odwołuje się do nazwy projektu jako właściwość zarezerwowane do określenia nazwy dla danych wyjściowych.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
[MSBuild](../msbuild/msbuild.md)  
 [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md)