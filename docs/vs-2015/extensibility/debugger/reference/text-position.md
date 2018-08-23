---
title: TEXT_POSITION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TEXT_POSITION
helpviewer_keywords:
- TEXT_POSITION structure
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d8d4a46a8aea165770c88b9479d5d19ed14def4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676846"
---
# <a name="textposition"></a>TEXT_POSITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [TEXT_POSITION](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/text-position).  
  
Określa lokalizację wierszy i kolumn w podanym tekście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct _tagTEXT_POSITION {   
   DWORD dwLine;  
   DWORD dwColumn;  
} TEXT_POSITION;  
```  
  
```csharp  
public struct TEXT_POSITION {   
   public uint dwLine;  
   public uint dwColumn;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwLine  
 Indeks wiersza w pliku źródłowym.  
  
 dwColumn  
 Przesunięcie znaku w wierszu.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest używany w [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) i [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury.  
  
 Ta struktura jest wypełniane przez wywołanie do następujących metod:  
  
-   [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)  
  
-   [Getsourcerange —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)  
  
-   [Getrange —](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)  
  
-   [Getoffset —](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)  
  
 Ta struktura jest przekazywany jako parametr do następujących metod:  
  
-   [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)  
  
-   [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)  
  
-   [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)  
  
-   [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)  
  
-   [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [Getsourcerange —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [Getrange —](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)   
 [Getoffset —](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)   
 [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

