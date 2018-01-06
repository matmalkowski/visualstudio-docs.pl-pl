---
title: IDebugCodeContext2::GetLanguageInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords: IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6bb29ddf1ebbaafffc316562604d3e7b6cba8ff5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Pobiera informacje o języku dla tego kontekstu kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLanguage`  
 [w, out] Zwraca ciąg zawierający nazwę języka, takie jak "C++."  
  
 `pguidLanguage`  
 [w, out] Zwraca identyfikator GUID dla języka kontekst kodu, na przykład `guidCPPLang`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Co najmniej jeden z parametrów musi zwracać wartość inną niż null.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)