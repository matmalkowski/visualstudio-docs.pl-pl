---
title: IManagedAddin::Load
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
ms.openlocfilehash: b5f8e94ebcd0aec8e17cac8d651017ed1565d2ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Wywoływane, gdy jest ładowany zarządzanych dodatku VSTO.  
  
## <a name="syntax"></a>Składnia  
  
```c++
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*bstrManifestURL*|Pełna ścieżka manifestu dodatku VSTO.|  
|*pdispApplication*|Wskaźnik do elementu IDispatch reprezentujący aplikacji hosta, który jest ładowany w dodatku VSTO.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Manifestu to plik (zazwyczaj plik XML), który zawiera informacje, które umożliwiają załadowanie dodatku VSTO. Na przykład manifestu, można określić lokalizacji zestawu dodatku VSTO i klasa punktu wejścia, można utworzyć wystąpienia, gdy jest ładowany dodatku VSTO.  
  
 *BstrManifestURL* parametru zawiera wartość `Manifest` wpis w **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<Nazwa aplikacji >_ \Addins\\_\<identyfikator dodatku >_**  klucza rejestru dla dodatku VSTO. Aby uzyskać więcej informacji, zobacz [imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md).  
  
 Implementowanie [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) metody do wykonywania zadań, takich jak Konfigurowanie zasad domeny i zabezpieczeń aplikacji dodatku VSTO, który jest ładowany.  
  
## <a name="see-also"></a>Zobacz także  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  