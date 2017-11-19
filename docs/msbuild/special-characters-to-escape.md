---
title: "Znaki specjalne wyjścia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 6c236a86677dab4015f8a0dc234ed211def7b1f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)