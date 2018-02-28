---
title: THREADPROPERTY_FIELDS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9ff443fc655c18600ff90536d6e7ee5b8aa1ab7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Określa, jakie informacje o wątku ma być pobrana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 TPF_ID  
 Inicjowanie użycia `dwThreadId` pole [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury.  
  
 TPF_SUSPENDCOUNT  
 Inicjowanie użycia `dwSuspendCount` pole `THREADPROPERTIE`Struktura.  
  
 TPF_STATE  
 Inicjowanie użycia `dwThreadState` pole `THREADPROPERTIE`Struktura.  
  
 TPF_PRIORITY  
 Inicjowanie użycia `bstrPriority` pole `THREADPROPERTIE`Struktura.  
  
 TPF_NAME  
 Inicjowanie użycia `bstrName` pole `THREADPROPERTIE`Struktura.  
  
 TPF_LOCATION  
 Inicjowanie użycia `bstrLocation` pole `THREADPROPERTIE`Struktura.  
  
 TPF_ALLFIELDS  
 Określa wszystkie pola.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane jako argument [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody, aby wskazać, które pola [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury mają być zainicjowany.  
  
 Te wartości są również używane w `dwFields` członkiem `THREADPROPERTIES` struktury, aby wskazać pola, które są używane i prawidłowe.  
  
 Te flagi mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)