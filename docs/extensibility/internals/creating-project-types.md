---
title: "Tworzenie typów projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7c0bba9b80e4e874f222ce00834f44a2d93e3e7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-types"></a>Tworzenie typów projektów
Można rozszerzyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez utworzenie nowego typu projektu. Aby utworzyć nowy typ projektu, należy poznać kilka koncepcji i wykonać kilka kroków. Poniższe tematy zawierają omówienie sposobu tworzenia typów projektów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Decyzje projektowe typ projektu](../../extensibility/internals/project-type-design-decisions.md)  
 W tym artykule omówiono elementu trwałości pliku projektu, a projekt mechanika decyzje, które należy podjąć przed utworzeniem nowego typu projektu.  
  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Zawiera omówienie kroków, które należy wykonać, aby utworzyć nowy typ projektu, który obsługuje zadań programistycznych jako edytowanie kodu i kompilowanie, kompilowanie, debugowanie i wdrażanie aplikacji w projekcie.  
  
 [Tworzenie wystąpień projektu za pomocą fabryk projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Zawiera informacje o tym, jak do udostępniania i umożliwia tworzenie wystąpień nowy projekt fabrykę projektów.  
  
 [Rejestrowanie typ projektu](../../extensibility/internals/registering-a-project-type.md)  
 Zawiera przykłady kodu instrukcji z rejestru zapewniające domyślnych ścieżek i danych i tabeli zawierające wpisy z rejestru skryptu dla każdej instrukcji.  
  
 [Trwałość projektu](../../extensibility/internals/project-persistence.md)  
 W tym artykule omówiono używanie `IPersistFileFormat` utrwalić zarówno w plikach, jak i obiektów na podstawie pliku projektu.  
  
 [Przy użyciu programu MSBuild](../../extensibility/internals/using-msbuild.md)  
 W tym artykule opisano, jak używać danego typu projektu [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] kompilacji aparatu, aby umożliwić użytkownikom kompilacji z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i w wierszu polecenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługa narzędzia do przeglądania Symbol](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Opisano architekturę kodu, takie jak wyświetlanie narzędzia **przeglądarki obiektów** i **widoku klasy** okna. Opisuje interfejsy i metody służące do zaimplementowania przeglądania obiektów w pakiecie VSPackage.  
  
 [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 W tym artykule omówiono znaczenie, które projekty odtwarzać przy określaniu, edytor, którego jest używany podczas otwierania elementu projektu i jak można manipulować zasoby projektu.  
  
 [Instalowanie VSPackages za pomocą Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Pokazuje sposób zapewniają VSPackage własną unikatową tożsamość i zawijanie z biblioteki DLL pakiet VSPackage i inne informacje w pakiet Instalatora Windows (. Plik MSI) w przypadku wdrożeń na klientach.  
  
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Opisuje sposób [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hierarchie widoków i adresów.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Zawiera omówienie pakiet VSPackage, instalowalnych obiektu COM, rozszerzający [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska i opisano, jak wdrożyć własny pakiet VSPackage.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Omówiono sposoby używania projektów do modyfikowania kodu, skompiluj i kompilacji kodu, uruchomić i debugowania kodu i linki do szczegółowych tematów dotyczących sposobu tworzenia typów projektów.