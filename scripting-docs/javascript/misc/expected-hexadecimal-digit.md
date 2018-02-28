---
title: Oczekiwano cyfry szesnastkowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="expected-hexadecimal-digit"></a>Oczekiwano liczby szestnastkowej
Utworzono Nieprawidłowa sekwencja ucieczki kodu Unicode. Sekwencje specjalne Unicode zaczynać \u, a następnie dokładnie cztery cyfry szesnastkowe (nie więcej i nie mniej). Cyfry szesnastkowe Unicode może zawierać tylko cyfry 0-9, wielkie litery A-F i wielkością liter a-f. W poniższym przykładzie pokazano poprawnie sformułowany sekwencja ucieczki kodu Unicode.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Pamiętaj, z cyframi szesnastkowymi Unicode zaczynać \u, może zawierać tylko cyfry 0-9, wielkie litery A-F, wielkością liter a-f; i są podzielone na cztery cyfry.  
  
    > [!NOTE]
    >  Jeśli chcesz użyć \u literału tekst w ciągu, a następnie dwa razy — (\\\u)-jedną ucieczki pierwszy ukośnika odwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../javascript/data-types-javascript.md)