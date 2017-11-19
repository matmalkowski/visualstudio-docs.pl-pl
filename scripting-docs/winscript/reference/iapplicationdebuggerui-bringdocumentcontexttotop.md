---
title: IApplicationDebuggerUI::BringDocumentContextToTop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fab017ab286957cf2c4be35832b1db877b339bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Wywołuje okno zawierające kontekst danego dokumentu do góry w interfejsie użytkownika debugera i przewijania okna w kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddc`  
 [in] Kontekstu dokumentu, aby przełączyć do góry w interfejsie użytkownika debugera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Określony przez kontekst `pddc` nie jest znany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyświetlenie okna zawierającego kontekst danego dokumentu do góry w interfejsie użytkownika debugera i przewijania okna w kontekście.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)