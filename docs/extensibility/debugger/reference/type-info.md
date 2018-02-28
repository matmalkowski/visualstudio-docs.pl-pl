---
title: "TYPE_INFO — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d6888d2680cffbde132885d730cd35f6e509c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="typeinfo"></a>TYPE_INFO —
Ta struktura określa różne rodzaje informacji na temat typu pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 dwKind  
 Wartość z zakresu od [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) wyliczenie określające sposób interpretowania Unii.  
  
 type.typeMeta  
 [Tylko C++] Zawiera [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [Tylko C++] Zawiera [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [Tylko C++] Zawiera [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktury, jeśli `dwKind` jest `TYPE_KIND_BUILT`.  
  
 type.unused  
 Dopełnienie nieużywane.  
  
 — typ  
 Nazwa typu union.  
  
 unionmember  
 [C# tylko] Kierowanie na typ struktury odpowiednie na podstawie `dwKind`.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywana do [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metody, gdzie jest wypełnione. Zależy sposób interpretowania zawartość struktury `dwKind` pola.  
  
> [!NOTE]
>  [Tylko C++] Jeśli `dwKind` jest równe `TYPE_KIND_BUILT`, wówczas jest konieczny zwolnić odpowiadającego [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu podczas niszczenia `TYPE_INFO` struktury. Jest to realizowane przez wywołanie `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [C# tylko] W poniższej tabeli przedstawiono sposób interpretowania `unionmember` elementu członkowskiego dla każdego rodzaju. W przykładzie pokazano, jak to zrobić dla jednego rodzaju.  
  
|`dwKind`|`unionmember`interpretowane jako|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak interpretować `unionmember` członkiem `TYPE_INFO` struktury w języku C#. W tym przykładzie pokazano tylko jeden typ interpretacji (`TYPE_KIND_METADATA`), ale pozostałe będą interpretowane w taki sam sposób.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)