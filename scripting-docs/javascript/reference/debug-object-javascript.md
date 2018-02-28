---
title: "Debug — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
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
- debug
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Debug object
- Debug object, about Debug object
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6286e5db853daa97e43f36a1467abe90cbced5c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debug-object-javascript"></a>Obiekt Debug (JavaScript)
Wewnętrzne globalny obiekt, który wysyła dane wyjściowe do debugera.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.function  
```  
  
## <a name="remarks"></a>Uwagi  
 Nie można utworzyć wystąpienia obiektu debugowania. Dostęp można uzyskać jego właściwości i metod wywoływania `function`.  
  
 Istnieją różne sposoby debugowania programu Internet Explorer i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. W [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji, `write` i `writeln` funkcje `Debug` obiektów wyświetlanych ciągów w Visual Studio **dane wyjściowe** okna w czasie wykonywania. Aby uzyskać więcej informacji o debugowaniu [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji, zobacz [debugowania uniwersalnych aplikacji systemu Windows w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps.md).  
  
 Debugowanie skryptów w programie Internet Explorer, muszą mieć zainstalowany debugera skryptów i skrypt musi działać w trybie debugowania. Program Internet Explorer 8 i nowszych obejmują [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugera. Jeśli używasz starszej wersji programu Internet Explorer, zobacz [porady: Włączanie i Rozpocznij debugowanie skryptu z programu Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Jeśli skrypt nie jest debugowany, funkcje nie obowiązują.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `write` funkcji, aby wyświetlić wartość zmiennej.  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="constants"></a>Stałe  
 [Stałe debugowania](../../javascript/reference/debug-constants.md)  
  
## <a name="properties"></a>Właściwości  
 [Debug.debuggerenabled — właściwość](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setnonusercodeexceptions — właściwość](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## <a name="functions"></a>Funkcje  
 [Funkcja Debug.msTraceAsyncCallbackStarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Funkcja Debug.msTraceAsyncCallbackCompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Funkcja Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Funkcja Debug.msTraceAsyncOperationStarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Funkcja Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.Write — funkcja](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln — funkcja](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugger — instrukcja](../../javascript/reference/debugger-statement-javascript.md)