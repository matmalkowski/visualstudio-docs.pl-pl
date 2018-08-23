---
title: Trwałość i uruchamianie dokumentu tabeli | Dokumentacja firmy Microsoft
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
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44f8025bd20fe6522ec0f835e299a2a9efd9ca1e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682525"
---
# <a name="persistence-and-the-running-document-table"></a>Trwałość i uruchamianie tabeli dokumentów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [trwałość i uruchamianie tabeli dokumentu](https://docs.microsoft.com/visualstudio/extensibility/internals/persistence-and-the-running-document-table).  
  
W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, projekty są całkowicie odpowiedzialni za zarządzanie trwałości ich elementów projektu, które realizowane przy użyciu usługi, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumenty są podstawową jednostką trwałości w środowisku Visual Studio. Projekty koordynować otwieranie, zapisywanie i zmiana nazwy dokumentów za pomocą uruchomionej tabeli dokumentu (Normalizacją) z zasobem, który śledzi stan wszystkich otwartych dokumentach.  
  
## <a name="managing-persistence"></a>Zarządzanie trwałości  
 Projekty sterowania usługą trwałości środowiska poprzez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfejsu. Podczas środowiska prosi nigdy bezpośrednio dokumentu się, prosi będąca właścicielem projektu (lub hierarchia) można zapisać dokumentu. Dzięki temu możliwe dla projektu, aby zapisać swoje dane elementu projektu w lokalnych plików, pliki zdalne, bazę danych, repozytorium lub innego nośnika.  
  
 W środowisku globalnym zachowuje Normalizacją. Środowisko obsługuje wpisy dla wszystkich okien i dokumentów w Normalizacją, co umożliwia im odbieranie powiadomień specjalne, np. po zamknięciu rozwiązania. Ponadto Normalizacją umożliwia środowiska śledzić ich odpowiednich węzłów w **Eksploratora rozwiązań**. Normalizacją utrzymuje jeden rekord dla każdego obiektu otwarte, stałe, w tym pliki projektu i elementu projektu dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md)   
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

