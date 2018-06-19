---
title: Zarządzanie Cofnij i wykonaj ponownie przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 93bb65fa9865c5ca7386925d2c145f2acbc0993a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137514"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie Cofnij i ponów przy użyciu interfejsu API starsza wersja
Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom wycofać swoje ostatnie zmiany ich modyfikowania kodu. Większość edytorów realizowane w ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowane środowisko programistyczne (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Implementowanie zarządzania cofania](../extensibility/how-to-implement-undo-management.md)  
 Zapewnia cofania edytory z jednego lub wielu widoków.  
  
 [Porady: wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)  
 Opisuje sposób wyczyścić stosu cofania.  
  
 [Porady: za pomocą przystawki Zarządzanie połączonego cofania](../extensibility/how-to-use-linked-undo-management.md)  
 Dołącza zarządzania połączonego cofania do edytora.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Umożliwia zarządzanie cofania edytora, która obsługuje wiele widoków.  
  
## <a name="related-sections"></a>Sekcje pokrewne