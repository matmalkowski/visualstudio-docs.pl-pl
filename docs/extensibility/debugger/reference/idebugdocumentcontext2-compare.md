---
title: IDebugDocumentContext2::Compare | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f41b0e5973af8e0cb65f093f51137059084c9792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105492"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Porównuje tego kontekstu dokumentu do danej tablicy kontekstów dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compare`  
 [in] Wartość z zakresu od [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) wyliczenia, która określa typ porównania.  
  
 `rgpDocContextSet`  
 [in] Tablica [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiekty reprezentujące kontekstów dokumentu są porównywane do.  
  
 `dwDocContextSetLen`  
 [in] Długość tablicy kontekstów dokumentu do porównania.  
  
 `pdwDocContext`  
 [out] Zwraca indeks `rgpDocContextSet` tablicy pierwszy kontekstu dokumentu, który spełnia porównanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` Jeśli znaleziono dopasowanie. Zwraca `S_FALSE` Jeżeli nie znaleziono dopasowania. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiektów, które są przekazywane w tablicy musi być implementowana przez tego samego aparatu debugowania, który implementuje `IDebugDocumentContext2` obiekt wywoływany w przeciwnym razie wynik porównania jest nieprawidłowa.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)