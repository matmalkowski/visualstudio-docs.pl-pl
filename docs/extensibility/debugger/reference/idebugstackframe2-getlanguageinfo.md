---
title: IDebugStackFrame2::GetLanguageInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 12e27e744d13ce24f90a4c97ea242cecf8a843d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
Pobiera język skojarzony z tą ramką stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLanguageInfo (   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo (   
   ref string pbstrLanguage,  
   ref Guid   pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLanguage`  
 [out] Zwraca nazwę języka, który implementuje metodę skojarzoną z tą ramką stosu.  
  
 `pguidLanguage`  
 [out] Zwraca `GUID` języka. Aby uzyskać [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] języków, na przykład następujące może być zwracany:  
  
-   `guidVBScriptLang`  
  
-   `guidJScriptLang`  
  
-   `guidCPPLang`  
  
-   `guidVBLang`  
  
-   `guidSQLLang`  
  
-   `guidScriptLang`  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)