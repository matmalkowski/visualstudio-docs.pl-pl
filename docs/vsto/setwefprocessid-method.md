---
title: "SetWefProcessId — metoda | Dokumentacja firmy Microsoft"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dd4abab178c951c6150653a1228c2077c5585808
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="setwefprocessid-method"></a>SetWefProcessId — Metoda
  Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*dwProcessId*|Identyfikator procesu, który będzie służyć do uruchamiania WEF zawartości.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda musi zostać wywołana po utworzeniu procesu zawartości WEF, ale przed uruchomieniem żadnej zawartości WEF.  
  
 Jeśli chcesz dołączyć do procesu zawartości WEF przez środowisko deweloperskie, środowisko musi wykonać tej operacji w implementacji tej metody.  
  
  