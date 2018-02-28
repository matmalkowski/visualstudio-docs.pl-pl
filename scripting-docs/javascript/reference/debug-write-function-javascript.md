---
title: "Debug.Write — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugwrite-function-javascript"></a>Debug.write — Funkcja (JavaScript)
Wysyła ciągi do debugera skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 *str1 str2,..., strN*  
 Opcjonalny. Ciągi do wysłania do debugera skryptów.  
  
## <a name="remarks"></a>Uwagi  
 `Debug.write` Funkcja wysyła ciągi do okna bezpośredniego debugera skryptów w czasie wykonywania. Jeśli skrypt nie jest debugowany, `Debug.write` funkcja nie ma wpływu.  
  
 `Debug.write` Funkcji jest niemal identyczny `Debug.writeln` funkcji. Jedyną różnicą jest to, że `Debug.writeln` funkcja wysyła znaku nowego wiersza po wysłaniu ciągi.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Debug.write` funkcji, aby wyświetlić wartość zmiennej w oknie bezpośrednim debugera skryptów.  
  
> [!NOTE]
>  Do uruchomienia tego przykładu, muszą mieć zainstalowany debugera skryptów i skrypt musi działać w trybie debugowania.  
>   
>  Program Internet Explorer 8 zawiera [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugera. Jeśli używasz starszej wersji programu Internet Explorer, zobacz [porady: Włączanie i Rozpocznij debugowanie skryptu z programu Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [Debug — obiekt](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Debug.writeln — funkcja](../../javascript/reference/debug-writeln-function-javascript.md)