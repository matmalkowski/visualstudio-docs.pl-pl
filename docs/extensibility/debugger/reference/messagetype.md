---
title: MESSAGETYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4c507575442d188e7a273559689cc782f00d51c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="messagetype"></a>MESSAGETYPE
Określa typ wiadomości i przyczyny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MT_OUTPUTSTRING  
 Wskazuje, czy można wysłać komunikatu, w oknie danych wyjściowych. Jest to wykluczają się wzajemnie z `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Wskazuje, że komunikat powinien być wyświetlany w oknie komunikatu. Jest to wykluczają się wzajemnie z `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Wartość maski do izolowania miejsce docelowe dla wiadomości.  
  
 MT_REASON_EXCEPTION  
 Wskazuje, czy okno komunikatu jest pokazywane w wyniku wystąpienia wyjątku. Jest to wykluczają się wzajemnie z `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Wskazuje, że jest wyświetlane okno komunikatu wyniku naciśnięcie śledzenia. Jest to wzajemnie wykluczające się `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Wartość maski do izolowania Przyczyna komunikat jest wyświetlany.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są zwracane z [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) i [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metody.  
  
 Jedna z wartości Przyczyna można łączyć z jedną z wartości docelowe danych wyjściowych za pomocą bitowej `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)