---
title: IVariantChangeType::ChangeType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Przyjmuje wartość typu variant i tworzy nowy wariant z określonym typem.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarDst`  
 [w, out] Typ variant zawierający reprezentowany przez wartość `pvarSrc`, ale z typem określonym przez `vtNew`.  
  
 `pvarSrc`  
 [in] Wartość wariantu, aby zmienić do nowego typu.  
  
 `lcid`  
 [in] Kontekst ustawień regionalnych do użycia podczas konwertowania argumenty do lub z ciągów.  
  
 `vtNew`  
 [in] Określa typ `pvarDst` stanie się.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `pvarDst` i `pvarSrc` argumentów może być takie same, w którym to przypadku jest zastępowany oryginalną wartość. Ta metoda przekazuje `pvarDst` do `VariantClear` funkcji, a w konsekwencji `pvarDst` powinien być inicjowany na prawidłową wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)