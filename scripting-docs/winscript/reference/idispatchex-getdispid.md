---
title: IDispatchEx::GetDispID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapuje nazwę jednego członka DISPID odpowiednie, którego można użyć w kolejnych wywołań `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Składnia  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Przekazana nazwa można mapować.  
  
 `grfdex`  
 Określa opcje do uzyskania identyfikatora elementu członkowskiego. Może to być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexNameCaseSensitive|Żądania, które wyszukiwanie nazw odbywać się w sposób, z uwzględnieniem wielkości liter. Może być ignorowane przez obiekt, który nie obsługuje wyszukiwania z uwzględnieniem wielkości liter.|  
|fdexNameEnsure|Żądania, że element członkowski można utworzyć, jeśli jeszcze nie istnieje. Należy utworzyć nowy element członkowski z wartością `VT_EMPTY`.|  
|fdexNameImplicit|Wskazuje, czy obiekt wywołujący jest wyszukiwanie obiektów elementem członkowskim o określonej nazwie Jeśli obiektu podstawowego nie został jawnie określony.|  
|fdexNameCaseInsensitive|Żądania, które wyszukiwanie nazw odbywać się w sposób bez uwzględniania wielkości liter. Może być ignorowane przez obiekt, który nie obsługuje wyszukiwania bez uwzględniania wielkości liter.|  
  
 `pid`  
 Wskaźnik do przyjęcia DISPID wynik w lokalizacji przydzielone przez obiekt wywołujący. Jeśli wystąpi błąd, `pid` zawiera DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`E_OUTOFMEMORY`|Za mało pamięci.|  
|`DISP_E_UNKNOWNNAME`|Nazwa jest nieznana.|  
  
## <a name="remarks"></a>Uwagi  
 `GetDispID`można użyć zamiast `GetIDsOfNames` uzyskać identyfikator DISPID dla danego elementu członkowskiego.  
  
 Ponieważ `IDispatchEx` umożliwia dodawanie i usuwanie elementów członkowskich, zbiór identyfikator DISPID nie pozostaje stała okres istnienia obiektu.  
  
 Nieużywane `riid` parametru w `IDispatch::GetIDsOfNames` został usunięty.  
  
## <a name="example"></a>Przykład  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)