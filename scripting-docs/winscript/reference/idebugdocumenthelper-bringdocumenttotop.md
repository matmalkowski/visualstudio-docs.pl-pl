---
title: IDebugDocumentHelper::BringDocumentToTop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.BringDocumentToTop
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::BringDocumentToTop
ms.assetid: 91bdbb05-6f79-4b07-a707-838cb75a770f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34da5d19b927bf80c05675cbc6871b0a26801247
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperbringdocumenttotop"></a>IDebugDocumentHelper::BringDocumentToTop
Powoduje przeniesienie tego dokumentu do góry w debugerze interfejsu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BringDocumentToTop();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda uruchomienie debugera, jeśli nie jest już uruchomiona.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)