---
title: Poleceń i menu, które używają zestawów międzyoperacyjnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c48ee7eb25fa95789076454c849485f4ac1dc384
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135010"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Poleceń i menu, które używają zestawów międzyoperacyjnych
Pakiet VSPackage, który implementuje poleceń menu i paska narzędzi przy użyciu zestawy międzyoperacyjne muszą:  
  
-   Powiadamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) o poleceniach obsługuje oraz czy są obecnie włączone.  
  
-   Zgodne z regułami (Umowa) do obsługi poleceń.  
  
-   Jawne Implementowanie obsługi polecenia przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu.  
  
 Poniżej opisano sposób wykonywania tych zadań.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Określanie stanu polecenia przy użyciu zestawów międzyoperacyjnych](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 W tym artykule opisano, jak pakiet VSPackage powiadamia IDE dotyczących poleceń, które obsługuje i czy są obecnie włączone.  
  
 [Kontrakty poleceń w zestawach międzyoperacyjnych](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Zawiera definicję kontraktu podstawowe polecenia używane przez wszystkie VSPackages wykonania polecenia przy użyciu zestawy międzyoperacyjne  
  
 [Implementacja](../../extensibility/internals/command-implementation.md)  
 Zawiera omówienie sposobu pakiet VSPackage wykonuje polecenie.  
  
 [Rejestrowanie programów obsługi zestawu międzyoperacyjnego](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Opisuje wpisy rejestru wymagane do powiadamiania IDE, że pakiet VSPackage zapewnia programem obsługi.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dostępność](../../extensibility/internals/command-availability.md)  
 Zawiera opis kryteriów, które są używane IDE do ustalenia, jakie polecenia pakiet VSPackage są dostępne i jak obiekt obsługuje je.  
  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Zawiera szczegółowe informacje o sposobie tworzenia interfejsu użytkownika, który używa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia pomocy technicznej.  
  
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Omówienie procesu używany do tworzenia powiązań obiektu z żądaniem poprawne polecenie.