---
title: ASSEMBLYLOCRESOLUTION | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ASSEMBLYLOCRESOLUTION
helpviewer_keywords: ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7227b91a045c36624a1210224383c75b69f4c6db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Określa, w którym znajduje się zestaw.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```csharp  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 ALR_NAME  
 Zestaw znajduje się w bieżącej przestrzeni nazw.  
  
 ALR_USERDIR  
 Zestaw znajduje się w katalogu użytkownika.  
  
 ALR_SHAREDDIR  
 Zestaw znajduje się w katalogu udostępnionym.  
  
 ALR_REMOTEDIR  
 Zestaw znajduje się w katalogu zdalnym.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są zwracane przez [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) i [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) metody.  
  
 Wartości te można łączyć z `OR` operacji.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)