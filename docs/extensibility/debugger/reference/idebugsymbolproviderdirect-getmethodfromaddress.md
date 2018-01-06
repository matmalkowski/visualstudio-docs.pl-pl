---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3924a128450930dd057c8a5bda7e2466ae17309e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Pobiera informacje o metodzie pod adresem określonym debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Debugowanie adres, który jest reprezentowany przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
 `pGuid`  
 [out] Unikatowy identyfikator modułu.  
  
 `pAppID`  
 [out] Identyfikator domeny aplikacji.  
  
 `pTokenClass`  
 [out] Token, który reprezentuje klasę zawierającego.  
  
 `pTokenMethod`  
 [out] Token, który reprezentuje modułu.  
  
 `pdwOffset`  
 [out] Przesunięcie w bajtach od początku `pAddress` parametru.  
  
 `pdwVersion`  
 [out] Numer wersji metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)