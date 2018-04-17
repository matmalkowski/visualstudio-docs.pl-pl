---
title: Znaki specjalne w programie MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f7df43e773e965fe242cd9d9e73d4b681b96c15
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezerwuje niektórych znaków specjalnych w określonych okolicznościach. Masz ucieczki takich znaków, jeśli chcesz użyć ich dosłownie w kontekście, w którym są zastrzeżone. Na przykład gwiazdkę ma specjalne znaczenie tylko w `Include` i `Exclude` atrybutów definicji elementu i w wywołaniach `CreateItem`. Chcąc gwiazdkę są wyświetlane jako gwiazdki w jednym z tych kontekstach, musi on escape. W każdym kontekście po prostu wpisz gwiazdkę, którym ma być wyświetlany.  
  
 Aby znak specjalny, należy użyć składni %*xx*, gdzie *xx* reprezentuje wartość szesnastkową ASCII znaku. Aby uzyskać więcej informacji, zobacz [porady: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Znaki specjalne  
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] znaki specjalne:  
  
|**Znak**|**ASCII**|**Użycie zarezerwowanych**|  
|-------------------|---------------|------------------------|  
|%|%25|Odwołanie do metadanych|  
|$|%24|Właściwości odwołania|  
|@|%40|Odwołaniem do elementu listy|  
|'|%27|Warunki i inne wyrażenia|  
|;|%3B|Separator listy|  
|?|%3F|Znaki wieloznaczne w nazwach plików w `Include` i `Exclude` atrybutów|  
|*|%2A|Znaki wieloznaczne do użycia w nazwach plików w `Include` i `Exclude` atrybutów|  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)   
 [Elementy](../msbuild/msbuild-items.md)