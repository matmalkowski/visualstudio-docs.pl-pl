---
title: Zarządzanie Cofnij i wykonaj ponownie za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be60b3f0dd45a40663770b4b0debe8023e277f32
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638075"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API
Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom odwrotnego ich ostatnich zmian, ich modyfikowania kodu. Większość edytorów zaimplementowane mocy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Implementowanie cofania zarządzania](../extensibility/how-to-implement-undo-management.md)  
 Zapewnia możliwości cofania dla edytorów, przy użyciu jednego lub wielu widoków.  
  
 [Porady: wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)  
 W tym artykule opisano, jak wyczyścić stosu cofania.  
  
 [Porady: użycie połączonego cofania zarządzania](../extensibility/how-to-use-linked-undo-management.md)  
 Łączy w sobie zarządzanie połączonego cofania do edytora.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Umożliwia zarządzanie cofania dla edytora, która obsługuje wiele widoków.  
