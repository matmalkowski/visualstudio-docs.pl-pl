---
title: "Architektura pakiet VSPackage formantu źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 002dea54b63a78975d56464319614d369a9b2318
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-vspackage-architecture"></a>Architektura pakiet VSPackage kontroli źródła
Pakiet kontroli źródła jest pakiet VSPackage, który korzysta z usług [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia IDE. W zamian pakiet kontroli źródła zawiera jej funkcji jako usługi kontroli źródła. Ponadto pakiet kontroli źródła jest alternatywą bardziej elastyczne niż wtyczka do kontroli źródła do integracji kontroli źródła do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Wtyczka do kontroli źródła z zaimplementowanym interfejsem API dodatku typu Plug-in kontroli źródła przestrzega strict kontraktu. Na przykład wtyczka nie można zastąpić domyślną [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika (UI). Ponadto interfejs API dodatku typu Plug-in kontroli źródła nie obsługuje wtyczki do zaimplementowania własny model kontroli źródła. Pakiet kontroli źródła, jednak pozwala pokonać oba te ograniczenia. Pakiet kontroli źródła ma pełną kontrolę nad środowiskiem kontroli źródła z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownika. Ponadto pakiet kontroli źródła można użyć własnych model kontroli źródła i logiki, a następnie można określić wszystkich interfejsów użytkownika związane z kontroli źródła.  
  
## <a name="source-control-package-components"></a>Składniki pakietu kontroli źródła  
 Jak pokazano na diagramie architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] składnika o nazwie Stub kontroli źródła jest pakiet VSPackage, zintegrowany pakiet kontroli źródła o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Stub kontroli źródła obsługuje następujące zadania.  
  
-   Udostępnia wspólnego interfejsu użytkownika, który jest wymagany w czasie rejestracji pakietu kontroli źródła.  
  
-   Ładuje pakiet kontroli źródła.  
  
-   Ustawia pakietu kontroli źródła jako aktywny/nieaktywny.  
  
 Stub kontroli źródła szuka usługi active pakietu kontroli źródła i kieruje wszystkie przychodzące wywołania usługi z IDE tego pakietu.  
  
 Pakiet karty kontroli źródła jest specjalne kontroli źródła pakietu, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia. Ten pakiet jest głównym składnikiem obsługi źródła formantu dodatków plug-in oparte na interfejsie API dodatku Plug-in kontroli źródła. Gdy wtyczka do kontroli źródła jest aktywny wtyczki, Stub kontroli źródła wysyła jego zdarzenia do pakiet karty kontroli źródła. Z kolei pakiet karty kontroli źródła komunikuje się z wtyczkę kontroli źródła przy użyciu interfejsu API dodatku typu Plug-in kontroli źródła, a także udostępnia domyślny interfejs użytkownika, który jest typowe dla wtyczki sterowania wszystkie źródła.  
  
 Gdy pakiet kontroli źródła jest active pakietu, z drugiej strony, Stub kontroli źródła bezpośrednio komunikuje się z pakietu przy użyciu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfejsy kontroli źródła pakietu. Pakiet kontroli źródła jest odpowiedzialny za hosting własnego interfejsu użytkownika kontroli źródła.  
  
 ![Ilustracja architektury kontroli źródła](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 W przypadku pakietu kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie dostarcza kod kontroli źródła lub interfejsu API dla integracji. Natomiast to do metod opisanych w [tworzenie Plug-in kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md) gdzie wtyczkę kontroli źródła musi implementować sztywne zestaw funkcji i wywołania zwrotne.  
  
 Podobnie jak wszelkie VSPackage pakietu kontroli źródła jest obiekt COM, który można utworzyć przy użyciu `CoCreateInstance`. Pakiet VSPackage udostępnia siebie do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Podczas tworzenia wystąpienia pakiet VSPackage otrzymuje wskaźnik lokacji i <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejs, który udostępnia pakiet VSPackage dostępnych usług i interfejsów w IDE.  
  
 Zapisywanie pakietu kontroli źródła na podstawie pakiet VSPackage wymaga bardziej zaawansowanych doświadczenia programowania niż zapisu oparty na interfejsach API dodatku typu Plug-in kontroli źródła wtyczek.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-vspackages.md)