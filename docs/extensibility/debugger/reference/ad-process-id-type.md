---
title: AD_PROCESS_ID_TYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AD_PROCESS_ID_TYPE
helpviewer_keywords: AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75904ef6e06ef7ccd6d126091f8ec0fbe523ac9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Określa sposób interpretowania procesu o identyfikatorze w [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 AD_PROCESS_ID_SYSTEM  
 Identyfikator procesu jest identyfikatora systemowego. Użyj `ProcessId.dwProcessId` pole [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.  
  
 AD_PROCESS_ID_GUID  
 Identyfikator procesu jest identyfikatorem GUID. Użyj `ProcessId.guidProcessId` pole `AD_PROCESS_ID` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `ProcessIdType` członkiem [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury w celu określenia typu Identyfikator procesu, który jest zawarty w strukturze. Określa, jak interpretować `ProcessId` Unii w strukturze.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)