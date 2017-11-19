---
title: CANSTOP_REASON | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CANSTOP_REASON
helpviewer_keywords: CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4446921759c1b72dd75c31b52bab35d02b219942
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="canstopreason"></a>CANSTOP_REASON
Używany do określenia, czy program można zatrzymać wykonywania po osiągnięciu określonego punktu w realizacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 CANSTOP_ENTRYPOINT  
 Określa punkt wejścia danego programu.  
  
 CANSTOP_STEPIN  
 Określa Wkraczanie do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodę, aby potwierdzić z sesji debugowania Menedżera (SDM), jeśli można zatrzymać po osiągnięciu punktu wejścia programu lub Wkraczanie do metody lub funkcji.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)