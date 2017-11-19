---
title: IDispatchEx::DeleteMemberByDispID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 573eb60dc901e43706835c4d627b25bd54bbe751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Usuwa element członkowski przy użyciu identyfikatora DISPID.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator elementu członkowskiego. Używa `GetDispID` lub `GetNextDispID` do uzyskania identyfikatora wysyłania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Element członkowski istnieje, ale nie można go usunąć.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element członkowski zostanie usunięty, identyfikator DISPID musi są ważne `GetNextDispID`.  
  
 Jeśli element członkowski o podanej nazwie zostanie usunięty, a później zostaje odtworzone element członkowski o takiej samej nazwie, identyfikator DISPID powinna być taka sama. (Czy nazwy elementów członkowskich, które różnią się tylko wielkością liter są "same" jest zależny od obiektu).  
  
## <a name="example"></a>Przykład  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)