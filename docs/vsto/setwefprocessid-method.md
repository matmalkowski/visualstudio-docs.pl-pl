---
title: SetWefProcessId — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9dbd5a9ffb2ff9b3833dc8007fdfafb4b1a35857
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
  
  