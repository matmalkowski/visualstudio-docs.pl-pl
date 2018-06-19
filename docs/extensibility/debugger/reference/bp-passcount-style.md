---
title: BP_PASSCOUNT_STYLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b238012a844016324bbdee4df3cc167051815f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109834"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Określa warunek skojarzony z licznikiem przebiegu punktu przerwania powodujący uruchomienie punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BP_PASSCOUNT_NONE  
 Określa styl licznika przebiegu nie punktu przerwania.  
  
 BP_PASSCOUNT_EQUAL  
 Ustawia styl punktu przerwania przebiegu liczba równe. Punkt przerwania generowane, gdy liczba przebieg jest równe ile razy punkt przerwania zostaje trafiony.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Ustawia styl licznika przebiegu punktu przerwania równą lub większą. Punkt przerwania generowane, gdy liczba razy punkt przerwania zostaje trafiony jest równa lub większa niż liczba przebiegu.  
  
 BP_PASSCOUNT_MOD  
 Określa modulo Liczba przebiegów. Na przykład, jeśli liczba przebieg jest typu `BP_PASSCOUNT_MOD` i przekaż wartość licznika jest 4, uruchamiany punkt przerwania za każdym razem, gdy liczba trafień jest wielokrotnością liczby 4.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `stylePassCount` członkiem [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która z kolei jest elementem członkowskim [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)