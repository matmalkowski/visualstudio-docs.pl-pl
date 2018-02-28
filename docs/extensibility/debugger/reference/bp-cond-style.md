---
title: BP_COND_STYLE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b3d7bd22633985973975cb54d54ab3eb0837e30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Określa styl warunku punktu przerwania dla oczekujące i powiązane punkty przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BP_COND_NONE  
 Po osiągnięciu punktu przerwania pozycji, generowane punktu przerwania. Nie określono warunku punktu przerwania.  
  
 BP_COND_WHEN_TRUE  
 Generowane punkt przerwania, tylko jeśli wyrażenie warunkowe skojarzone z punktu przerwania daje w wyniku `true`.  
  
 BP_COND_WHEN_CHANGED  
 Uruchamiany punkt przerwania tylko wtedy, gdy wartość wyrażenia warunkowego skojarzone z punkt przerwania został zmieniony z jego poprzedniej oceny.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `styleCondition` członkiem [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)