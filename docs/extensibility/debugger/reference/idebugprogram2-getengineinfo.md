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
ms.workload: vssdk
ms.openlocfilehash: 3d643b3e2ca160d9898ec13ad09bdc654c88c2c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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