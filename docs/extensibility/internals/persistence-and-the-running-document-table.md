---
title: "Trwałość i uruchamiania dokumentu tabeli | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 062c623ec1de779733e41a8abcad8ca478155dba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchomiona tabeli dokumentu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, projekty są całkowicie odpowiedzialny za zarządzanie trwałości ich elementów projektu, które one osiągnąć za pomocą usługi, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumenty są jednostkę podstawową trwałości w środowisku Visual Studio. Projekty koordynować otwieranie, zapisywanie i zmiana nazwy dokumentów z uruchomionej tabeli dokumentów (Normalizacją) z zasobem, który śledzi stan wszystkich otwartych dokumentów.  
  
## <a name="managing-persistence"></a>Zarządzanie trwałości  
 Projekty kontrolować w środowisku usługi utrwalania, implementując <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Gdy środowiska pytanie, nigdy nie bezpośrednio dokumentu się, zapyta posiadający je projekt (lub hierarchii) można zapisać dokumentu. Umożliwia projekt, aby zapisać dane elementu projektu do lokalnych plików, pliki zdalne, bazy danych, repozytorium lub innych średnia liczba godzin.  
  
 Globalne środowiska przechowuje Normalizacją. Środowisko obsługuje wpisy dla wszystkich okien i dokumentów w Normalizacją, co umożliwia im odbieranie powiadomień specjalnych, takich jak zamknięcia rozwiązania. Ponadto Normalizacją umożliwia środowiska śledzić swoje odpowiadających im węzłów w **Eksploratora rozwiązań**. Normalizacją obsługuje jeden rekord dla każdego obiektu otwarty, możliwy do utrwalenia, w tym zarówno pliki projektu i elementu projektu dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomionej tabeli dokumentu](../../extensibility/internals/running-document-table.md)   
 [Wybór i waluty w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)