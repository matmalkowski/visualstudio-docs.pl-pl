---
title: "Efektywne używanie pamięci podczas kompilowania dużych projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1e78afd0f76839d170f12cf4315610c183899fff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Efektywne używanie pamięci podczas kompilowania dużych projektów
Dużych projektów często zawierają wiele podprojekty i inne zależności, a te mogą wykorzystywać duże ilości pamięci w czasie kompilacji. Gdy zostaje zmniejszona dostępnej pamięci systemu, może również zmniejszyć wydajność systemu. Starsze wersje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów pozostała w pamięci lub w wersji 3.5 projekty zostały usunięte, ale zachowane wyniki kompilacji w pamięci podręcznej pobierania nowsze.  
  
 W wersji 4.0 obsługuje ten zarządzania pamięcią automatycznie, zapisywanie projektów z konieczności użycia właściwości, takie jak `UnloadProjectsOnCompletion` i `UseResultsCache`.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)