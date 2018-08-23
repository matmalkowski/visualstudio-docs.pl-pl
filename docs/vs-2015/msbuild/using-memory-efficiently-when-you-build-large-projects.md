---
title: Efektywne używanie pamięci podczas kompilowania dużych projektów | Dokumentacja firmy Microsoft
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
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2cb204fcfb5a96fe9833571895513dfda4449b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678413"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Efektywne używanie pamięci podczas kompilowania dużych projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przy użyciu pamięci efektywnie po użytkownik kompilacji dużych projektów](https://docs.microsoft.com/visualstudio/msbuild/using-memory-efficiently-when-you-build-large-projects).  
  
  
Duże projekty często zawierają wiele projektów podrzędnych oraz inne zależności, a te mogą wykorzystywać duże ilości pamięci systemowej w czasie kompilacji. Gdy jest zmniejszenie ilości dostępnej pamięci systemowej, wydajność systemu również można zmniejszyć. Starsze wersje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektów pozostaje w pamięci lub w wersji 3.5 projekty zostały usunięte, ale zachowane wyniki kompilacji w pamięci podręcznej pobierania nowsze.  
  
 Wersja 4.0 obsługuje to zarządzanie pamięcią automatycznie, zapisywanie projektów z konieczności używania właściwości, takie jak `UnloadProjectsOnCompletion` i `UseResultsCache`.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



