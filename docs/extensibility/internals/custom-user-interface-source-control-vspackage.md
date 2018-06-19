---
title: Niestandardowy interfejs użytkownika (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebd2361e94e9b1430f5bac99f2e71dc53a02ebf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131890"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Niestandardowy interfejs użytkownika (VSPackage kontroli źródła)
Pakiet VSPackage deklaruje elementy jego menu i ich domyślne stany poprzez plik tabeli poleceń w usłudze Visual Studio (vsct). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) do momentu załadowania pakiet VSPackage wyświetla elementów menu w ich domyślne Stany. Następnie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementów menu.  
  
 Pakiet VSPackage można ustawić klucz rejestru, aby pakiet VSPackage mogą być ładowane automatycznie w zależności od kontekstu polecenia interfejsu użytkownika, chociaż zazwyczaj kontroli źródła pakiet VSPackage powinny zostać załadowane na żądanie, a nie tylko przełączanie do określonego kontekstu interfejsu użytkownika. Aby uzyskać więcej informacji na temat klucza rejestru AutoLoadPackages, zobacz [Zarządzanie VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Pakiet VSPackage interfejsu użytkownika  
 Pakiet kontroli źródła jest wdrażany jako pakiet VSPackage i nie używa elementów interfejsu użytkownika z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Każdy pakiet VSPackage kontroli źródła należy określić własne elementy interfejsu użytkownika, takich jak elementy menu, grupy menu okna narzędzi, paski narzędzi i wszelkie wymagane interfejsu użytkownika dla opcji ustawienia określonego do kontroli źródła pakiet VSPackage. Te elementy interfejsu użytkownika można włączyć statycznie lub dynamicznie. Statyczne elementy interfejsu użytkownika są zdefiniowane w pliku vsct i są wyświetlane, czy pakiet VSPackage jest załadowany lub nie. Dynamiczne elementy interfejsu użytkownika mogą być widoczne w zależności od konkretnego polecenia kontekst interfejsu użytkownika, takich jak <xref:EnvDTE.Constants.vsContextNoSolution>, lub w wyniku wywołania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Widoczność dynamiczne elementy interfejsu użytkownika spełnia strategii opóźnionego ładowania VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Ograniczenia interfejsu użytkownika na VSPackages kontroli źródła  
 Ponieważ pakiet VSPackage kontroli źródła nie można usunąć z IDE po załadowaniu, pakiet VSPackage musi mieć możliwość wprowadź nieaktywny. Gdy pakiet VSPackage otrzyma powiadomienie, że nie jest już aktywny, pakiet VSPackage powoduje wyłączenie jego interfejsie użytkownika i ignoruje interakcji IDE zewnętrznych. Implementacja pakiet VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody powinny Ukryj poleceń podczas VSPackage nie jest aktywny.  
  
 Kontrola źródła, co pakiet VSPackage musi implementować `IVsSccProvider` interfejsu. Dwie metody w interfejsie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, musi być implementowana przez pakiet VSPackage.  
  
 Kontroli źródła, pakiet VSPackage może subskrybuje różnych zdarzeń IDE, implementowanych za <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>i tak dalej. Ponadto pakiet VSPackage mogą wdrażać interfejsów włączone rejestru wywołania zwrotnego, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Te muszą wszystkie zignorowane, kiedy nieaktywne.  
  
 Poniższa lista zawiera interfejsy dotyczy aktywnego stanu kontroli źródła pakiet VSPackage:  
  
-   Śledzenie zdarzeń dokumentów projektu.  
  
-   Rozwiązanie zdarzenia.  
  
-   Interfejsy trwałości rozwiązania. Gdy nieaktywny, pakietów nie należy zapisać .sln i .suo plików.  
  
-   Właściwości rozszerzeń.  
  
 Wymagane <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, a także interfejsami opcjonalne skojarzone z kontroli źródła, nie są nazywane podczas VSPackage kontroli źródła jest nieaktywny.  
  
 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchamia IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ustawia kontekst interfejsu użytkownika poleceń identyfikator bieżącego kontroli źródła domyślny identyfikator pakiet VSPackage. Powoduje to statycznych interfejsu użytkownika z kontroli źródła active pakiet VSPackage pojawią się w środowisku IDE bez faktycznie ładowania pakiet VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wstrzymuje działanie na pakiet VSPackage zarejestrować za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> przed jego sprawia, że wszystkie wywołania pakiet VSPackage.  
  
 W poniższej tabeli przedstawiono szczegółowe informacje o sposobie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ukrywa różne elementy interfejsu użytkownika.  
  
|Element interfejsu użytkownika|Opis|  
|-------------|-----------------|  
|Menu i pasków narzędzi|Pakiet kontroli źródła należy ustawić początkowej stanów widoczność menu i paska narzędzi z Identyfikatorem pakietu kontroli źródła w [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sekcji pliku vsct. Dzięki temu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE do ustawiania stanu elementów menu odpowiednio bez ładowania pakiet VSPackage i wywoływania implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody.|  
|Okna narzędzi|Kontroli źródła pakiet VSPackage ukrywa żadnych okien narzędzi, który jest właścicielem, gdy jest on nieaktywny.|  
|Kontroli źródła pakiet VSPackage określonych opcji stron|Klucz rejestru HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts umożliwia pakiet VSPackage ustawiania kontekstów, w których wymaga jego stron opcje mają być wyświetlane. Wpisu rejestru w kluczu musi być utworzone przy użyciu usługi identyfikator usługi kontroli źródła i przypisywania go wartość DWORD na 1. Zawsze, gdy wystąpi zdarzenie interfejsu użytkownika w kontekście pakiet VSPackage jest zarejestrowana z kontroli źródła, pakiet VSPackage zostanie wywołany, jeśli jest aktywny.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)