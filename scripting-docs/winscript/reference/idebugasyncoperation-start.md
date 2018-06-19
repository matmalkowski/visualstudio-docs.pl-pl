---
title: IDebugAsyncOperation::Start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd39053e86dce95fa52ba8576814962d13d8b050
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793936"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Powoduje, że operacja asynchroniczna rozpocząć.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `padocb`  
 Interfejs wywołania zwrotnego, który odbiera zdarzenia stanu z tej operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_UNEXPECTED`|Operacja jest już oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje `IDebugSyncOperation::Execute` ma zostać wywołana asynchronicznie w wątku uzyskane z `IDebugSyncOperation::GetTargetThread`. Tę metodę należy wywoływać tylko z wewnątrz wątek debugera; w przeciwnym razie nie powróci do czasu tej operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)