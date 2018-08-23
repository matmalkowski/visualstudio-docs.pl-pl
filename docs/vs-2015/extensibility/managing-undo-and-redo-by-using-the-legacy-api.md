---
title: Zarządzanie Cofnij i wykonaj ponownie za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bb1cc883941c8365e4d4341c93084beaef44d48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682610"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Zarządzanie Cofnij i ponów przy użyciu starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Zarządzanie Cofnij i wykonaj ponownie za pomocą starszej wersji interfejsu API](https://docs.microsoft.com/visualstudio/extensibility/managing-undo-and-redo-by-using-the-legacy-api).  
  
Edytory musi obsługiwać operacje cofania, które pozwalają użytkownikom odwrotnego ich ostatnich zmian, ich modyfikowania kodu. Większość edytorów zaimplementowane mocy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] może mieć Obsługa polecenia Cofnij automatycznie udostępniane przez zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Implementowanie zarządzania cofania](../extensibility/how-to-implement-undo-management.md)  
 Zapewnia możliwości cofania dla edytorów, przy użyciu jednego lub wielu widoków.  
  
 [Porady: wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)  
 W tym artykule opisano, jak wyczyścić stosu cofania.  
  
 [Porady: Użyj przystawki Zarządzanie połączonego cofania](../extensibility/how-to-use-linked-undo-management.md)  
 Łączy w sobie zarządzanie połączonego cofania do edytora.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Umożliwia zarządzanie cofania dla edytora, która obsługuje wiele widoków.  
  
## <a name="related-sections"></a>Sekcje pokrewne

