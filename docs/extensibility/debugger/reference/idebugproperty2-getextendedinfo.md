---
title: IDebugProperty2::GetExtendedInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetExtendedInfo
helpviewer_keywords: IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7456ebe1e28618270bd90f09186ec49814c62b66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Pobiera rozszerzone informacje dla właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidExtendedInfo`  
 [in] Identyfikator GUID, który określa typ danych rozszerzonych do pobrania. Aby uzyskać więcej informacji, zobacz uwagi.  
  
 `pExtendedInfo`  
 [out] Zwraca `VARIANT` (C++) lub obiektu (C#), który można pobrać informacji o rozszerzonych właściwości. Na przykład ten parametr może zwrócić `IUnknown` interfejs, który można wykonać zapytania o [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfejsu. Aby uzyskać więcej informacji, zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Jeśli nie ma żadnych rozszerzonych informacji do pobrania.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda istnieje na potrzeby pobierania informacji, które nie nadają się do pobieranych przez wywołanie metody [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.  
  
 Następujące identyfikatory GUID zwykle są rozpoznawane przez tę metodę (identyfikator GUID wartości są określone dla C#, ponieważ nazwa nie jest dostępna w żadnych zestawów). Można tworzyć dodatkowe identyfikatorów GUID do użytku wewnętrznego.  
  
|Nazwa|Identyfikator GUID|Opis|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Zwraca `IUnknown` interfejs do dokumentu. Zazwyczaj [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfejsu można uzyskać z tego `IUnknown` interfejsu.|  
|guidCodeContext|{e2fc65e-56ce - 11d 1-b528-00aax004a8797}|Zwraca `IUnknown` interfejs do kontekstu dokumentu. Zazwyczaj [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu można uzyskać z tego `IUnknown` interfejsu.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Zwraca ciąg zawierający identyfikator CLSID podglądu niestandardowego zwykle implementowany przez ewaluatora wyrażeń.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Zwraca liczbę 32-bitowa reprezentująca numer gniazda żądaną, jeśli ta właściwość reprezentuje adres lokalny kodu zarządzanego.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Zwraca ciąg zawierający podpis skojarzony z obiektem właściwość zmiennej.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)