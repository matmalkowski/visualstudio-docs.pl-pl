---
title: IManagedAddin::Unload
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: db805aa1e00d672b4a0579e546a6827e9135b909
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676200"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Wywoływana tuż przed zarządzanych dodatku narzędzi VSTO dla programów nie jest załadowany.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT, która wskazuje, czy metoda została ukończona pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest wywoływana przez bieżącej wersji pakietu Microsoft Office. Ta metoda jest zarezerwowana do użytku w przyszłości.  
  
## <a name="see-also"></a>Zobacz także  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  