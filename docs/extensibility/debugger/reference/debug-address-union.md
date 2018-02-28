---
title: DEBUG_ADDRESS_UNION | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fc4e5c4bf075c69f4549e34185d407ba9fb95cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
W tym artykule opisano różne rodzaje adresów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>Warunki  
 dwKind  
 Wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, określając sposób interpretowania Unii.  
  
 addr.addrNative  
 [Tylko C++] Zawiera [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) struktury, jeśli `dwKind` = ADDRESS_KIND_NATIVE.  
  
 addr.addrThisRel  
 [Tylko C++] Zawiera[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) struktury, jeśli `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.  
  
 addr.addUPhysical  
 [Tylko C++] Zawiera[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) struktury, jeśli `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.  
  
 addr.addrMethod  
 [Tylko C++] Zawiera[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) struktury, jeśli `dwKind` = ADDRESS_KIND_METHOD.  
  
 addr.addrField  
 [Tylko C++] Zawiera[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) struktury, jeśli `dwKind` = ADDRESS_KIND_FIELD.  
  
 addr.addrLocal  
 [Tylko C++] Zawiera[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) struktury, jeśli `dwKind` = ADDRESS_KIND_LOCAL.  
  
 addr.addrParam  
 [Tylko C++] Zawiera[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) struktury, jeśli `dwKind` = ADDRESS_KIND_PARAM.  
  
 addr.addrArrayElem  
 [Tylko C++] Zawiera[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) struktury, jeśli `dwKind` = ADDRESS_KIND_ARRAYELEM.  
  
 addr.addrRetVal  
 [Tylko C++] Zawiera[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) struktury, jeśli `dwKind` = ADDRESS_KIND_RETVAL.  
  
 addr.unused  
 Dopełnienie [C++ tylko].  
  
 ADR  
 [Tylko C++] Nazwa typu union.  
  
 unionmember  
 [C# tylko] Ta wartość musi być przekazywane do typu odpowiednie struktury na podstawie `dwKind`. Zobacz uwagi dla skojarzenia między `dwKind` i interpretacji Unii.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury i jedna z wielu różnych rodzajów adresów ( `DEBUG_ADDRESS` struktury jest wypełniane przez wywołanie do [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metody).  
  
 [C# tylko] W poniższej tabeli przedstawiono sposób interpretowania `unionmember` elementu członkowskiego dla każdego rodzaju adres. W przykładzie pokazano, jak to zrobić dla jednego rodzaju adres.  
  
|`dwKind`|`unionmember`interpretowane jako|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak interpretować jednego rodzaju adresu (`METADATA_ADDRESS_ARRAYELEM`) z `DEBUG_ADDRESS_UNION` struktury w języku C#. Wszystkie pozostałe elementy mogą być interpretowane w taki sam sposób.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)