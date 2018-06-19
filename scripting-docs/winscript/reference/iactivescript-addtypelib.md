---
title: IActiveScript::AddTypeLib | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791773"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Dodaje bibliotekę typów obszar nazw dla skryptu. Jest to podobne do `#include` dyrektywy języka C/C++. Umożliwia to zestaw wstępnie zdefiniowanych elementów takich jak definicje klas, `typedefs`oraz o nazwie stałe, które mają zostać dodane do środowiska czasu wykonywania dla skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidTypeLib`  
 [in] Identyfikator CLSID biblioteki typów, aby dodać.  
  
 `dwMaj`  
 [in] Numer wersji głównej.  
  
 `dwMin`  
 [in] Numer wersji pomocniczej.  
  
 `dwFlags`  
 [in] Flagi opcji. Mogą być następujące:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Biblioteka typów zawiera opis formantu ActiveX, używany przez hosta.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
|`TYPE_E_CANTLOADLIBRARY`|Nie można załadować określonej biblioteki typów.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)