---
title: Błędy środowiska wykonawczego języka JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT-32725
- VS.WebClient.Help.SCRIPT7002
- VS.WebClient.Help.SCRIPT1001
- VS.WebClient.Help.SCRIPT16389
- VS.WebClient.HelpSCRIPT50
- VS.WebClient.HelpSCRIPT70
- VS.WebClient.HelpSCRIPT87
- VS.WebClient.HelpSCRIPT65535
- VS.WebClient.HelpSCRIPT445
- VS.WebClient.HelpSCRIPT600
- VS.WebClient.HelpSCRIPT2343
- VS.WebClient.HelpSCRIPT122
- VS.WebClient.HelpSCRIPT28
- VS.WebClient.HelpSCRIPT16386
- VS.WebClient.HelpSCRIPT7015
- VS.WebClient.HelpSCRIPT3
- VS.WebClient.HelpSCRIPT16388
- VS.WebClient.HelpSCRIPT14
- VS.WebClient.HelpSCRIPT12030
- VS.WebClient.HelpSCRIPT12029
- VS.WebClient.HelpSCRIPT1001
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- run-time errors, JavaScript
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb75c59fae32911c3dd3a7468439a198d7191755
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791752"
---
# <a name="javascript-run-time-errors"></a>Błędy środowiska wykonawczego JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]błędy środowiska wykonawczego są błędów występujących, gdy skrypt próbuje wykonać akcję system nie może wykonać. Gdy wyrażeniach zmiennych są oceniane i jest przydzielana pamięć mogą zostać wyświetlone błędy czasu wykonywania.  
  
## <a name="windows-runtime-errors"></a>Błędy środowiska wykonawczego systemu Windows  
 Jeśli używasz interfejsów API środowiska wykonawczego systemu Windows w Twojej [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji, mogą pojawić błędy JavaScript, które zostały zamienione z wyników HRESULT środowiska wykonawczego systemu Windows. Wyników HRESULT środowiska wykonawczego systemu Windows w zakresie przez 0x80070000 są konwertowane na JavaScript — błędy przez pobranie wartość szesnastkową niski usługi bits i konwertowana na format dziesiętny. Na przykład HRESULT 0x80070032 jest konwertowana na wartość dziesiętna 50, a błąd JavaScript jest SCRIPT50. HRESULT 0x80074005 jest konwertowana na wartość dziesiętna 16389 i SCRIPT16389 jest błąd kodu JavaScript.  
  
## <a name="errors"></a>błędy  
  
|Numer błędu|Opis|  
|------------------|-----------------|  
|5|[Odmowa dostępu](../../javascript/misc/access-is-denied.md)|  
|438|[Obiekt nie obsługuje tej właściwości lub metody](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Za mało pamięci|  
|5029|[Długość tablicy musi być skończony dodatnią liczbą całkowitą](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[Długość tablicy musi być przypisany dodatnią liczbę całkowitą](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Oczekiwano obiektu typu tablica lub argumentów](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Oczekiwano obiektu logicznego](../../javascript/misc/boolean-expected.md)|  
|5003|[Nie można przypisać do wyniku funkcji](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[Nie można przypisać do "this"](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Odwołanie cykliczne w argumencie wartości nie jest obsługiwane.](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Oczekiwany obiekt Date](../../javascript/misc/date-object-expected.md)|  
|5015|[Oczekiwano obiektu wyliczenia](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Wyjątek zgłoszony i nieprzechwycony](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[Oczekiwano ")" w wyrażeniu regularnym](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[Oczekiwano "&#93;" w wyrażeniu regularnym](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[Funkcja nie zawiera prawidłowego prototypu obiektu](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Oczekiwano funkcji](../../javascript/misc/function-expected.md)|  
|5008|[Niedozwolone przypisanie](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Nieprawidłowy zakres w zestawie znaków](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Nieprawidłowy argument zastępczy](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[JavaScript Oczekiwany obiekt](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Oczekiwano liczby](../../javascript/misc/number-expected.md)|  
|5007|[Oczekiwany obiekt](../../javascript/misc/object-expected.md)|  
|5012|[Oczekiwany element członkowski obiektu](../../javascript/misc/object-member-expected.md)|  
|5016|[Oczekiwano obiektu będącego wyrażeniem regularnym](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Ciąg oczekiwany](../../javascript/misc/string-expected.md)|  
|5017|[Błąd składni w wyrażeniu regularnym](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[Liczba cyfr ułamkowych jest poza zakresem](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[Dokładność jest spoza zakresu](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[Identyfikator URI, który ma być zdekodowany jest nie prawidłowym kodowaniem](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Niezdefiniowany identyfikator](../../javascript/misc/undefined-identifier.md)|  
|5018|[Nieoczekiwany kwantyfikator](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[Oczekiwano VBArray](../../javascript/misc/vbarray-expected.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy składniowe JavaScript](../../javascript/reference/javascript-syntax-errors.md)