---
title: IDebugArrayField::GetRank | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2467c8d4ed85a685de80511d68a20e24c047306e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Pobiera pozycję lub liczbę wymiarów tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwRank`  
 [out] Zwraca rangę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ranga tablicy odpowiada liczbę wymiarów. W języku C++ i C# tablic wielowymiarowych są naprawdę tablic zawierających tablice i dlatego jest uznawana za Jednowymiarowa tablica (i `GetRank` metoda zawsze zwraca wartość 1). W [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], z drugiej strony, tablic wielowymiarowych są obsługiwane w inny sposób i rangę tablicy takie odzwierciedla liczbę wymiarów (i `GetRank` metoda zawsze zwraca liczbę wymiarów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)