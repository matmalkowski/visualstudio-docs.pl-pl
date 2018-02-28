---
title: IDebugDocumentHost::OnCreateDocumentContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Powiadamia hosta, że nowy kontekst dokumentu jest tworzony i umożliwia hostowi opcjonalnie zwracać kontrolowanie nieznany w nowym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkOuter`  
 [out] Obiekt, który określa nowy kontekst.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie udostępnia kontrolowanie obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia dodawanie nowych funkcji do dokumentów dostarczonych przez pomocnika kontekstów hosta. Ta metoda może zwracać **E_NOTIMPL** lub obiektu zewnętrznego wartości null, w którego przypadku wywołujący jest odpowiedzialny za tworzenia kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)