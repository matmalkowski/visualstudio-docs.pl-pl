---
title: "Scriptenginemajorversion — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ScriptEngineMajorVersion
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ScriptEngineMajorVersion function
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 815e6fb92744fc2145cae2cbaa6a5574c3ea3ecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="scriptenginemajorversion-function-javascript"></a>ScriptEngineMajorVersion — Funkcja (JavaScript)
Pobiera numer wersji głównej aparat skryptów w użyciu.  
  
## <a name="syntax"></a>Składnia  
  
```  
ScriptEngineMajorVersion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość odpowiada bezpośrednio do wersji informacji zawartych w biblioteki dołączanej (dynamicznie DLL) dla języka skryptów w użyciu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `ScriptEngineMajorVersion` funkcji:  
  
```JavaScript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ScriptEngine — funkcja](../../javascript/reference/scriptengine-function-javascript.md)   
 [Scriptenginebuildversion — funkcja](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Scriptengineminorversion — funkcja](../../javascript/reference/scriptengineminorversion-function-javascript.md)