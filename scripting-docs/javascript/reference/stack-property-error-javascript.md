---
title: "Stack — właściwość (błąd) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="stack-property-error-javascript"></a>stack — Właściwość (Błąd) (JavaScript)
Pobiera lub ustawia bufor błędów jako ciąg, który zawiera ramek stosu śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Uwagi  
 `stack` Właściwość jest ustawiona na `undefined` po błędu jest tworzony i pobiera informacje o śledzeniu, gdy zostanie zgłoszony błąd. Jeśli wiele razy, występuje błąd `stack` właściwość jest aktualizowana każdorazowo błąd.  
  
 Ramki stosu są wyświetlane w następującym formacie: **na FunctionName (\<pełną nazwę lub adres URL >:\<numer wiersza >:\<numer kolumny >)**  
  
 Jeśli tworzenie obiektu błąd i ustawić wartość ślad stosu wartość nie jest zastępowana generowany jest błąd.  
  
 `stack` Właściwości nie są wyświetlane funkcji śródwierszowych jego ramki. Pokazywane są tylko fizyczne stosu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać stosu, gdy jest przechwytywanie wystąpił błąd.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak i następnie Uzyskaj stosu.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Dotyczy**: [Error — obiekt](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Description — właściwość (błąd)](../../javascript/reference/description-property-error-javascript.md)   
 [Message — właściwość (błąd)](../../javascript/reference/message-property-error-javascript.md)   
 [name — właściwość (błąd)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit właściwość (błąd)](../../javascript/reference/stacktracelimit-property-error-javascript.md)