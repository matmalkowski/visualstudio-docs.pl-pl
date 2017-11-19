---
title: "Błąd specjalne właściwości asynchronicznego Windows metody środowiska uruchomieniowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>Błąd specjalne właściwości asynchronicznego Windows metody środowiska uruchomieniowego
Może być trudne do debugowania metod asynchronicznych środowiska wykonawczego systemu Windows w języku JavaScript, ponieważ może zostać zgłoszony błąd z innym głębokie w stosie wywołań. Kod JavaScript `Error` obiekt ma dodatkowe właściwości, które są wyświetlane tylko wtedy, gdy zostanie zgłoszony błąd ze środowiska wykonawczego systemu Windows metody asynchronicznej gdy aplikacja działa w trybie debugowania.  
  
## <a name="special-error-properties"></a>Błąd specjalne właściwości  
 Obiekt błąd, który jest wynikiem nieudanej operacji asynchronicznych środowiska wykonawczego systemu Windows w trybie debugowania ma następujące właściwości specjalne:  
  
-   `asyncOpSource`(Obiekt) Pobiera informacje o oryginalnej lokalizacji, w którym wykonano wywołanie, który powoduje błąd. Właściwość `asyncOpSource.originatingCall` (ciąg) Wyświetla lokalizację w kodzie użytkownika, które powstały operację asynchroniczną.  
  
-   asyncOpType (ciąg) pobiera nazwę typu operację asynchroniczną, która wywołała błędu.  
  
 Aby uzyskać więcej informacji o błędach z operacji asynchronicznych zobacz:  
  
-   [Sposób obsługi błędów z niesie obietnice](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Rozwiązywanie problemów z błędami środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)