---
title: 'Porady: wyświetlanie listy elementów rozdzielanych przecinkami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b438f96d9b19ba7f434a83016bdf652740770c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Porady: wyświetlanie listy elementów rozdzielanych przecinkami
Podczas pracy z elementem list w [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), czasami jest to przydatne wyświetlić zawartość tych list elementów w taki sposób, który jest łatwy do odczytania. Lub może być zadanie, które przyjmuje listę elementów oddzielonych ciąg separatora specjalnych. W obu przypadkach można określić ciąg separatora listy elementów.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Oddzielanie elementów na liście przecinkami  
 Domyślnie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa średnikami do oddzielania elementów na liście. Rozważmy na przykład `Message` elementu przy użyciu następującej wartości:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Gdy `@(TXTFile)` listy elementów zawiera elementy App1.txt, App2.txt i App3.txt, komunikat:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Jeśli chcesz zmienić to zachowanie domyślne, możesz określić własne separatora. Składnia określająca element separatora listy jest następująca:  
  
 `@(ItemListName, '<separator>')`  
  
 Separator może być pojedynczym znakiem lub ciągiem i musi być ujęta w apostrofy.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Aby wstawić przecinkiem i spacją między elementami  
  
-   Notacja elementu podobny do następującego:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [Exec](../msbuild/exec-task.md) zadanie jest uruchamiane narzędzie findstr można znaleźć w pliku Phrases.txt ciągów określony tekst. Polecenie findstr literałów ciągów znaków oznaczono **/ / c:** przełącznika, to separatora elementu `/c:` dodaje się między elementami w `@(Phrase)` listy elementów.  
  
 W tym przykładzie jest to równoważne polecenie:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```xml  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)