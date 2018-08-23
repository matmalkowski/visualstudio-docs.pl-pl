---
title: Znaki specjalne w programie MSBuild | Dokumentacja firmy Microsoft
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
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fcbafb43a059221e5572c9c807cadfdefe68134
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682481"
---
# <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [znaki specjalne MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-special-characters).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rezerwuje niektórych znaków specjalnych w określonych kontekstach. Masz tylko takie znaki ucieczki, aby ich używać dosłownie w kontekście, w którym są one zarezerwowane. Na przykład znak gwiazdki ma specjalne znaczenie tylko w `Include` i `Exclude` atrybuty definicji elementu i w wywołaniach `CreateItem`. Jeśli chcesz, aby znak gwiazdki, aby pojawiało się jako znak gwiazdki w jednym z tych kontekstach, musisz wyjść z niego. W każdym kontekście wystarczy wpisać gwiazdkę, w której ma się pojawić.  
  
 Aby znak specjalny, należy użyć składni %*xx*, gdzie *xx* reprezentuje wartości szesnastkowej znaku ASCII. Aby uzyskać więcej informacji, zobacz [porady: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Znaki specjalne  
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] znaki specjalne:  
  
|**Znak**|**ASCII**|**Użycie zarezerwowanych**|  
|-------------------|---------------|------------------------|  
|%|%25|Odwoływanie się do metadanych|  
|$|%24|Właściwości odwołania|  
|@|%40|Odwołujący się listy elementów|  
|'|%27|Warunki i inne wyrażenia|  
|;|%3B|Separator listy|  
|?|%3F|Znak symbolu wieloznacznego dla nazwy plików w `Include` i `Exclude` atrybutów|  
|*|%2A|Znak symbolu wieloznacznego do użytku w nazwach plików w `Include` i `Exclude` atrybutów|  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)   
 [Elementy](../msbuild/msbuild-items.md)



