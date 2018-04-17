---
title: 'Porady: tworzenie projektów Office w Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50739bfde7578a49226e5396c8eeb78e56c4b0ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Porady: tworzenie projektów Office w Visual Studio
  Można użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do tworzenia dodatku VSTO i na poziomie dokumentu dostosowania aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji na temat tych typów projektów, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Aby utworzyć projekt dodatku narzędzi VSTO  
  
1.  Na **pliku** menu, wybierz **nowy**, **projektu**. Jeśli Twoje zintegrowane środowisko programistyczne (IDE) jest skonfigurowany do używania [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ustawienia środowiska deweloperskiego na **pliku** menu, wybierz **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
    > [!NOTE]  
    >  Docelowy projektów pakietu Office [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] domyślnie. Aby uzyskać więcej informacji, zobacz [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
2.  W okienku szablonów w węźle dla języka, którego chcesz użyć, rozwiń **Office i SharePoint**.  
  
3.  Wybierz **dodatków pakietu Office** węzła.  
  
4.  Na liście szablony projektów wybierz szablon projektów dodatku VSTO. Aby uzyskać listę dostępnych szablonów dodatku VSTO projektu, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Jeśli szablony projektu nie są widoczne po wybraniu **dodatków pakietu Office** węzła, upewnij się, że **.NET Framework 4** lub nowszego jest zaznaczona w polu kombi w górnej części okna dialogowego. Szablony projektów pakietu Office są widoczne dla obu wersji programu .NET Framework.  
  
5.  W **nazwa** wpisz nazwę dla projektu. Domyślnie nazwa projektu jest również używane jako nazwa rozwiązania.  
  
6.  W **lokalizacji** wprowadź ścieżkę, w której chcesz utworzyć projekt. Można używać bezwzględnych i uniwersalnych nazw ścieżek convention (UNC). Nie należy używać protokołu HTTP, FTP lub innych ścieżek protokołu.  
  
     Lokalizacje mieć następujący format:  
  
    -   [*dysku*\]: \  
  
    -   \\\\*Serwer*\\*udziału*  
  
     W tym miejscu nie należy używać następujących znaków:  
  
    -   Znak gwiazdki (*)  
  
    -   Pionowej kreski (|)  
  
    -   Dwukropka (:) (Oprócz następujących literę dysku).  
  
    -   Podwójny cudzysłów (") (ścieżek zawierających spacje nie są znaki cudzysłowu.)  
  
    -   Mniej niż (\<)  
  
    -   Większości (>)  
  
    -   Znak zapytania (?)  
  
    -   Znaku procentu (%)  
  
7.  Wybierz **OK** przycisku.  
  
    > [!NOTE]  
    >  Dodatek projekty są zawsze zapisywane podczas ich tworzenia. Nie można ich utworzyć jako tymczasowe projekty. Aby uzyskać więcej informacji na temat tymczasowe projekty, zobacz [tymczasowe projekty](http://msdn.microsoft.com/en-us/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Aby utworzyć projekt dostosowania na poziomie dokumentu  
  
1.  Na **pliku** menu, wybierz **nowy**, **projektu**. Jeśli środowiskiem IDE jest skonfigurowany do używania ustawienia środowiska deweloperskiego Visual Basic, na **pliku** menu, wybierz **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
    > [!NOTE]  
    >  Docelowy projektów pakietu Office [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] domyślnie.  Aby uzyskać więcej informacji, zobacz [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
2.  W okienku szablonów w węźle dla języka, którego chcesz użyć, rozwiń **Office i SharePoint**.  
  
3.  Wybierz **dodatków pakietu Office** węzła.  
  
4.  Na liście szablony projektów wybierz szablon projektu na poziomie dokumentu. Lista szablonów dostępnych projektu na poziomie dokumentu, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Jeśli szablony projektu nie są widoczne po wybraniu **dodatków pakietu Office** węzła, upewnij się, że **.NET Framework 4** lub nowszego jest zaznaczona w polu kombi w górnej części okna dialogowego. Szablony projektów pakietu Office są widoczne dla obu wersji programu .NET Framework.  
  
5.  W **nazwa** wpisz nazwę dla projektu. Domyślnie ta nazwa jest również używana dla dokumentu. Jeśli środowiskiem IDE ustawiono za pomocą ustawienia środowiska deweloperskiego Visual C# lub ustawienia ogólne środowiska deweloperskiego, również wprowadź lokalizację i nazwę rozwiązania.  
  
    > [!NOTE]  
    >  Nie można używać znaków dwuskładnikowych, ścieżkę lokalizacji projektu lub nazwą projektu. Ponadto jeśli planujesz wdrożyć rozwiązanie do użycia w trybie offline, znaki w nazwie projektu musi znajdować się w specyfikacji protokołu HTTP.  
  
6.  Wybierz **OK** przycisku.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
7.  Wybierz **Utwórz nowy dokument** Jeśli chcesz utworzyć nowy dokument dla rozwiązania, lub wybierz **Skopiuj istniejący dokument** Jeśli chcesz dostosować istniejący dokument.  
  
     Jeśli tworzysz nowy dokument, określ nazwę w **nazwa** i wybierz format dokumentu za pomocą **Format** pole. Aby uzyskać więcej informacji o dostępnych formatów, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
     Jeśli używasz istniejącego dokumentu, określ lokalizację dokumentu w **pełną ścieżkę istniejącego dokumentu** pole. Można użyć bezwzględne ani ścieżki UNC. Nie należy używać protokołu HTTP, FTP lub innych ścieżek protokołu do dokumentu.  
  
     Lokalizacje mieć następujący format:  
  
    -   [*dysku*\]: \  
  
    -   \\\\*Serwer*\\*udziału*  
  
     W tym miejscu nie należy używać następujących znaków:  
  
    -   Znak gwiazdki (*)  
  
    -   Pionowej kreski (|)  
  
    -   Dwukropka (:) (Oprócz następujących literę dysku).  
  
    -   Podwójny cudzysłów (") (ścieżek zawierających spacje nie są znaki cudzysłowu.)  
  
    -   Mniej niż (\<)  
  
    -   Większości (>)  
  
    -   Znak zapytania (?)  
  
    -   Znaku procentu (%)  
  
    > [!NOTE]  
    >  Jeśli używasz istniejącego dokumentu w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] projektu, używają tylko dokumenty, które zostały utworzone w lub przekonwertować [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Podobnie jeśli używasz istniejącego dokumentu programu Word 2010 projektu, używają tylko dokumenty, które zostały utworzone w lub przekonwertować Word 2010. Niektóre funkcje zostaną wyłączone w dokumencie, jeśli używasz dokument, który został utworzony we wcześniejszej wersji programu Word. Jeśli spróbujesz pisania kodu, który korzysta z tych funkcji, mogą wystąpić błędy w projekcie. Aby dokonać konwersji dokumentu, otwórz go w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub Word 2010 na **pliku** na Wstążce, wybierz pozycję **informacji**, **przekonwertować**.  
  
8.  Wybierz **Zakończ**.  
  
9. Dodaj folder projektu i jego podfolderach do listy zaufanych lokalizacji w Centrum zaufania w programie Word w następujących przypadkach:  
  
    -   Tworzysz dokument programu Word, który jest oparty na pliku docm, a dokument zawiera projekt VBA lub obsługuje formanty formularzy systemu Windows. Dodawanie do listy zaufanych lokalizacji folderu projektu, pomoże upewnij się, że dokument działa zgodnie z oczekiwaniami w czasie projektowania.  
  
    -   Tworzysz opartego na dotx projektu szablon programu Word. Należy dodać folder projektu do listy zaufanych lokalizacji dzięki czemu można uruchamiać i debugowania projektu.  
  
     Aby uzyskać więcej informacji na temat sposobu dodawania dokumentu do zaufanej lokalizacji, zobacz witrynę sieci web Microsoft Office Online [Utwórz, usuń lub zmień zaufanej lokalizacji plików](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)   
 [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  