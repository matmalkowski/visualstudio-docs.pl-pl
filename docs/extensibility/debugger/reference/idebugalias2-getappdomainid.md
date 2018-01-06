---
title: IDebugAlias2::GetAppDomainId | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a8ddebc0f540be650650595e5b808c9c4b19f706
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Pobiera identyfikator domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pappDomainId`  
 [out] Zwraca identyfikator domeny aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Utworzono zmiany identyfikator domeny aplikacji przy każdym uruchomieniu aplikacji i nowej domeny aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)