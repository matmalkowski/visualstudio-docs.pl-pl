---
title: IDebugDisassemblyStream2::GetSize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetSize
helpviewer_keywords: IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35dfb225c6359e3b039b21255b1e6ba5979c3e6f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Pobiera rozmiar w instrukcjach tego strumienia dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pnSize`  
 [out] Zwraca rozmiar w instrukcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę można przydzielić tablicy [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, które są następnie przekazywane do [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)