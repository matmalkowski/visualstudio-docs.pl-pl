---
title: IDebugModule2::ReloadSymbols_Deprecated | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2::ReloadSymbols
helpviewer_keywords: IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3923431ed4936cf34a077d8d5d818c96e9630221
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
PRZESTARZAŁE. NIE UŻYWAJ. Ponownie ładuje symbole dla tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszUrlToSymbols`  
 [in] Ścieżka do magazynu symboli.  
  
 `pbstrDebugMessage`  
 [out] Zwraca komunikat informacyjny, takich jak stan albo komunikatu o błędzie, który jest wyświetlany po prawej stronie nazwy modułu w oknie moduły.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Aparat debugowania zawsze powinna zwrócić `E_FAIL`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest już obsługiwana. Implementowanie [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) metody zamiast tego.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)