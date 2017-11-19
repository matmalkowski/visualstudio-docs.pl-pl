---
title: dwTYPE_KIND | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: dwTYPE_KIND
helpviewer_keywords: dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5207bbb9ff81a274d60ffb5957d2b5f31c73dbf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Określa sposób interpretowania typ [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 TYPE_KIND_METADATA  
 [Type_info —](../../../extensibility/debugger/reference/type-info.md) Unii powinny być rozumiane jako [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktury.  
  
 TYPE_KIND_PDB  
 `TYPE_INFO` Unii powinny być rozumiane jako [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktury.  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO` Unii powinny być rozumiane jako [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktury.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są wyświetlane w `dwKind` pole [type_info —](../../../extensibility/debugger/reference/type-info.md) struktury i służą do określenia sposobu interpretowania `type` elementu członkowskiego typu union. `TYPE_INFO` Struktury jest zwracany przez wywołanie do [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO —](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)