---
title: METADATA_ADDRESS_LOCAL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_LOCAL
helpviewer_keywords: METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74d59fb19d130ad53ddbf200e96cdf04e958e239
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
Ta struktura reprezentuje adresu lokalnej zmiennej w zakresie (zazwyczaj funkcji lub metody).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Warunki  
 tokMethod  
 Identyfikator metody lub funkcji zmiennej lokalnej jest częścią.  
  
 [C++] `_mdToken` jest `typedef` dla 32-bitowej `int`.  
  
 pLocal  
 Token, której adres reprezentuje tej struktury.  
  
 dwIndex  
 Może być indeks tej zmiennej lokalnej w metodzie lub funkcji lub wartość (specyficzne dla języka).  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, kiedy `dwKind` pole `DEBUG_ADDRESS_UNION` ustawiono struktury `ADDRESS_KIND_LOCAL` (wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Wyliczenie).  
  
 `Warning:`[Tylko C++]  Jeśli `pLocal` nie jest pusta, należy wywołać `Release` token wskaźnika (`addr` jest polem w [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)