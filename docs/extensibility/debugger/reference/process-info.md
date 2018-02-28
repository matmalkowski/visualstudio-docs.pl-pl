---
title: PROCESS_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5628e3cca48799b602917fa1504479b46ee02dd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="processinfo"></a>PROCESS_INFO
Zawiera informacje dotyczące procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Pola  
 Kombinacja flag z [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) wyliczenie Określ pola, które są wypełnione.  
  
 bstrFileName  
 Pełna nazwa ścieżki procesu. Odpowiednikiem wywołania [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metody z parametrem `GN_FILENAME`.  
  
 bstrBaseName  
 Nazwa pliku i rozszerzenie procesu. Odpowiednikiem wywołania `IDebugProcess2::Getname` metody z parametrem `GN_BASENAME`.  
  
 bstrTitle  
 Tytuł ten proces, jeśli taka istnieje. Odpowiednikiem wywołania `IDebugProcess2::Getname` metody z parametrem `GN_TITLE`.  
  
 Identyfikator procesu  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) strukturę, która identyfikuje proces. Odpowiednikiem wywołania [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) metody.  
  
 dwSessionId  
 Identyfikator ten proces jest uruchomiony w sesji debugowania.  
  
 bstrAttachedSessionName  
 Nazwa sesji dołączone. Odpowiednikiem wywołania [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) metody.  
  
 CreationTime  
 Czas utworzenia procesu.  
  
 Flagi  
 Kombinacja flag z [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) wyliczenia, która określa właściwości procesu.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywana do [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metody, gdzie jest wypełnione.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)