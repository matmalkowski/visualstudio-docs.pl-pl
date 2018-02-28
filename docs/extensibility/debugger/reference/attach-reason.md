---
title: ATTACH_REASON | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 527e7a445356a46abdd6f2edb0555b7c5c9c7de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="attachreason"></a>ATTACH_REASON
Określa przyczynę aparat debugowania (DE), można dołączyć do węzła programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 ATTACH_REASON_AUTO  
 Dołącz, ponieważ proces jest obecnie w trybie debugowania.  
  
 ATTACH_REASON_LAUNCH  
 Dołączyć, ponieważ proces został uruchomiony.  
  
 ATTACH_REASON_USER  
 Dołącz ze względu na żądanie użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są używane jako parametr [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) i [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)