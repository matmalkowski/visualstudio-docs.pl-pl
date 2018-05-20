---
title: Debugowanie projektów pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9ce3b064f97c2a04b8d7483080e260105aebab9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="debug-office-projects"></a>Debugowanie projektów pakietu Office
  Projekty pakietu Office można debugować przy użyciu tego samego pakietu Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] narzędzi, które jest używane dla innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Funkcje debugera, takie jak możliwość wstawiania punktów przerwania i wyświetlić zmiennych w **zmiennych lokalnych** okna, są również dostępne podczas debugowania w projektach pakietu Office. Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] narzędzia debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Aby uprościć debugowania, zamknij wszystkie wystąpienia aplikacji pakietu Office, zanim kompilacji i debugować go.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="start-and-stop-the-debugger"></a>Uruchamianie i zatrzymywanie debugera  
 Można uruchomić debugowania projektu pakietu Office, tak samo, jak rozpoczynania debugowania innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów; na przykład możesz nacisnąć przycisk **F5** klucza. Po rozpoczęciu debugowania projektu dodatku VSTO, zainicjowany nowy proces do docelowej aplikacji pakietu Office i dodatku VSTO został załadowany.  
  
 Po rozpoczęciu debugowania projektu na poziomie dokumentu, dokument lub skoroszyt zostanie otwarty w nowy proces Word czy Excel.  
  
 Po zatrzymaniu debugera debuger nagle kończy proces aplikacji lub odłącza, jeśli masz ustawioną odłączyć debugera. Wszystkie dokumenty, otwieranych w procesie zakończone aplikacji pakietu Office są również zamknięte bez ostrzeżenia, a wszystkie niezapisane zmiany zostaną utracone. Może to obejmować wszystkie dokumenty lub skoroszytów, które są otwarte, gdy debuger jest uruchomiona.  
  
 Zazwyczaj jest lepszym rozwiązaniem odłączyć od procesu przed zatrzymaniem debugera, dzięki czemu można zamknąć aplikacji pakietu Office w zwykły sposób. Można również odłączyć od procesu najpierw Jeśli nadal chcesz współpracować z otwartego dokumentu lub arkuszu po zatrzymaniu debugera.  
  
 Jeśli debugujesz dostosowania poziomie dokumentu dla programu Word wielokrotnie zatrzymanie debugera i powoduje Word zamknąć nagle może prowadzić do szablonu normalnej uszkodzeniu. W takim przypadku można usunąć uszkodzony szablonu normalnej i jego zostanie automatycznie utworzona ponownie przy następnym otwarciu programu Word. Jednak nie zostaną odtworzone makr, które były przechowywane w szablonie Normal.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Debugowanie pakietu Office 2013 VSTO dodatki za pomocą pakietu Office 2013 lub Office 2016  
 Jeśli używasz programu Visual Studio 2015 i obie wersje pakietu Office zainstalowane obok siebie, Visual Studio zostanie uruchomiony pakiet Office 2016. Jeśli używasz programu Visual Studio 2013, Visual Studio rozpoczyna pakietu Office 2013.  
  
 Jeśli chcesz debugować dodatek VSTO przy użyciu różnych wersji pakietu Office (2013 lub 2016), otwórz **Projektant projektu**, a następnie w **debugowania** , wybierz pozycję **uruchomienia programu zewnętrznego**przycisk opcji. Następnie przejdź do lokalizacji pliku wykonywalnego odpowiedniej aplikacji pakietu Office.  
  
## <a name="f10-and-f11-behavior"></a>Zachowanie F10 i F11  
 Po rozpoczęciu debugowania projektu pakietu Office **F10** i **F11** nie ma zachowania podczas uruchamiania debugowania innych projektów Visual Basic lub C#. W projektach Visual Basic lub C# debuger zatrzymuje na funkcja main; w projektach pakietu Office Visual Studio nie mają kontrolę nad główną funkcją aplikacji pakietu Office. Jednak w trakcie debugowania, **F10** i **F11** mają te same funkcje jak projekty Visual Basic i C#.  
  
## <a name="display-exceptions"></a>Wyświetlić wyjątki  
 Ze względu na sposób, w jaki kod zarządzany wchodzi w interakcję z kodem niezarządzanym Visual Studio nie są wyświetlane błędy, które są generowane przez aplikacje Microsoft Office. Na przykład Dodaj VSTO utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio zgłasza wyjątek, aplikacji Microsoft Office będzie nadal bez wyświetlania wystąpił błąd. Aby wyświetlić te błędy, ustaw debugera do dzielenia na wspólnej wyjątki środowiska uruchomieniowego języka. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Jeśli ustawisz debugera do dzielenia na wspólnej wyjątki środowiska uruchomieniowego języka wszystkie wyjątki będą teraz wkroczenia do debugera, w tym te, które zostały obsłużone i niektóre wyjątki pierwszej szansy ze środowiska uruchomieniowego, które może nie być odpowiednie dla projektu. Błędy nie odwołuje się do msosec, ale znaleziono są wyświetlane w każdym projekcie są bezpiecznie zignorować. Te wyjątki msosec nie wpływa na rozwiązania.  
  
 Można również użyć **spróbuj... CATCH** instrukcje wokół metody przechwytują wyjątki.  
  
 Domyślnie program Visual Studio nie również wyświetlana Just In Time debugowania błędów dla projektów pakietu Office; można jednak włączyć tę funkcję, dzięki czemu widać błędów, które są wywoływane. Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio Just In Time](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Argumenty wiersza polecenia  
 Jeśli **Akcja uruchamiania** na **debugowania** strony właściwości jest równa **uruchomić projekt**, Visual Studio nie używa argumentów wiersza polecenia podczas debugowania projektu, nawet jeśli masz Ponieważ opcje uruchamiania, należy określić argumenty wiersza polecenia. Jeśli chcesz użyć argumenty wiersza polecenia, po rozpoczęciu debugowania, musisz wybrać **Akcja uruchamiania** innych niż **uruchomić projekt**.  
  
## <a name="source-control"></a>Kontrola źródła  
 Debugowanie właściwości nie są współużytkowane przez wielu użytkowników pod kontrolą źródła. Projekty Visual Basic i C# przechowywane właściwości debugowania w pliku specyficzne dla użytkownika (*ProjectName*. vbproj.user lub *ProjectName*. csproj.user), a ten plik nie jest pod kontrolą źródła. W przypadku debugowania jest więcej niż jedna osoba, każda osoba właściwości debugowania ręcznie wprowadzić.  
  
## <a name="debug-cached-datasets-in-a-document-level-project"></a>Debugowanie pamięci podręcznej zestawów danych w projektach na poziomie dokumentu  
 Za każdym razem, gdy w przypadku kompilowania projektu dataset jest opróżniany i utworzona ponownie. Jeśli chcesz debugować pamięci podręcznej zestawu danych, należy otworzyć dokument poza Visual Studio, a następnie dołącz debugera.  
  
## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Projekty dokument programu Word debugowania na podstawie dokumentu programu Word 97-2003 (* .doc) format  
 Do debugowania projektu dokument programu Word, na podstawie dokumentu programu Word 97-2003 (*/* doc *) formatu, folder projektu należy dodać do listy zaufanych folderów. Aby uzyskać więcej informacji, jak to zrobić, zobacz [przyznać zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
## <a name="debug-disabled-add-ins"></a>Debugowania wyłączone dodatki  
 Aplikacje Microsoft Office może spowodować wyłączenie dodatków VSTO, które nieoczekiwane zachowanie. Aplikacja Microsoft Office powoduje wyłączenie dodatków VSTO, aby zapobiec kodu powodować problemy podczas ładowania każdym uruchomieniu aplikacji. Jednak również jest łatwo spowodować nieoczekiwane zachowanie podczas debugowania typowych. Informacje o sposobie ponowne włączenie dodatki VSTO, zobacz [porady: ponowne włączanie dodatku VSTO, która została wyłączona](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Istnieją dwa typy wyłączenia, aplikacje Microsoft Office używany dla dodatków VSTO: wyłączanie twardym i wyłączanie nietrwałego.  
  
### <a name="hard-disabling"></a>Twarde wyłączenie  
 Wyłączenie ciężko może wystąpić, gdy dodatku VSTO powoduje, że aplikacja jest nieoczekiwanie zamykany. Go może również wystąpić na komputerze deweloperskim po zatrzymaniu debugera podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonuje program obsługi zdarzeń w Twojej dodatku VSTO. Gdy dodatku VSTO jest wyłączone twardym, pojawi się w **elementy wyłączone** listy w aplikacji.  
  
 W przypadku aplikacji pakietu Office twardych wyłącza Add VSTO utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio, aplikacja wyłącza tylko VSTO dodatek, który spowodował błąd. Innych dodatków VSTO utworzone za pomocą narzędzi programowania pakietu Office w Visual Studio dla tej aplikacji pakietu Office będą w dalszym ciągu obciążenia.  
  
### <a name="soft-disabling"></a>Wyłączanie elastyczne  
 Wyłączanie nietrwałego może wystąpić, gdy dodatku VSTO generuje błąd, który nie powoduje nieoczekiwanego zamknięcia aplikacji. Na przykład aplikacji soft może wyłączyć dodatku VSTO, jeśli zgłasza nieobsługiwany wyjątek podczas <xref:Microsoft.Office.Tools.AddIn.Startup> program obsługi zdarzeń jest wykonywany. Gdy dodatku VSTO jest wyłączone miękkie, zostanie wyświetlony w **dodatki nieaktywne aplikacji** listy w aplikacji i zmienia wartość **LoadBehavior** wpisu rejestru dotyczącego VSTO Dodatek do wskazywania zwolniony. Aby uzyskać więcej informacji na temat **LoadBehavior** wpis rejestru, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Rozwiązywanie problemów z błędami instalacji za pomocą Podglądu zdarzeń  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapisuje komunikaty w Podglądzie zdarzeń w systemie Windows, wszystkie wyjątki, które są generowane po zainstalowaniu lub odinstalowaniu rozwiązań pakietu Office. Te komunikaty służy do rozwiązywania instalacji i problemy z wdrażaniem.  
  
## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Rozwiązywanie problemów z uruchamianiem za pomocą dziennika pliku i komunikaty o błędach  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Można zapisać wszystkich błędów występujących podczas uruchamiania dziennika pliku lub wyświetlić każdy z błędów w oknie komunikatu. Te opcje są domyślnie wyłączone. Opcje można włączyć, tworząc zmiennych środowiskowych.  
  
 Aby wyświetlić liczbę błędów w oknie komunikatu, Utwórz zmienną środowiskową o nazwie `VSTO_SUPPRESSDISPLAYALERTS` i ustaw ją na 0 (zero). Komunikaty można pominąć, usuwając zmiennej środowiskowej lub ustawiona na 1 (jeden).  
  
 Można zapisać błędów w pliku dziennika, należy utworzyć zmienną środowiskową o nazwie `VSTO_LOGALERTS` i wartości 1 (jeden). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy plik dziennika w folderze, który zawiera manifest wdrażania dodatku VSTO lub w folderze, który zawiera dokument lub skoroszytu, który jest skojarzony z dostosowań. W przypadku niepowodzenia [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tworzy plik dziennika w lokalnej *% TEMP %* folderu. Na poziomie aplikacji VSTO dodatki, nazwa domyślna to *nazwa dodatku*. vsto.log. Dla projektów na poziomie dokumentu, nazwa pliku dziennika jest *nazwy dokumentu*. *rozszerzenie*log, takich jak ExcelWorkbook1.xlsx.log. Aby zatrzymać rejestrowanie błędów, Usuń zmienną środowiskową lub równa 0 (zero).  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Porady: ponowne włączanie dodatku VSTO, która została wyłączona](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)  
  
  