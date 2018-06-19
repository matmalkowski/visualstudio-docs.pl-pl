---
title: IDebugDocumentInfo::GetDocumentClassId | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be3d29cf19752da18b76f31b4d12cecb05592c00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794224"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Zwraca `CLSID` określający typ dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pclsidDocument`  
 [out] A `CLSID` określający typ dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia debugera IDE użytkownikom niestandardowych hosta dla tego dokumentu.  
  
 Jeśli dokument nie jest możliwa do wyświetlenia danych, zwracana wartość `pclsidDocument` jest `CLSID_NULL`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)