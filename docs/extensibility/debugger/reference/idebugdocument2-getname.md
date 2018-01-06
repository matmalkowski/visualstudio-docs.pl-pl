---
title: IDebugDocument2::GetName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocument2::GetName
helpviewer_keywords: IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2eeef7ced30d6f8de3b9d0fc6f783502936a4859
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Pobiera nazwę dokumentu w jednym z kilku formularzy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `gnType`  
 [in] Wartość z zakresu od [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) wyliczenia, która określa typ nazwy, aby znaleźć.  
  
 `pbstrFileName`  
 [out] Zwraca ciąg zawierający nazwę dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tej metody można na przykład zwraca nazwę dokumentu jako tytuł lub nazwę pliku lub nawet część nazwy pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)