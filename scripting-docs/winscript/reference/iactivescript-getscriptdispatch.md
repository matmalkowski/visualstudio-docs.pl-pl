---
title: IActiveScript::GetScriptDispatch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791950"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Pobiera `IDispatch` interfejsu dla metody i właściwości skojarzone z obecnie uruchamianie skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrItemName`  
 [in] Adres buforu, który zawiera nazwę elementu, dla którego wywołujący musi obiektu dyspozytora skojarzone. Jeśli ten parametr ma `NULL`, zawiera obiekt wysyłania jako elementy członkowskie wszystkie globalne metody i właściwości zdefiniowane przez skrypt. Za pomocą `IDispatch` interfejs oraz skojarzonych z nimi `ITypeInfo` interfejsu hosta można wywołać metody skryptu lub widoku i modyfikować zmiennych skryptu.  
  
 `ppdisp`  
 [out] Adres zmiennej, która otrzymuje wskaźnik do obiektu skojarzone z globalnej metody i właściwości skryptu. Jeśli aparat skryptów nie obsługuje takiego obiektu `NULL` jest zwracany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu dyspozytora; `ppdisp` parametr ma wartość NULL.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ metody i właściwości mogą być dodawane przez wywołanie [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interfejsu `IDispatch` interfejsu zwracane przez tę metodę można dynamicznie obsługuje nowych metod i właściwości. Podobnie `IDispatch::GetTypeInfo` metoda powinna zwrócić nowe, unikatowe `ITypeInfo` interfejsu woluminowi metody i właściwości. Należy jednak pamiętać, nie może zmienić język aparaty `IDispatch` interfejsu w sposób niezgodny ze wszystkimi poprzedniej `ITypeInfo` zwróciła interfejsu. Oznacza to, na przykład, że identyfikator DISPID nigdy nie zostanie ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)