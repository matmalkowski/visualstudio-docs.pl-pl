---
title: DEBUG_ADDRESS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07312208967aeccfbd81f44587f84a43dfebf4c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101449"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Ta struktura reprezentuje adres.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Warunki  
 ulAppDomainID  
 Identyfikator procesu.  
  
 guidModule  
 Identyfikator GUID moduł, który zawiera ten adres.  
  
 tokClass  
 Token identyfikujący klasę lub typ ten adres.  
  
> [!NOTE]
>  Ta wartość jest specyficzne dla dostawcy symboli i dlatego nie ma znaczenia innych niż ogólne jako identyfikator dla typu klasy.  
  
 ADR  
 A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, która zawiera Unię struktur, które opisują typy pojedynczy adres. Wartość `addr`.`dwKind` pochodzi z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) wyliczenia, w którym wyjaśniono, jak interpretować Unii.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywana do [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodę, aby wypełnić.  
  
 **Ostrzeżenie [tylko C++]**  
  
 Jeśli `addr.dwKind` jest `ADDRESS_KIND_METADATA_LOCAL` i jeśli `addr.addr.addrLocal.pLocal` nie jest wartością null, należy wywołać `Release` na wskaźniku tokenu:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)