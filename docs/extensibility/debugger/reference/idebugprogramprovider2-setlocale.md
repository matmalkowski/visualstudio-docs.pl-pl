---
title: IDebugProgramProvider2::SetLocale | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fa3bbadd4266466d18fbd24cee83ec916aa571ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2setlocale"></a>IDebugProgramProvider2::SetLocale
Określa ustawienia regionalne do użycia dla wszystkich zasobów specyficznych dla ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetLocale(  
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wLangID`  
 [in] Identyfikator języka Aby ustanowić. Na przykład 1033 dla języka angielskiego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)