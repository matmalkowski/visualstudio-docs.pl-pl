---
title: IManagedAddin::Load | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 545560c5f02437925c2f93e9c6dc3113e1cddd0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wywoływane, gdy jest ładowany zarządzanych dodatku VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*bstrManifestURL*|Pełna ścieżka manifestu dodatku VSTO.|  
|*pdispApplication*|Wskaźnik do elementu IDispatch reprezentujący aplikacji hosta, który jest ładowany w dodatku VSTO.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Manifestu to plik (zazwyczaj plik XML), który zawiera informacje, które umożliwiają załadowanie dodatku VSTO. Na przykład manifestu, można określić lokalizacji zestawu dodatku VSTO i klasa punktu wejścia, można utworzyć wystąpienia, gdy jest ładowany dodatku VSTO.  
  
 *BstrManifestURL* parametru zawiera wartość `Manifest` objęcie HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<Nazwa aplikacji >*\Addins\\*\<identyfikator dodatku >* klucza rejestru dla dodatku VSTO. Aby uzyskać więcej informacji, zobacz [imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md).  
  
 Implementowanie [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) metody do wykonywania zadań, takich jak Konfigurowanie zasad domeny i zabezpieczeń aplikacji dodatku VSTO, który jest ładowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  