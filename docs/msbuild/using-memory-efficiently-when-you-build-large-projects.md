---
title: "Efektywne używanie pamięci podczas kompilowania dużych projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 203868b91778f977affc9c20c8dafa8a5fdf8f60
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Efektywne używanie pamięci podczas kompilowania dużych projektów
Dużych projektów często zawierają wiele podprojekty i inne zależności, a te mogą wykorzystywać duże ilości pamięci w czasie kompilacji. Gdy zostaje zmniejszona dostępnej pamięci systemu, może również zmniejszyć wydajność systemu. Starsze wersje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów pozostała w pamięci lub w wersji 3.5 projekty zostały usunięte, ale zachowane wyniki kompilacji w pamięci podręcznej pobierania nowsze.  
  
 W wersji 4.0 obsługuje ten zarządzania pamięcią automatycznie, zapisywanie projektów z konieczności użycia właściwości, takie jak `UnloadProjectsOnCompletion` i `UseResultsCache`.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)