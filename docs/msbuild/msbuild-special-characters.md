---
title: Znaki specjalne w programie MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9859cf55b3b9fd4745c5e799a9a54e7c1d2cb9cd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]rezerwuje niektórych znaków specjalnych w określonych okolicznościach. Masz ucieczki takich znaków, jeśli chcesz użyć ich dosłownie w kontekście, w którym są zastrzeżone. Na przykład gwiazdkę ma specjalne znaczenie tylko w `Include` i `Exclude` atrybutów definicji elementu i w wywołaniach `CreateItem`. Chcąc gwiazdkę są wyświetlane jako gwiazdki w jednym z tych kontekstach, musi on escape. W każdym kontekście po prostu wpisz gwiazdkę, którym ma być wyświetlany.  
  
 Aby znak specjalny, należy użyć składni %*xx*, gdzie *xx* reprezentuje wartość szesnastkową ASCII znaku. Aby uzyskać więcej informacji, zobacz [porady: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Znaki specjalne  
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] znaki specjalne:  
  
|**Znak**|**ASCII**|**Użycie zarezerwowanych**|  
|-------------------|---------------|------------------------|  
|%|%25|Odwołanie do metadanych|  
|$|%24|Właściwości odwołania|  
|@|%40|Odwołaniem do elementu listy|  
|'|%27|Warunki i inne wyrażenia|  
|;|% 3B|Separator listy|  
|?|% 3F|Znaki wieloznaczne w nazwach plików w `Include` i `Exclude` atrybutów|  
|*|% 2A|Znaki wieloznaczne do użycia w nazwach plików w `Include` i `Exclude` atrybutów|  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)   
 [Elementy](../msbuild/msbuild-items.md)