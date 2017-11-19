---
title: "Właściwości i metody przedłużony podtypów projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd4e46148950af925b7b41c4e3b5bd66fce5063c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Właściwości i metody przedłużony podtypów projektu
Podtyp projektu ma wiele możliwości w celu wywierania wpływu na zachowanie projektu, ponieważ jest tworzony jako agregatora podstawowego projektu. Ta sekcja zawiera podsumowanie niektórych funkcji, które mogą być rozszerzone lub modyfikowane przez podtypów projektu.  
  
## <a name="features-gained-by-aggregation"></a>Funkcje uzyskany w wyniku agregacji  
 W poniższej tabeli przedstawiono wiele metod, które podtypów projektu do zastąpienia w podstawowej projektów agregacji.  
  
|Metody zastąpione agregacji|Podtyp projektu|  
|---------------------------------------|---------------------|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Włącza podtypu projektu<br /><br /> -Zmień podpisu i ikona węzła projektu.<br />-Całkowicie zastąpić projektu `Browse` obiektu.<br />-Kontrolowanie, czy można zmienić nazwy projektu.<br />-Kolejność sortowania control.<br />-Kontekst użytkownika control dla dynamicznej pomocy.|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umożliwia podtypu projektu sterować kontekstowe usług są dostarczane do projektantów i edytory.|  
|Z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Włącza podtypu projektu<br /><br /> -Uczestniczyć w routing poleceń dla polecenia projektu.<br />-Dodaj, usuń lub wyłącz zarówno projektu otoczenia oraz Eksploratora rozwiązań aktywnych poleceń.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Włącza podtypu projektu do filtrowania, użytkownik zobaczy w **Dodaj nowy element** okno dialogowe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Włącza podtypu projektu<br /><br /> -Określ generator domyślne rozszerzenie pliku podane.<br />-Mapowania nazwy człowieka generator do odczytu do obiektu COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Właściwości używanych przez podtypów projektu  
 System projektu środowiska i base można użyć właściwości z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> wyliczenia szczegółowe w poniższej tabeli w celu umożliwienia podtypu projektu do kontrolowania różnych funkcji systemu projektu.  
  
|Właściwość VSHPROPID|Podtyp projektu|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Umożliwia podtyp projektu kontrolować zawartość **Dodaj element** okno dialogowe. Podtypu projektu można podać specyfikację nowy szablon katalogów, dodawanie nowych typów elementów, Usuń istniejące elementy i reorganizować podzbiór elementów w projekcie podstawowej **Dodaj element** okno dialogowe.|  
|`PropertyPagesCLSIDList`|Umożliwia podtyp projektu dodać lub usunąć strony właściwości niezależny od konfiguracji.|  
|`CfgPropertyPagesCLSIDList`|Umożliwia podtypu projektu dodać lub usunąć strony właściwości zależne od konfiguracji.|  
|`ExtObjectCATID`|Umożliwia zapewnienie rozszerzenie automatyzacji dla projektu lub projektów obiektów elementu znając CATID rozszerzeń podtypu projektu. Na przykład podtyp projektu można podać niestandardowy `Project.Extender("<subtype>")` obiektu.|  
|`BrowseObjectCATID`|Umożliwia podtypu projektu dostarczyć rozszerzenie automatyzacji dla `Browse` obiektu znając CATID rozszerzeń. Na przykład podtyp projektu można dodać dodatkowe właściwości, aby <xref:EnvDTE.Project.Properties%2A> kolekcji.|  
|`CfgBrowseObjectCATID`|Umożliwia podtypu projektu dostarczyć rozszerzenie automatyzacji dla obiekt przeglądania konfiguracji projektu. Na przykład podtyp projektu można dodać dodatkowe właściwości, aby <xref:EnvDTE.Configuration.Properties%2A> kolekcji.|  
|`CfgExtObjectCATID`|Umożliwia podtypu projektu dostarczyć rozszerzenie automatyzacji dla obiekt konfiguracji.|  
|`DefaultPlatformName`|Umożliwia podtypu projektu można określić nazwy platformy dla obiekt konfiguracji projektu.|  
  
 Podstawowy projekt udostępnia domyślną implementację powyżej właściwości. Podstawowy projekt pobiera te przez wywołanie metody `QueryInterface` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na podtyp projektu najbardziej zewnętrznego, dzięki czemu podtypu projektu do przesłonięcia implementację właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Podtypów projektu](../../extensibility/internals/project-subtypes-design.md)