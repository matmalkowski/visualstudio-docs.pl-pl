---
title: CODE_PATH | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CODE_PATH
helpviewer_keywords: CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aad85bd41537073a54b319b2830ea621fd4bece4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="codepath"></a>CODE_PATH
Opisuje wywołanie metody lub funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
 bstrName  
 Nazwa ścieżki kodu.  
  
 pCode  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiektu, który identyfikuje w kodzie Aby wkraczać do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest używany do zaimplementowania Wkraczanie do funkcji. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) zwraca wszystkie wywołania z bieżącej lokalizacji w programie debugowany. Ta struktura reprezentuje jednego takiego wywołania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)