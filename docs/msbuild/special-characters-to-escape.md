---
title: "Znaki specjalne wyjścia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b79a497af179f0038f09f2455ed206a0f99aeddc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="special-characters-to-escape"></a>Znaki specjalne wyjścia
Tylko wtedy, gdy mają specjalne znaczenie w tym kontekście, w którym są one używane, należy zastosować ucieczkę znaki specjalne. Na przykład znak gwiazdki (*) jest znak specjalny tylko w definicji elementu "Dołącz" i "Wyklucz" atrybuty lub w wywołaniu <xref:Microsoft.Build.Tasks.CreateItem>. We wszystkich innych przypadkach gwiazdka jest traktowana jako literał gwiazdki. Gdy jest konieczne escape gwiazdki w plikach projektu, spowoduje to nie jest szkodliwy.  
  
 Użyj % notacji*xx* zamiast znaków specjalnych, gdzie *xx* reprezentuje wartość szesnastkową znaków ASCII. Na przykład, aby użyć gwiazdki (*) jako literał znaków, użyj wartości `%2A`.  
  
 Pełną listę znaki specjalne wyjścia następująco:  
  
|Znak|Opis|  
|---------------|-----------------|  
|%|Znak procentu, używana do utworzenia odwołania metadanych.|  
|$|Znak dolara ($), używany do właściwości.|  
|@|Znak używany w celu list elementów.|  
|(|Nawiasu otwierającego używane na listach.|  
|)|Nawiasu zamykającego używane na listach.|  
|`|Apostrof (lub znacznika), używana w warunkach i inne wyrażenia.|  
|;|Średnik, separatora listy.|  
|?|Znak zapytania symbolu wieloznacznego w opisie Specyfikacja pliku, w sekcji dołączania/wykluczania elementów.|  
|*|Gwiazdka specyfikacji symbolu wieloznacznego w opisie pliku w sekcji dołączania/wykluczania elementów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)