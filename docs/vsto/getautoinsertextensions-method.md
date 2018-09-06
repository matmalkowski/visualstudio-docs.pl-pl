---
title: GetAutoInsertExtensions, metoda
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e3e0fda420682e4f33c0d22a3e9c8caa920895b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677284"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions, metoda
  Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.  
  
 Ta metoda jest zarezerwowana do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*psaExtensionNames*|Rozszerzenie nazwy aplikacji dla pakietu Office.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Każda aplikacja dla pakietu Office ma zostać wstawiony jest zwracany jako nazwa rozszerzenia aplikacji pakietu Office, który odpowiada wartości w obszarze **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Host musi wyszukiwać te wartości w rejestrze i automatyczne wstawianie rozszerzenia.  
  
  