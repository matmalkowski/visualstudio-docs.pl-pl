---
title: "GetAutoInsertExtensions — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d222f7b6751381ceb4ebdb27bb6a6bf223616df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions — Metoda
  Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.  
  
 Ta metoda jest zarezerwowana do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*psaExtensionNames*|Rozszerzenie nazwy aplikacji dla pakietu Office.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Każda aplikacja dla pakietu Office do wstawienia jest zwracana jako nazwa rozszerzenia aplikacji pakietu Office, co odpowiada wartości w obszarze HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. Host musi odszukać te wartości w rejestrze i automatyczne wstawianie rozszerzeń.  
  
  