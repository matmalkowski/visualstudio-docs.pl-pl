---
title: 'Porady: znaki specjalne ucieczki w MSBuild | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: "12"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6d5fda1972cfc483a02a7f655a33b1fb9efdf43f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Porady: znaki specjalne ucieczki w MSBuild
Niektóre znaki mają specjalne znaczenie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu. Przykłady znaków średnikami (;) i gwiazdki (*). Aby uzyskać pełną listę tych znaków specjalnych, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Aby można było używać tych znaków specjalnych jako literał w pliku projektu, muszą być one określone za pomocą składni %*xx*, gdzie *xx* reprezentuje wartość szesnastkową ASCII znaku.  
  
## <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild  
 Co znajduje się przykład gdy są używane znaki specjalne w `Include` atrybutu list elementów. Na przykład na poniższej liście element deklaruje dwóch elementów: `MyFile.cs` i `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Jeśli chcesz zadeklarować elementu, który zawiera średnikiem w nazwie, należy użyć %*xx* składni escape średnik i zapobiec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] z deklarowanie dwa osobne elementy. Na przykład następujący element specjalne średnik i jedną o nazwie deklaruje `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Aby użyć MSBuild znak specjalny w postaci literału znaku  
  
-   Użyj % notacji*xx* zamiast znaków specjalnych, gdzie *xx* reprezentuje wartość szesnastkową znaków ASCII. Na przykład, aby użyć gwiazdki (*) jako literał znaków, użyj wartości `%2A`.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md) [elementów](../msbuild/msbuild-items.md)