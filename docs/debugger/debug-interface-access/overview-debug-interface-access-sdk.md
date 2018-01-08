---
title: "Omówienie (Debug Interface Access SDK) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb13b9a77bcd34b22a7a82182a63440cb02a4e76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="overview-debug-interface-access-sdk"></a>Przegląd (Zestaw SDK dostępu do interfejsu debugowania)
Umożliwia dostęp do informacji debugowania Microsoft DIA SDK. DIA SDK zawiera oparte na modelu COM zestawu interfejsów API, która eliminuje potrzebę ponownego zapisywania kodu przy każdej zmianie Microsoft format informacji debugowania. DIA SDK umożliwia także odczytywać wybrane grupy poprzednie wersje informacji o debugowaniu w plikach .pdb i .dbg generowane przez [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] w wersji 5.0 lub nowszej.  
  
 Każdego interfejsu w DIA SDK reprezentuje różne obiekty COM, z wyjątkiem w przypadku, gdy zaznaczono inaczej. Dodatkowe interfejsy, a w związku z tym dodatkowe obiekty są tworzone za pomocą jawnego zapytania, takie jak [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) lub [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), a nie przez wywołanie metody `QueryInterface` na istniejące wskaźniki interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)