---
title: IManagedAddin::Unload | Dokumentacja firmy Microsoft
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
helpviewer_keywords: Unload method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: aadf5235eb64c14b14f7241b4fd2b89b0a9887da
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Wywoływana tuż przed zarządzanych dodatku VSTO nie jest załadowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest wywoływana przy użyciu bieżącej wersji pakietu Microsoft Office. Ta metoda jest zarezerwowana do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz też  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  