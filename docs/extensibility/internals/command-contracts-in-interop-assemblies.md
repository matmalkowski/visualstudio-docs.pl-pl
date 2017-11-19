---
title: "Polecenie kontrakty w zestawy międzyoperacyjne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 901423bfa9b43e2d4eaaa20a225c35e76a0b8790
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty polecenia w zestawy międzyoperacyjne
Podstawowy kontrakt obsługi poleceń za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs jest środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, aby określić, czy polecenie jest obsługiwana i, jeśli jest obsługiwana, aby określić jego stanu i tekst. Następnie wywołania środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę można wykonać polecenia.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Metody odbywa się tak samo dla wszystkich poleceń. Dalszą komunikację, w razie potrzeby (na przykład z listy rozwijanej) jest zarządzany przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody z odpowiednimi parametrami. Określone polecenie zależy od interpretacji tych parametrów.  
  
 Jeśli element docelowy polecenia zwraca wartości w parametr wyjściowy, wywołujący zawsze jest odpowiedzialny za zwalnianie wszystkie zasoby, które zostały przydzielone. Ponieważ ten parametr ma typ variant, czyszcząc wariant zwalnia zasoby.  
  
 W przypadkach, gdy polecenia musi działać w ramach okna hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejs musi być używany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejs ma podobny kontrakt za pomocą metod podobne: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing poleceń w VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementacja](../../extensibility/internals/command-implementation.md)