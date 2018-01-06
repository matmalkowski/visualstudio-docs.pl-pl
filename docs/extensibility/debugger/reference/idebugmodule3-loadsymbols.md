---
title: IDebugModule3::LoadSymbols | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::LoadSymbols
helpviewer_keywords: IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1b3dda16ac3312e7deec21b06a4df05162bfa692
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Ładuje symbole dla bieżącego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca `S_OK`. W przypadku niepowodzenia zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ładuje symbole z bieżącej ścieżki wyszukiwania (może się zmienić wywołując [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) metody).  
  
 Ta metoda jest preferowana przez [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)