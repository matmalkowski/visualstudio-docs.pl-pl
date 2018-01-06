---
title: GETNAME_TYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GETNAME_TYPE
helpviewer_keywords: GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb73d39aec7f364ce27ab06ef426d1c4a622878a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getnametype"></a>GETNAME_TYPE
Określa typ nazwy plików do pobrania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 GN_NAME  
 Określa przyjazną nazwę dokumentu lub kontekstu.  
  
 GN_FILENAME  
 Określa pełną ścieżkę dokumentu lub kontekstu.  
  
 GN_BASENAME  
 Określa nazwę pliku podstawowego zamiast pełnej ścieżki dokumentu lub kontekstu.  
  
 GN_MONIKERNAME  
 Określa unikatową nazwę dokumentu lub kontekstu postać krótkiej nazwy.  
  
 GN_URL  
 Określa nazwę adresu URL dokumentu lub kontekstu.  
  
 GN_TITLE  
 Określa tytuł dokumentu, jeśli taka istnieje.  
  
 GN_STARTPAGEURL  
 Pobiera początkowy adres URL strony dla procesów.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane jako parametry [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), i [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metod, aby określić, jakiego rodzaju nazwy, aby znaleźć.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)