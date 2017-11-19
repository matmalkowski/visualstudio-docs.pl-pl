---
title: METADATA_ADDRESS_RETVAL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_RETVAL
helpviewer_keywords: METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51db1e429e363a653ddde4948f7519e547f99a19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Ta struktura reprezentuje wartość zwracaną z metody lub funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>Warunki  
 tokMethod  
 Identyfikator metody dotyczy tej wartości zwracanej.  
  
 dwCorType  
 Podstawowy typ zwracanej wartości. Jest to wartość z zakresu od `CorElementType` wyliczenia zdefiniowanych w [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] pliku corhdr.h zestawu SDK.  
  
 dwSigSize  
 Rozmiar podpisu zwracanej wartości (przechowywanej w `rgSig`).  
  
 rgSig  
 Tablica bajtów tworzące podpisu zwracanej wartości.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest częścią Unii w [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struktury, kiedy `dwKind` pole `DEBUG_ADDRESS_UNION` ustawiono struktury `ADDRESS_KIND_RETVAL` (wartość z zakresu od [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Wyliczenie).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)