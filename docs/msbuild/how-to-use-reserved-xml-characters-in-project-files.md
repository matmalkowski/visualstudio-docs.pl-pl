---
title: 'Porady: użycie znaków zarezerwowanych XML w plikach projektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647dba94840383410d06f6e5bf96ec3b0146c394
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077662"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Porady: użycie znaków zarezerwowanych XML w plikach projektu
Podczas tworzenia plików projektu, może być konieczne użycie zarezerwowanych znaków XML w przypadku, na przykład w wartości właściwości lub wartości parametrów zadania. Jednak niektóre zastrzeżone znaki muszą zostać zastąpione nazwanych jednostek, dzięki czemu można przeanalizować pliku projektu.  
  
## <a name="use-reserved-characters"></a>Zastrzeżone znaki  
 W poniższej tabeli opisano zarezerwowanych znaków XML, które muszą zostać zastąpione odpowiednia jednostka o nazwie, dzięki czemu można przeanalizować pliku projektu.  
  
|Zastrzeżonego znaku|Nazwanych jednostek|  
|------------------------|------------------|  
|\<|&amp;lt;|  
|>|&amp;gt;|  
|&|&amp;amp;|  
|"|&amp;quot;|  
|'|&amp;APOS;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Aby używać cudzysłowów w pliku projektu  
  
-   Zamień podwójnych cudzysłowów odpowiadającą nazwie podmiotu, &amp;quot;. Na przykład, aby umieścić podwójnego cudzysłowu wokół `EXEFile` listy elementów, wpisz:  
  
    ```xml  
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu podwójne cudzysłowy są używane do zaznacz nazwę pliku na komunikat, który jest wysyłany przy użyciu pliku projektu.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)    
 [MSBuild](../msbuild/msbuild.md)    
