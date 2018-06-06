---
title: SetWefProcessId — metoda
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
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693435"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId — metoda
  Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
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
  
  