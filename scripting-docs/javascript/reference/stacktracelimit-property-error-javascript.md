---
title: "stackTraceLimit właściwość (błąd) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>stackTraceLimit Właściwość (Błąd) (JavaScript)
Pobiera lub ustawia limit śledzenia bufora, który jest odpowiednikiem liczba ramek błąd do wyświetlenia. Domyślny limit wynosi 10.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Uwagi  
 Można ustawić `stackTraceLimit` właściwości do dowolnej wartości dodatniej między 0 a `Infinity`. Jeśli `stackTraceLimit` właściwość jest ustawiona na 0 w czasie, zostanie zgłoszony błąd, nie ślad stosu jest wyświetlany. Jeśli właściwość jest ustawiona wartość ujemną lub wartość nieliczbowy, wartość jest konwertowana na 0. Jeśli ustawiono stackTraceLimit `Infinity`, cały stos jest wyświetlany. W przeciwnym razie `ToUint32` służy do konwertowania wartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak i następnie Uzyskaj limit śledzenia bufora.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w programie Internet Explorer 10 i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
 **Dotyczy**: [Error — obiekt](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Description — właściwość (błąd)](../../javascript/reference/description-property-error-javascript.md)   
 [Message — właściwość (błąd)](../../javascript/reference/message-property-error-javascript.md)   
 [name — właściwość (błąd)](../../javascript/reference/name-property-error-javascript.md)   
 [Stack — właściwość (błąd)](../../javascript/reference/stack-property-error-javascript.md)