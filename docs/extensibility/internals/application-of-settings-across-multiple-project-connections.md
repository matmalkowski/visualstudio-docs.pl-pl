---
title: "Stosowanie ustawień przez wiele połączeń projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9750d946a941e86a6c0a6973661f00f8f44cf9b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Stosowanie ustawień przez wiele połączeń projektu
Wtyczka do kontroli źródła utworzony za pomocą 1.2 interfejsu API dodatku typu Plug-in kontroli źródła, można użyć do wykonania tej samej operacji kontroli źródła dla wielu projektów lub wielu kontekstów połączenia operacji zbiorczej. Partie można wyeliminować nadmiarowego, okien dialogowych z doświadczenia użytkownika projektu.  
  
 Jeśli użytkownik wybierze wiele elementów, które należą do więcej niż jedno połączenie dodatku plug-in kontroli źródła utworzony za pomocą 1.1 interfejsu API dodatku typu Plug-in kontroli źródła o (na przykład dwa projekty sieci Web na maszynach inny udział plików) i sprawdza je, użytkownik zobaczy tego samego okno dialogowe wielokrotnie. Dzieje się tak nawet wtedy, gdy użytkownik kliknie **Zastosuj do wszystkich** Sprawdź pola w oknie dialogowym, ponieważ IDE resetuje stanu dla każdego połączenia kontekstu.  
  
## <a name="new-capability-flag"></a>Nowe możliwości flagi  
 `SccBeginBatch`Zestawy funkcji `SCC_CAP_BATCH` Flaga do wskazywania wsadową operację w toku  
  
## <a name="new-functions"></a>Nowe funkcje  
 Następujące nowe funkcje obsługi operacji zbiorczej:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch` Funkcja rozpoczyna grupy operacji kontroli źródła. `SccEndBatch`Zamyka grupy. Grupy nie mogą być zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Nowości w źródła formantu wtyczka interfejsu API wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)