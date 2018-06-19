---
title: IDebugDocumentHelper::SetShortName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetShortName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetShortName
ms.assetid: 811a444b-0ea4-4374-9d4c-4f7713bdd1ff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69674b5639c7d59a4551192177d9ebdafd27ac99
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793981"
---
# <a name="idebugdocumenthelpersetshortname"></a>IDebugDocumentHelper::SetShortName
Ustawia krótką nazwę dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetShortName(  
   LPCOLESTR  pszShortName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszShortName`  
 [in] Zerem ciągu zawierającego krótką nazwę dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustawia krótką nazwę nowego dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)