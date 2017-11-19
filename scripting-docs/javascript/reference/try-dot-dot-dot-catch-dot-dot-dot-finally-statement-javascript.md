---
title: "try... catch... finally — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="trycatchfinally-statement-javascript"></a>try...catch...finally — Instrukcja (JavaScript)
Ustawia bloki kodu, w których błędy generowane w jednym bloku, są obsługiwane w innym. Błędy wewnątrz `try` bloku są przechwytywane w `catch` bloku. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## <a name="parameters"></a>Parametry  
 `tryStatements`  
 Wymagany. Instrukcje, w których może wystąpić błąd.  
  
 `exception`  
 Wymagany. Dowolna nazwa zmiennej. Początkowa wartość `exception` jest wartością zgłoszenia błędu.  
  
 `catchStatements`  
 Opcjonalny. Instrukcje w celu obsługi błędów występujących w skojarzonym `tryStatements`.  
  
 `finallyStatements`  
 Opcjonalny. Instrukcje wykonywane bezwarunkowo po tym, jak zostało wykonane przetwarzanie wszystkich innych błędów.  
  
## <a name="remarks"></a>Uwagi  
 `try...catch...finally` Instrukcji zapewnia sposób obsługi niektóre lub wszystkie błędy, które mogą wystąpić w danym bloku kodu, w trakcie wykonywania kodu. Jeśli wystąpią błędy, które nie są obsługiwane, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zapewnia normalnego komunikatu o błędzie.  
  
 `try` Blok zawiera kod, który może powodować błąd, gdy `catch` blok zawiera kod, który obsługuje niektóre lub wszystkie błędy. W przypadku wystąpienia błędu w `try` bloku, program kontroli jest przekazywana do `catch` bloku. Wartość `exception` jest wartość błąd, który wystąpił w `try` bloku. Jeśli nie występują błędy, kod w `catch` blok nie został wykonany.  
  
 Ten błąd można przekazać do następnego poziomu przy użyciu `throw` instrukcji, aby można było ponownie zgłosić błąd.  
  
 Po wszystkie instrukcje w `try` bloku zostały wykonane i obsługa błędów zostało wykonane `catch` blok, instrukcje w `finally` bloku są wykonywane, czy błąd został obsłużony. Kod w `finally` bloku jest gwarantowana do uruchomienia, o ile nie wystąpił nieobsługiwany błąd (na przykład błędów czasu wykonywania wewnątrz **catch** bloku).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje, że `ReferenceError` wyjątków i wyświetla nazwę błędu i komunikatu.  
  
```JavaScript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób ponowne generowanie błędów, a także wykonywanie zagnieżdżonych `try...catch` bloków. Jeśli błąd jest zgłaszany z zagnieżdżone `try` bloku przekazaniem do zagnieżdżone `catch` bloku ponownie zgłasza wyjątek. Zagnieżdżone `finally` bloku jest uruchamiany przed zewnętrznego `catch` blok obsługuje błędu, a na koniec zewnętrznego `finally` blokowanie działa.  
  
```JavaScript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Począwszy od tryb standardów programu Internet Explorer 8, **catch** bloku nie jest już wymagane dla `finally` do uruchomienia.  
  
## <a name="see-also"></a>Zobacz też  
 [throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [Skrypt ScriptJunkie konfiguracji kreatora przykładowej aplikacji](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)