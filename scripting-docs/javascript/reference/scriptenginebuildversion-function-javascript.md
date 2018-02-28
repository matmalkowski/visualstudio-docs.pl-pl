---
title: "Scriptenginebuildversion — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- ScriptEngineBuildVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ScriptEngineBuildVersion function
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd458d43bebfb0d0e0b2cb6bebb483c22a60b4f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginebuildversion-function-javascript"></a>ScriptEngineBuildVersion — Funkcja (JavaScript)
Pobiera numer wersji kompilacji aparatu skryptów w użyciu.  
  
## <a name="syntax"></a>Składnia  
  
```  
ScriptEngineBuildVersion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość odpowiada bezpośrednio do wersji informacji zawartych w biblioteki dołączanej (dynamicznie DLL) dla języka skryptów w użyciu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `ScriptEngineBuildVersion` funkcji:  
  
```JavaScript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ScriptEngine — funkcja](../../javascript/reference/scriptengine-function-javascript.md)   
 [Scriptenginemajorversion — funkcja](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Scriptengineminorversion — funkcja](../../javascript/reference/scriptengineminorversion-function-javascript.md)