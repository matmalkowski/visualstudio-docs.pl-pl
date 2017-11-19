---
title: "Zarządzanie Cofnij i wykonaj ponownie przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41672845d318707512472f556753f429661d008c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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