---
title: "Debug.writeln — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Debug.writeln — Funkcja (JavaScript)
Wysyła ciągi do debugera skryptów, a następnie znaku nowego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 *str1 str2,..., strN*  
 Opcjonalny. Ciągi do wysłania do debugera skryptów.  
  
## <a name="remarks"></a>Uwagi  
 `Debug.writeln` Funkcja wysyła ciągów, następuje znak nowego wiersza do okna bezpośredniego Microsoft Script Debugger w czasie wykonywania. Jeśli skrypt nie jest debugowany, `Debug.writeln` funkcja nie ma wpływu.  
  
 `Debug.writeln` Funkcji jest niemal identyczny `Debug.write` funkcji. Jedyną różnicą jest to, że `Debug.write` funkcja nie wysyła znaku nowego wiersza po wysłaniu ciągi.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Debug.writeln` funkcji, aby wyświetlić wartość zmiennej w oknie bezpośrednim Microsoft Script Debugger.  
  
> [!NOTE]
>  Do uruchomienia tego przykładu, muszą mieć zainstalowany debugera skryptów i skrypt musi działać w trybie debugowania.  
>   
>  Program Internet Explorer 8 zawiera [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugera. Jeśli używasz starszej wersji programu Internet Explorer, zobacz [porady: Włączanie i Rozpocznij debugowanie skryptu z programu Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [Debug — obiekt](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Debug.Write — funkcja](../../javascript/reference/debug-write-function-javascript.md)