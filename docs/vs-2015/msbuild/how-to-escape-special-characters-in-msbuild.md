---
title: 'Porady: znaki specjalne ucieczki w MSBuild | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a900ebe49e95b512c0f53a5542f0ba8ee238a83f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689062"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Porady: znaki specjalne ucieczki w MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: znaki specjalne ucieczki w MSBuild](https://docs.microsoft.com/visualstudio/msbuild/how-to-escape-special-characters-in-msbuild).  
  
  
Niektóre znaki mają specjalne znaczenie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliki projektu. Przykłady znaków średnikami (;) i gwiazdki (*). Aby uzyskać pełną listę tych znaków specjalnych, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Aby można było używać tych znaków specjalnych jako literały w pliku projektu, muszą one być określone za pomocą składni %*xx*, gdzie *xx* reprezentuje wartości szesnastkowej znaku ASCII.  
  
## <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild  
 Co znajduje się przykład użycia znaków specjalnych w `Include` atrybutu elementu listy. Na przykład na poniższej liście elementu deklaruje dwa elementy: `MyFile.cs` i `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Jeśli chcesz zadeklarować elementu, który zawiera średnikami w nazwie, należy użyć %*xx* składni ucieczki średnika i zapobiec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] od zadeklarowania dwa oddzielne elementy. Na przykład, następujący element specjalne średnika i deklaruje jeden element o nazwie `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Aby użyć znaku specjalnego MSBuild jako znak literału  
  
-   Użyj % notacji*xx* zamiast znaki specjalne, gdzie *xx* reprezentuje wartości szesnastkowej znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znak literałowy, użyj wartości `%2A`.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Program MSBuild](msbuild.md) [elementów](../msbuild/msbuild-items.md)


