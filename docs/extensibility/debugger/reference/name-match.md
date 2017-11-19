---
title: NAME_MATCH | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NAME_MATCH
helpviewer_keywords: NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce68a98df224ddf3195dda2501210a54920ebb69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="namematch"></a>NAME_MATCH
Wybiera opcję case do dopasowania nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
} NAME_MATCH;  
```  
  
```csharp  
public enum NameMatchOptions {   
   nmNone            = 0,  
   nmCaseSensitive   = 1,  
   nmCaseInsensitive = 2  
}  
```  
  
## <a name="members"></a>Elementy członkowskie  
 nmNone  
 Nie określono opcji.  
  
 nmCaseSensitive  
 Wskazuje, że w nazwach można dopasować jest rozróżniana wielkość liter.  
  
 nmCaseInsensitive  
 Wskazuje nazwy można dopasować nie jest rozróżniana.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument do następujących metod:  
  
-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)  
  
-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)  
  
-   [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)  
  
-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)   
 [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)