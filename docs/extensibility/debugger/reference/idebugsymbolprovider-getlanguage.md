---
title: IDebugSymbolProvider::GetLanguage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetLanguage
helpviewer_keywords: IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cd5cf44f56b91d5e6c04b220e36c7f0e82d3159c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Ta metoda pobiera język używany do kompilowania kodu pod adresem debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```csharp  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Adres obiektu reprezentowanego przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
 `pguidLanguage`  
 [out] Zwraca `GUID` , który określa język.  
  
 `pguidLanguageVendor`  
 [out] Zwraca `GUID` , który określa dostawcy języka.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aparat debugowania wywołuje tę metodę, aby uzyskać informacje potrzebne do wybierz ewaluatora wyrażenia poprawne.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)