---
title: IDebugFormatter::GetStringForVarType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e056fa2ef9613c1af776840d1dae61078e26f83
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794323"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
Zwraca ciąg reprezentujący podana wartość VARTYPE.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vt`  
 [in] VARTYPE do reprezentowania jako ciąg.  
  
 `ptdescArrayType`  
 [in] Tablica struktur, która zawiera opis typów.  
  
 `pbstr`  
 [out] Ciąg reprezentujący `vt`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda zwraca ciąg reprezentujący podana wartość VARTYPE.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)