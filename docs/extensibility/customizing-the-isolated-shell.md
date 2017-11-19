---
redirect_url: shell/customizing-the-isolated-shell
title: Dostosowywanie programu Isolated Shell | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35aab40dbacd814dcec281ff1f3dd529b29d4424
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-isolated-shell"></a>Dostosowywanie programu Isolated Shell
Można dostosować aplikacji Visual Studio izolowane powłoki, zmieniając różne aspekty interfejsu użytkownika programu Visual Studio i przez ograniczenie możliwości wykonywania poleceń i funkcje zawarte w specjalistycznych aplikacji.  
  
## <a name="using-the-applicationpkgdef-file"></a>Przy użyciu pliku Application.pkgdef  
 Rozwiązanie szablonu programu isolated shell zawiera *Nazwa rozwiązania*. Plik Application.pkgdef, który umożliwia modyfikowanie następujące funkcje:  
  
##### <a name="the-application-title"></a>Tytuł aplikacji  
 Można dostosować tytuł aplikacji, którego nazwa jest wyświetlana na pasku tytułu aplikacji, zmieniając wartość na wiersz "AppName" *Nazwa rozwiązania*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Jeśli nie chcesz, aby nazwa aplikacji, aby wyświetlić projekt, który jest aktualnie załadowany, zmień wartość na wiersz "Element ShowHierarchyRootInTitle" *Nazwa rozwiązania*. Plik Application.pkgdef z DWORD: 00000001 na DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Ikona aplikacji  
 Ikona aplikacji, która jest ikonę, która jest wyświetlana nazwa aplikacji na pasku tytułu aplikacji można dostosować. Skopiuj inną ikonę do katalogu ikony. W **Eksploratora rozwiązań**, dodać ikony do folderu plików zasobów. Następnie otwórz plik VSShellStub.rc i zastąp wartość IDI_STUBPROGRAM o nazwie ikonę Nowy. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Logo wiersza polecenia  
 Możesz dostosować logo wiersza polecenia, który jest wyświetlany tekst, który pojawia się po uruchomieniu aplikacji z poziomu wiersza polecenia, zmieniając wartość wiersza "CommandLineLogo" w *Nazwa rozwiązania*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie izolowane powłoki aplikacji w warstwie podstawowa](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Nazwa podfolderu plików użytkownika  
 Można zmienić nazwę folderu aplikacji przechowuje pliki użytkownika, zmieniając wartość na wiersz "UserFilesSubFolderName" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Tytuł węzła drzewa rozwiązań w oknie dialogowym Nowy projekt  
 Tytuł węzła rozwiązania w oknie dialogowym Nowy projekt można dostosować, zmieniając wartość na wiersz "NewProjDlgSlnTreeNodeTitle" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Nagłówek szablonów zainstalowanych w oknie dialogowym Nowy projekt  
 Nagłówek szablonów zainstalowanych w oknie dialogowym Nowy projekt można zmienić, zmieniając wartość na wiersz "NewProjDlgInstalledTemplatesHdr" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Umożliwia określenie, czy Ukryj domyślnie różne pliki  
 Można określić, czy ma być Ukryj pozostałe pliki domyślne, zmieniając tę wartość na wiersz "HideMiscellaneousFilesByDefault" *Nazwa rozwiązania*. Plik Application.pkgdef. Aby ukryć różne pliki, należy ustawić wartość `dword:00000001`i aby wyświetlić pliki, ustaw wartość `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Czy chcesz wyłączyć w oknie danych wyjściowych  
 Można określić, czy nie można wyłączyć w oknie danych wyjściowych w aplikacji, zmieniając wartość na wiersz "DisableOutputWindow" *Nazwa rozwiązania*. Plik Application.pkgdef. Aby wyłączyć w oknie danych wyjściowych, należy ustawić wartość `dword:00000001`, a następnie do wyświetlenia w oknie danych wyjściowych, ustaw wartość `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Czy nie zezwalaj na porzucone pliki w oknie głównym  
 Można określić, czy nie zezwalaj na porzucone pliki w oknie głównym w aplikacji, zmieniając wartość na wiersz "AllowsDroppedFilesOnMainWindow" *Nazwa rozwiązania*. Plik Application.pkgdef. Zezwalaj na porzucone pliki, określoną wartość `dword:00000001`i aby nie zezwalaj na porzucone pliki, należy ustawić wartość `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Domyślna strona wyszukiwania  
 Można dostosować strona przeglądarki sieci web, czyli strony wyświetlanej po otwarciu okna przeglądarki sieci web, zmieniając wartość na wiersz "DefaultSearchPage" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>Domyślną stronę główną  
 Strona główna można dostosować, zmieniając wartość na wiersz "DefaultHomePage" *Nazwa rozwiązania*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie izolowane powłoki aplikacji w warstwie podstawowa](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Czy chcesz ukryć koncepcji rozwiązania  
 Można określić, czy chcesz ukryć rozwiązania w aplikacji, zmieniając wartość na wiersz "HideSolutionConcept" *Nazwa rozwiązania*. Plik Application.pkgdef. Aby ukryć rozwiązanie, należy ustawić wartość `dword:00000001`i aby wyświetlić rozwiązania, ustaw wartość `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Domyślny aparat debugowania  
 Można zmienić aparat debugowania aplikacja używa zmieniając tę wartość na wiersz "DefaultDebugEngine" *Nazwa rozwiązania*. Plik Application.pkgdef z identyfikatorem GUID aparat debugowania.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Rozszerzenie pliku opcji użytkownika  
 Można zmienić nazwę folderu aplikacji przechowuje pliki użytkownika, zmieniając wartość na wiersz "UserOptsFileExt" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Rozszerzenie pliku rozwiązania  
 Rozszerzenia plików rozwiązania, zmieniając wartość na wiersz "SolutionFileExt" można zmienić *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Domyślny element folderu plików użytkownika  
 Można zmienić nazwę głównego folderu plików użytkownika dla aplikacji, zmieniając wartość na wiersz "UserFilesSubFolderName" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identyfikator twórcy plików rozwiązania  
 Można zmienić identyfikatora używanego do plików rozwiązania, zmieniając tę wartość na wiersz "SolutionFileCreatorIdentifier" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>Domyślna lokalizacja projektów  
 Można zmienić nazwę domyślnej lokalizacji projektów, zmieniając wartość na wiersz "DefaultProjectsLocation" *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Lokalizacja pakietu aplikacji  
 Można zmienić używany dla aplikacji, zmieniając wartość na wiersz "AppLocalizationPackage" pakiet lokalizacja *Nazwa rozwiązania*. Plik Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Czy chcesz pokazać główny hierarchii w tytule  
 Można określić, czy mają być pokazywane główny hierarchii na pasku tytułu aplikacji, zmieniając wartość na wiersz "Element ShowHierarchyRootInTitle" *Nazwa rozwiązania*. Plik Application.pkgdef. Aby wyświetlić główny hierarchii, należy ustawić wartość `dword:00000001`i aby ukryć główny hierarchii, należy ustawić wartość `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Określanie strony początkowej  
 Aby określić strony początkowej aplikacji niestandardowych, w *Nazwa rozwiązania*. Plik Application.pkgdef, ustaw wartość "DisableStartPage" `dword:00000000`, a następnie w obszarze `[$RootKey$\StartPage\Default]` Ustaw identyfikator URI do lokalizacji pliku .xaml:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 W pliku Applicationcommands.vsct *Nazwa rozwiązania*projektu interfejsu użytkownika, komentarz wpis "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Musisz dodać plik .xaml i wszystkie pliki grafiki należy do *Nazwa rozwiązania* projektu. Te pliki faktycznie należy skopiować do *Nazwa rozwiązania* katalogu projektu, nie są dodawane z niektórych innym katalogu.  
  
 We wszystkich plikach, należy ustawić **typu elementu** właściwości **izolowanego pliku powłoki** w kolejności plików do skopiowania na *$RootFolder$* katalogu. (Aby ustawić **typu elementu** właściwości, kliknij prawym przyciskiem myszy plik i wybierz **właściwości**. Ta właściwość jest jedną z **właściwości konfiguracji**, **ogólne**.)  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania stron początkowych, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Przy użyciu innych elementów programu isolated shell  
 Można użyć innych plików i projektów, które są zawarte w szablonie rozwiązania programu isolated shell, aby dostosować aplikację.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Włącz/Wyłącz pakiety programu Visual Studio  
 *Nazwa rozwiązania*pliku .pkgundef umożliwia wyłączenie niektóre rodzaje funkcje programu Visual Studio, wykluczając niektórych pakietów. Na przykład następujący wiersz:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Usuwa projekt różne pliki z zestawu szablonów projektu wyświetlane w **nowy projekt** okna dialogowego. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Włącz/Wyłącz polecenia menu  
 *Nazwa rozwiązania*UI.vsct plik zawiera listę wszystkich dostępnych izolowane powłoki poleceń menu poza komentarzem. Aby wyłączyć danego polecenia, usuń znaczniki komentarza z odpowiednim. Na przykład, aby wyłączyć komentarz podział/okna, usuń znaczniki komentarza `<Define name="No_SplitCommand"/>` wiersza. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Mapy bitowej na ekranie powitalnym  
 Można dostosować mapę bitową używane na ekranie powitalnym jest wyświetlany po uruchomieniu aplikacji, zmieniając wartość wiersza "SplashScreenBitmap" w oknie *Nazwa rozwiązania*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Pomoc/informacje o oknie  
 W szablonie programu isolated shell jest oddzielny projekt można dostosować Pomoc/informacje okno aplikacji. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie podstawowego izolowanych aplikacji powłoki](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).