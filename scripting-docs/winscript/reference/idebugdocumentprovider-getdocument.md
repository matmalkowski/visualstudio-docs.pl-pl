---
title: IDebugDocumentProvider::GetDocument | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentProvider::GetDocument
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dd952a63253dbbf6034e0345547e2bec73b60c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovidergetdocument"></a>IDebugDocumentProvider::GetDocument
Powoduje, że dokument utworzone, jeśli jeszcze nie istnieje.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppssd`  
 [out] Dokument debugowania odpowiadającego dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że dokument utworzone, jeśli jeszcze nie istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)