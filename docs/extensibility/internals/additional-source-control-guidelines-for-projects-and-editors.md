---
title: Wskazówki dotyczące kontroli dodatkowe źródła dla projektów i edytory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e39c8fcc78712f0f8d9b799789751c16f343ada6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129284"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Wskazówki dotyczące kontroli dodatkowe źródła dla projektów i edytory
Istnieje szereg wskazówki, które projekty i edytory należy stosować się do celu zapewnienia obsługi kontroli źródła.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Projekcie lub Edytor również należy wykonać następujące polecenie, aby obsługiwać kontroli źródła:  
  
|Obszar|Projekt|Edytor|Szczegóły|  
|----------|-------------|------------|-------------|  
|Prywatne kopie plików|X||Środowisko obsługuje prywatnej kopii plików. Oznacza to, że każda osoba zarejestrowana w projekcie ma jego własnej prywatnej kopię plików projektu.|  
|ANSI/Unicode trwałości|X|X|Podczas pisania kodu trwałości, utrwalić plików w formularzu ANSI, ponieważ większość programów kontroli źródła aktualnie nie obsługują standardu Unicode.|  
|Wyliczanie plików|X||Projekt musi zawierać listę wszystkich plików znajdujących się w i musi być w stanie wyliczyć listy plików przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Projekt, również powinny ujawniać nazwy elementów za pomocą jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> wdrażania i obsługi technicznej wyszukiwanie nazw (w tym pliki specjalne) za pośrednictwem jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementacji.|  
|Format tekstu|X|X|Jeśli to możliwe, pliki powinny być w formacie tekstowym do obsługi scalanie różne wersje. Pliki, które nie są w formacie tekstowym nie mogą być scalone z innymi wersjami pliku później. Format tekstu preferowany jest XML.|  
|Na podstawie odwołania|X||Projekty oparte na odwołanie łatwo są obsługiwane w kontroli źródła. Jednak projekty oparte na katalogu są również obsługiwane przez kontroli źródła, tak długo, jak projekt może wygenerować listy plików na żądanie, niezależnie od tego, czy te pliki znajdują się na dysku. Otwieranie projektu z kontroli źródła, plik projektu jest obniżył pierwszej przed jej plików.|  
|Utrwalanie w przewidywalnej kolejności obiektów i właściwości|X|X|Utrwalanie w przewidywalnej kolejności, takich jak alfabetycznie, aby ułatwić scalanie plików.|  
|Załaduj ponownie|X|X|Podczas zmiany pliku na dysku, Edytor musi mieć możliwość załadować go ponownie. Uczestnictwa w kontroli źródła, środowisko, załaduje danych przez wywołanie metody z <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementacji. Podczas wyewidencjonowania wywołanego IVsQueryEditQuerySave jest najtrudniejsze przypadku Załaduj ponownie::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przetwarzania informacji. Jednak kod Załaduj ponownie musi być można uruchomić w tej sytuacji.<br /><br /> Środowisko automatycznie ładuje ponownie pliki projektu. Jednak projekt musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> jeśli zawiera on zagnieżdżone hierarchie w celu zapewnienia obsługi ponownego ładowania zagnieżdżone pliki projektu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)