---
title: Scriptengineminorversion — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- ScriptEngineMinorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineMinorVersion function
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1be01c0ee10cac1c68d4750455151032a59a8e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791371"
---
# <a name="scriptengineminorversion-function-javascript"></a>ScriptEngineMinorVersion — Funkcja (JavaScript)
Pobiera podrzędny numer wersji aparatu skryptów w użyciu.  
  
## <a name="syntax"></a>Składnia  
  
```  
ScriptEngineMinorVersion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość odpowiada bezpośrednio do wersji informacji zawartych w biblioteki dołączanej (dynamicznie DLL) dla języka skryptów w użyciu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `ScriptEngineMinorVersion` funkcji.  
  
```JavaScript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ScriptEngine — funkcja](../../javascript/reference/scriptengine-function-javascript.md)   
 [Scriptenginebuildversion — funkcja](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Scriptenginemajorversion — funkcja](../../javascript/reference/scriptenginemajorversion-function-javascript.md)