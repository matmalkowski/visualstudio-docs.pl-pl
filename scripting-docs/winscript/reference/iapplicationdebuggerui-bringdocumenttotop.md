---
title: IApplicationDebuggerUI::BringDocumentToTop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57b76f44eeeaad1946d40435c770b0687b82fd17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Udostępnia interfejs użytkownika okna zawierającego dokument określony debugowania do góry w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddt`  
 [in] Debugowanie dokument, aby przełączyć do góry w interfejsie użytkownika debugera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Dokument nie jest znany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyświetlenie okna zawierającego debugowania określony dokument do góry w debugerze interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)