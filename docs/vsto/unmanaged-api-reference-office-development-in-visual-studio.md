---
title: Niezarządzany wykaz interfejsów API (Office development w programie Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b0f48ea5997c2c8c2dd7d90eebde8322fad8a7a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676348"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Niezarządzany wykaz interfejsów API (Office development w programie Visual Studio)
  Począwszy od systemu Microsoft Office 2007, aplikacji pakietu Office korzysta [imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md) interfejs do wywołania w dodatku narzędzi VSTO programu ładującego składnik, który jest dołączony do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ten składnik ułatwiają zarządzane ładowania dodatków narzędzi VSTO. Możesz utworzyć własne składnika dodatku narzędzi VSTO dla programów modułu ładującego poprzez implementację tego interfejsu.  
  
> [!NOTE]  
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md)  
 To interfejs modelu COM, który można zaimplementować, aby załadować i rozładować zarządzanych dodatków narzędzi VSTO dla programów w aplikacjach pakietu Office.  
  
  