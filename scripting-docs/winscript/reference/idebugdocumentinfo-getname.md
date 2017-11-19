---
title: IDebugDocumentInfo::GetName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Zwraca nazwę określonego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dnt`  
 [in] Typ nazwy dokumentu do zwrócenia.  
  
 `pbstrName`  
 [out] Ciąg zawierający nazwę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Określona nazwa dokumentu nie jest znany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca nazwę określonego dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Wyliczenie DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)