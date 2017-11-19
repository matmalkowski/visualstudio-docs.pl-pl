---
title: IDebugProgram2::GetEngineInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetEngineInfo
helpviewer_keywords: IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a093ab6fc4acc1ea1d1a378b06d721b1316f359f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Pobiera nazwę i identyfikator GUID aparatu debugowania (DE) uruchomieniem tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrEngine`  
 [out] Zwraca nazwę DE uruchomieniem tego programu.  
  
 `pguidEngine`  
 [out] Zwraca identyfikator GUID DE uruchomieniem tego programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy DE definiuje własnego identyfikatora GUID do identyfikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)