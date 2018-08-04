---
title: Polecenie kontraktów w zestawach międzyoperacyjnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2ac80125111ebfe3d8a7e5dc89d1f2597f8d3a4
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510858"
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty poleceń w zestawach międzyoperacyjnych
Podstawowy kontrakt dla obsługi poleceń w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs jest, że środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, które określają, czy polecenie jest obsługiwane, a jeśli jest obsługiwana, aby ustalić ich stan i tekst. Następnie wywołuje środowisko <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wykonać polecenie.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Metoda odbywa się tak samo dla wszystkich poleceń. Dalszej komunikacji, jeśli jest to wymagane (na przykład, z listy rozwijanej) odbywa się przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody za pomocą odpowiednich parametrów. Interpretacja tych parametrów, zależy od określone polecenie.  
  
 Jeśli element docelowy polecenia zwraca wartości w parametrze danych wyjściowych, obiekt wywołujący zawsze jest odpowiedzialny za zwolnić wszystkie zasoby, które zostały przydzielone. Ponieważ ten parametr jest typu variant, czyszcząc wariant zwalnia zasoby.  
  
 W przypadkach, gdzie polecenia musi działać w oknie hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejs musi być używany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejs ma podobny kontrakt, z podobnych metod: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Zobacz także  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementacja poleceń](../../extensibility/internals/command-implementation.md)