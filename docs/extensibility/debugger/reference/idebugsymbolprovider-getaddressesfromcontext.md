---
title: IDebugSymbolProvider::GetAddressesFromContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09bc0d4fc0a723c259e2897b95abbd8611b10c7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Ta metoda mapuje kontekstu dokumentu na tablicę adresów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocContext`  
 [in] Kontekstu dokumentu.  
  
 `fStatmentOnly`  
 [in] Jeśli PRAWDA, ogranicza adresy debugowania do jednej instrukcji.  
  
 `ppEnumBegAddresses`  
 [out] Zwraca moduł wyliczający dla początkowy adresów debugowania skojarzone z tym instrukcji lub wiersza.  
  
 `ppEnumEndAddresses`  
 [out] Zwraca [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) modułu wyliczającego dla końcowy adresów debugowania skojarzone z tym instrukcji lub wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kontekstu dokumentu zazwyczaj wskazuje zakres wierszy źródłowych. Ta metoda zapewnia początkowy i końcowy adres debugowania związane z tych wierszy. W przypadku niektórych języków Zezwalaj instrukcje, które obejmują wiele wierszy lub wierszy, które zawiera więcej niż jedną instrukcję. Ta metoda zapewnia flagę, aby ograniczyć adresy debugowania do jednej instrukcji.  
  
 Istnieje możliwość dla jednej instrukcji wielu adresów debugowania, tak jak w przypadku szablonów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)