---
title: "Określanie, które Edytor otwiera plik w projekcie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7c69bc08d0f1bb72a37b76fca2d402d73036deb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Określanie otwieranym edytora plików w projekcie
Po otwarciu pliku w projekcie, środowisko przechodzi przez proces sondowania, po pewnym czasie otwierania odpowiedniego edytora lub projektanta dla tego pliku. Procedury początkowej przez środowisko jest taki sam dla edytory standardowe i niestandardowe. Środowisko używają różnych kryteriów, podczas sondowania Edytor Otwórz plik i pakiet VSPackage musi koordynować ze środowiskiem w trakcie tego procesu.  
  
 Na przykład, gdy użytkownik wybierze **Otwórz** polecenie **pliku** menu, a następnie wybiera `filename`.rtf (lub inne pliki z rozszerzeniem .rtf) wywołań środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Implementacja dla każdego projektu, po pewnym czasie okrągło wszystkich wystąpień projektu w rozwiązaniu. Projekty zwraca zestaw flag, które identyfikują oświadczeń w dokumencie według priorytetu. Korzystając z najwyższym priorytetem, środowisko wywołuje odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Aby uzyskać więcej informacji na temat procesu sondowania [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt różne pliki oświadczeń wszystkie pliki, które nie zostały przejęte przez innych projektów. W ten sposób edytory niestandardowe mogą otwierać dokumenty, zanim standardowe edytory je otworzyć. Jeśli w projekcie plików pozostałych oświadczeń pliku, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody do otwierania pliku przy użyciu standardowego edytora. Środowisko sprawdza listy wewnętrznej edytory zarejestrowanych na taki, który obsługuje .rtf — pliki. Ta lista znajduje się w następującym kluczu rejestru:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Środowisko sprawdza również identyfikatorów klasy w kluczu HKEY_CLASSES_ROOT\CLSID dla obiektów, które mają podklucza DocObject. Jeśli znajduje się rozszerzenie pliku, wbudowana wersja aplikacji, na przykład Microsoft Word, zostanie utworzony w miejscu w programie Visual Studio. Te obiekty dokumentu musi być złożone pliki, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> musi implementować interfejs lub obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejsu.  
  
 Jeśli nie istnieje żadna fabryki edytora plików RTF w rejestrze, a następnie środowiska jest wyszukiwany w HKEY_CLASSES_ROOT \\klucz .rtf i otwiera edytor istnieje określony. Jeśli rozszerzenie pliku nie zostanie znaleziony w wpisów z HKEY_CLASSES_ROOT, następnie środowiska używa Edytor tekstu Visual Studio core można otworzyć pliku, jeśli jest to plik tekstowy.  
  
 Jeśli Edytor tekstu core nie powiedzie się, co ma miejsce, jeśli plik nie jest plikiem tekstowym, następnie środowiska używa jej Edytor plików binarnych dla pliku.  
  
 Jeśli środowisko znaleźć edytora dla rozszerzenia .rtf w jego rejestru, ładuje pakiet VSPackage, który implementuje ten fabryki edytora. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody na nowy pakiet VSPackage. Wywołania pakiet VSPackage `QueryService` dla `SID_SVsRegistorEditor`za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodę, aby zarejestrować fabryki edytora ze środowiskiem.  
  
 Środowisko ponownie sprawdza listy wewnętrznej zarejestrowanych edytory można znaleźć fabryki edytora nowo zarejestrowanych dla plików RTF. Środowisko wywołuje implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, przekazując typ nazwy i widoku pliku do utworzenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>