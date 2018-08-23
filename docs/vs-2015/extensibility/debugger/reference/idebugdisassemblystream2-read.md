---
title: IDebugDisassemblyStream2::Read | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 117a90cbcfd96db808252b9653ee4c0015e92b0d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42692260"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugDisassemblyStream2::Read](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2-read).  
  
Odczytuje instrukcje od bieżącej pozycji w strumieniu dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwInstructions`  
 [in] Liczba instrukcji do przekształcenia. Ta wartość jest również maksymalną długość `prgDisassembly` tablicy.  
  
 `dwFields`  
 [in] Kombinacja flag z [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Wyliczenie wskazujące, które pola `prgDisassembly` są wypełnione.  
  
 `pdwInstructionsRead`  
 [out] Zwraca liczbę instrukcji faktycznie dezasemblowany.  
  
 `prgDisassembly`  
 [out] Tablica [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktur, które jest wypełniane zdezasemblowany kod, co Struktura na dezasemblowany instrukcji. Długość tej tablicy jest zależna od `dwInstructions` parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Maksymalna liczba instrukcje, które są dostępne w bieżącym zakresie można uzyskać przez wywołanie metody [getsize —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) metody.  
  
 Można zmienić bieżącej pozycji, gdy następnej instrukcji są odczytywane z przez wywołanie metody [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metody.  
  
 `DSF_OPERANDS_SYMBOLS` Flagi mogą być dodawane do `DSF_OPERANDS` znacznik w `dwFields` parametru, aby wskazać, że nazwy symboli powinien być używany, gdy deasemblowanie instrukcje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Getsize —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Wyszukiwanie](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

