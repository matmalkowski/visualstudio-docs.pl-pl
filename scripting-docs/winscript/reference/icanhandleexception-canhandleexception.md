---
title: ICanHandleException::CanHandleException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Określa, czy element wywołujący aparat skryptu może obsłużyć określony wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcepInfo`  
 [in] Wskaźnik do `EXCEPINFO` struktury zawierające informacje, które będą zgłaszane w przypadku nieznalezienia bez obsługi wyjątków.  
  
 `pvar`  
 [in] Wartość skojarzona z powodu wyjątku, takie jak wartość zgłaszanych przez `throw` instrukcji. Ten parametr może mieć `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Obiekt wywołujący może obsłużyć wyjątek|  
|`E_FAIL`|Obiekt wywołujący nie może obsłużyć wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wywołanie `IDispatchEx::InvokeEx`, lub podobnej metody powoduje wyjątek aparatu skryptu kontroli dla obiekt wywołujący w łańcuchu wywołującego skryptu, który obsługuje `ICanHandleException` interfejsu i wskazuje, że może obsłużyć wyjątek. Jeśli wywołujący nie może obsłużyć wyjątek, aparat skryptu zostanie zatrzymany.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)