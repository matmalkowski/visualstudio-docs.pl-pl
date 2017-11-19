---
title: IDispatchEx::GetMemberProperties | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Pobiera właściwości elementów członkowskich.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Określa element członkowski. Używa `GetDispID` lub `GetNextDispID` do uzyskania identyfikatora wysyłania.  
  
 `grfdexFetch`  
 Określa właściwości, które można pobrać. Może to być kombinacją wartości na liście `pgrfdex` i/lub kombinację następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|grfdexPropCanAll|Łączy fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct i fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Łączy fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct i fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Łączy fdexPropNoSideEffects i fdexPropDynamicType.|  
|grfdexPropAll|Łączy grfdexPropCanAll, grfdexPropCannotAll i grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adres `DWORD` odbierająca wymaganych właściwości. Może to być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexPropCanGet|Element członkowski można uzyskać za pomocą DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Element członkowski nie można uzyskać za pomocą DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Element członkowski można ustawić za pomocą DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Nie można ustawić elementu członkowskiego przy użyciu DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Element członkowski można ustawić za pomocą DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Nie można ustawić elementu członkowskiego przy użyciu DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Element członkowski nie ma żadnych efektów ubocznych. Na przykład debugera można bezpiecznie get/set/wywołanie tego elementu członkowskiego bez zmiany stanu skryptu debugowany.|  
|fdexPropDynamicType|Element członkowski jest dynamiczny i zmienić okres istnienia obiektu.|  
|fdexPropCanCall|Element członkowski można wywołać jako metodę przy użyciu DISPATCH_METHOD.|  
|fdexPropCannotCall|Nie można wywołać elementu członkowskiego jako metody przy użyciu DISPATCH_METHOD.|  
|fdexPropCanConstruct|Jako konstruktora przy użyciu DISPATCH_CONSTRUCT można wywołać elementu członkowskiego.|  
|fdexPropCannotConstruct|Nie można wywołać elementu członkowskiego jako przy użyciu DISPATCH_CONSTRUCT konstruktora.|  
|fdexPropCanSourceEvents|Element członkowski mogą wyzwalać zdarzeń.|  
|fdexPropCannotSourceEvents|Element członkowski nie może wyzwalać zdarzeń.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`DISP_E_UNKNOWNNAME`|Nazwa jest nieznana.|  
  
## <a name="example"></a>Przykład  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)