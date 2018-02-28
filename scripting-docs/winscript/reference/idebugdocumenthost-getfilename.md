---
title: IDebugDocumentHost::GetFileName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.GetFileName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909c431a389a2589d48b6228534b16675ea41383
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Zwraca nazwę dokumentu bez informacji o ścieżce.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrShortName`  
 [out] Ciąg zawierający krótką nazwę dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca krótką nazwę dokumentu bez informacji o ścieżce. Krótka nazwa jest zwykle używany w sytuacjach, takich jak **Zapisz jako...**  okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)