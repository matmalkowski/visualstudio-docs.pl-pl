---
title: Odmowa dostępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9c097cd09712d19acf5a0e4999b5c7a47469f958
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788614"
---
# <a name="access-is-denied"></a>Odmowa dostępu
Skrypt próbował uzyskać dostęp do danych ze źródła innego niż hosta bieżącej strony. Te Same zasady pochodzenia następuje programu Internet Explorer i innych przeglądarek umożliwia skrypty dostęp do danych tylko z źródeł schemat, hosta i numer portu, adresu URL bieżącej strony.  
  
 Na przykład jeśli bieżąca strona jest https://employees.mycompany.com, nie masz dostępu do danych z następujących adresów URL:  
  
-   http://Data.contoso.com, ponieważ używa protokołu HTTP zamiast HTTPS.  
  
-   https://somedatasource.com, ponieważ jest on inną domenę.  
  
-   https://Employees.mycompany.com:8888, ponieważ używa on innego portu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź, czy w przypadku próby wywołania interfejsu API obsługuje JSONP lub CORS, które są dwie metody bezpiecznie Zezwalaj na wykonywanie skryptów między źródłami.  
  
-   Jeśli próbujesz wywołać interfejs API REST, Refaktoryzuj tego wywołania do kodu po stronie serwera, a następnie udostępnić nowy punkt końcowy REST dla skryptów po stronie klienta.  
  
     Aby uzyskać dodatkowe informacje Wyszukaj odnoszących się do tych samych zasad pochodzenia, JSONP i CORS dokumentację w trybie online.