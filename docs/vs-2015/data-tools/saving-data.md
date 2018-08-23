---
title: Zapisywanie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14ff0e62608c3e2ab0c72366d9544f1d1309737a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688729"
---
# <a name="saving-data"></a>Zapisywanie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisywanie danych jest proces utrwalanie zmienić dane w modelu danych aplikacji z powrotem do oryginalnego magazynu danych, zazwyczaj relacyjnej bazy danych takich jak SQL Server.  
  
 Aktualizowanie źródła danych za pomocą modelu danych zwykle jest procesem dwuetapowym. Pierwszym krokiem jest aktualizowanie modelu danych o nowe informacje — nowe rekordy rekordów, lub usunięcie rekordów. Drugi etap jest, aby zapisać zmiany w modelu danych w bazie danych.  
  
 W poniższych tematach opisano pojęcia i zadania związane z zapisywaniem danych.  
  
## <a name="related-topics"></a>Tematy pokrewne  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)  
 Zawiera omówienie sposobu zmiany zostały wprowadzone w zestawie danych i jak zestawu danych śledzi informacje o zmianach, aby zapisać te zmiany do bazy danych.  
  
 [Zapisywanie danych dotyczących jednostki](../data-tools/saving-entity-data.md)  
 Opisuje sposób zapisać zmiany w [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) i [4.5 usług danych WCF](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) aplikacji.