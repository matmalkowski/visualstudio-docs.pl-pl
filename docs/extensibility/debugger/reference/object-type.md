---
title: OBJECT_TYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OBJECT_TYPE
helpviewer_keywords: OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223833857568da64e24aa2e955ecabce0b36af57
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="objecttype"></a>OBJECT_TYPE
Określa typ obiektu z ewaluatora wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 OBJECT_TYPE_BOOLEAN  
 Wskazuje, że obiekt jest wartością logiczną.  
  
 OBJECT_TYPE_CHAR  
 Wskazuje, że obiekt jest znak.  
  
 OBJECT_TYPE_I1  
 Wskazuje, że obiekt jest całkowita jednobajtowe.  
  
 OBJECT_TYPE_U1  
 Wskazuje, że obiekt jest jednobajtowych liczbę całkowitą bez znaku.  
  
 OBJECT_TYPE_I2  
 Wskazuje, czy obiekt jest całkowita dwubajtowych.  
  
 OBJECT_TYPE_U2  
 Wskazuje, że obiekt jest liczba całkowita bez znaku dwubajtowego.  
  
 OBJECT_TYPE_I4  
 Wskazuje, że obiekt jest całkowita 4 bajtowych.  
  
 OBJECT_TYPE_U4  
 Wskazuje, czy obiekt jest 4 bajtowych liczbę całkowitą bez znaku.  
  
 OBJECT_TYPE_I8  
 Wskazuje, czy obiekt jest 8 bajtowych liczbę całkowitą ze znakiem.  
  
 OBJECT_TYPE_U8  
 Wskazuje, że obiekt jest liczbą całkowitą bez znaku ośmiu bajtów.  
  
 OBJECT_TYPE_R4  
 Wskazuje, że obiekt jest 4 bajtowa liczba zmiennoprzecinkowa.  
  
 OBJECT_TYPE_R8  
 Wskazuje, że obiekt jest 8 bajtowa liczba zmiennoprzecinkowa.  
  
 OBJECT_TYPE_OBJECT  
 Wskazuje, że obiekt jest obiektem.  
  
 OBJECT_TYPE_NULL  
 Wskazuje, że obiekt ma wartość NULL.  
  
 OBJECT_TYPE_CLASS  
 Wskazuje, że obiekt jest klasą.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) i [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)