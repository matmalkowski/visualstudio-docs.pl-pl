---
title: IManagedAddin::Load | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: 
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 91a2909d407dbdc7629e189585333a3e4702483d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  