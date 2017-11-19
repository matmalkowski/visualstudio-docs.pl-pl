---
title: "Debugowanie rozwiązań SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14a3c7a2676c786e631b4c8b471272185b81e36c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-sharepoint-solutions"></a>Debugowanie rozwiązań SharePoint
  Rozwiązania programu SharePoint można debugować przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera. Po rozpoczęciu debugowania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wdraża pliki projektu do serwera programu SharePoint, a następnie otwiera wystąpienia witryny programu SharePoint w przeglądarce sieci Web. W poniższych sekcjach opisano sposób debugowania aplikacji SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Włączanie debugowania](#EnableDebug)  
  
-   [Proces wdrażania i debugowania za pomocą F5](#Deployment)  
  
-   [Funkcje projektu SharePoint](#Features)  
  
-   [Debugowanie przepływów pracy](#Workflow)  
  
-   [Odbiorcy zdarzeń funkcji debugowania](#FeatureEvents)  
  
-   [Włączanie rozszerzonej informacji o debugowaniu](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a>Włączanie debugowania  
 Po pierwsze debugowania rozwiązania programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], okno dialogowe ostrzega, że plik web.config nie jest skonfigurowana by włączyć debugowanie. (Plik web.config jest tworzona podczas instalowania serwera programu SharePoint. Aby uzyskać więcej informacji, zobacz [Praca z plikami Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) Okno dialogowe daje możliwość włączenia debugowania uruchomionych projekt bez debugowania lub zmodyfikowanie pliku web.config. Wybranie opcji pierwszy projekt działa normalnie. Jeśli wybierzesz opcję drugi plik web.config jest skonfigurowany do:  
  
-   Włącz w stosie wywołań (`CallStack="true"`)  
  
-   Wyłącz błędy niestandardowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
-   Włącz debugowanie kompilacji (`<compilation debug="true">`)  
  
 Wynikowy plik web.config następująco:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <configuration>  
        ...  
        <SharePoint>  
            <SafeMode MaxControls="200"  
                CallStack="true"  
                DirectFileDependencies="10"  
                TotalFileDependencies="50"  
                AllowPageLevelTrace="false">  
                ...  
            </SafeMode>  
        ...  
        </SharePoint>  
        <system.web>  
            ...  
            <customErrors mode="Off" />  
            ...  
            <compilation debug="true">  
            ...  
            </compilation>  
            ...  
        </system.web>  
        ...  
    </configuration>  
```  
  
 Aby cofnąć te zmiany i wyłączyć debugowanie, Zmień następujące [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] w pliku web.config:  
  
-   Wyłącz stos wywołań (`CallStack="false"`)  
  
-   Włącz błędy niestandardowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Wyłącz debugowanie kompilacji (`<compilation debug="false">`)  
  
##  <a name="Deployment"></a>Proces wdrażania i debugowania za pomocą F5  
 Po uruchomieniu projektu programu SharePoint w trybie debugowania procesu wdrażania SharePoint wykonuje następujące zadania:  
  
1.  Uruchamia polecenia można dostosowywać przed wdrożeniem.  
  
2.  Tworzy plik pakietu (wsp) rozwiązanie sieci Web przy użyciu [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] poleceń. Plik wsp obejmuje wszystkie niezbędne pliki i funkcje. Aby uzyskać więcej informacji, zobacz [omówienie rozwiązań](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Jeśli rozwiązanie programu SharePoint jest rozwiązanie farmy, odtwarzana [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] puli aplikacji dla określonej lokacji [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Ten krok zwalnia zablokowane przez pliki [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] proces roboczy.  
  
4.  Jeśli poprzednia wersja pakietu już istnieje, wycofuje poprzedniej wersji funkcji i plików w pliku wsp. Ten krok dezaktywuje funkcje, odinstalowanie pakietu rozwiązania, a następnie usuwa pakietu rozwiązania na serwerze programu SharePoint.  
  
5.  Instaluje bieżącej wersji funkcji i plików w pliku wsp. Ten krok dodaje i instaluje rozwiązanie na serwerze programu SharePoint.  
  
6.  W przypadku przepływów pracy instaluje zestawu przepływu pracy. Można zmienić lokalizacji za pomocą *lokalizacji zestawu* właściwości.  
  
7.  Aktywuje funkcję projektu w programie SharePoint, jeśli zakres jest witryny lub aplikacji internetowej. Funkcje w zakresach farmy i aplikacji sieci Web nie są uaktywnione.  
  
8.  Dla przepływów pracy, przepływ pracy zostanie skojarzony z biblioteki programu SharePoint, listy lub witryny, które wybrano w **Kreator dostosowania programu SharePoint**.  
  
    > [!NOTE]  
    >  To skojarzenie występuje tylko wtedy, gdy wybrano **automatycznie Skojarz przepływu pracy** w kreatorze.  
  
9. Uruchamia polecenia po wdrożeniu można dostosowywać.  
  
10. Dołącza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuger [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] procesu (w3wp.exe). Jeśli typ projektu umożliwia zmianę *rozwiązania w trybie piaskownicy* właściwość i jej wartość jest równa **true**, a następnie dołącza debuger do innego procesu (SPUCWorkerProcess.exe). Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Uruchomienie debugera JavaScript, jeśli rozwiązanie farmy jest rozwiązania programu SharePoint.  
  
12. Wyświetla odpowiednią bibliotekę, listy lub strony w przeglądarce sieci Web.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Wyświetla komunikat o stanie w oknie danych wyjściowych, po zakończeniu każdego zadania. Jeśli nie można ukończyć zadania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyświetla komunikat o błędzie w oknie Lista błędów.  
  
##  <a name="Features"></a>Funkcje projektu SharePoint  
 Funkcja jest jednostką przenośnych i moduły funkcji, które ułatwiają modyfikacji lokacji przy użyciu definicji lokacji. Istnieje również pakiet [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] elementów (WSS), które można uaktywnić dla określonego zakresu i pomagające użytkownikom wykonania określonego celu lub zadania. Szablony są wdrażane jako funkcje.  
  
 Po uruchomieniu projektu w trybie debugowania procesu wdrażania tworzy folder w *funkcji* katalogu w %COMMONPROGRAMFILES%\Microsoft Shared\web extensions\14\TEMPLATE\FEATURES serwera. Nazwy funkcji ma format *Nazwa projektu*_Feature*x*, takich jak TestProject_Feature1.  
  
 Folder rozwiązania w katalogu funkcji zawiera *definicji funkcji* pliku i *definicji przepływu pracy* pliku. Plik definicji funkcji (Feature.xml) opisuje pliki w Feature.The projektu pliku definicji projektu (Elements.xml) zawiera opis szablonu projektu. Elements.XML można znaleźć w **Eksploratora rozwiązań**, ale Feature.xml jest generowany po utworzeniu pakietu rozwiązania. Aby uzyskać więcej informacji o tych plikach, zobacz [projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a>Debugowanie przepływów pracy  
 Podczas debugowania projektów przepływu pracy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje szablonu przepływu pracy (w zależności od jego typu) do biblioteki lub do listy. Następnie należy uruchomić szablon przepływu pracy ręcznie lub przez dodanie lub uaktualnienie elementu. Następnie można użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aby debugować przepływ pracy.  
  
> [!NOTE]  
>  Jeśli dodasz odwołania do innych zestawów, upewnij się, że zainstalowanych zestawów w globalnej pamięci podręcznej zestawów ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). W przeciwnym razie rozwiązania przepływu pracy zakończy się niepowodzeniem. Aby uzyskać informacje o sposobie instalowania zestawów, zobacz [ręcznie uruchomić przepływ pracy dla dokumentu lub elementu](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Jednak proces wdrożenia nie można uruchomić przepływu pracy. Należy uruchomić przepływ pracy z witryny sieci Web programu SharePoint. Można też uruchomić przepływ pracy za pomocą aplikacji klienckiej, takich jak Microsoft Office Word 2010 lub przy użyciu osobnych kodu po stronie serwera. Użyj jednej z metod określone w **Kreator dostosowania programu SharePoint**.  
  
 Na przykład jeśli określono, że przepływ pracy można uruchomić ręcznie, należy uruchomić przepływ pracy bezpośrednio z poziomu elementu w bibliotece lub na liście. Aby uzyskać więcej informacji na temat ręcznego uruchamiania przepływu pracy, zobacz [ręcznie uruchomić przepływ pracy element dokumentu](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a>Odbiorcy zdarzeń funkcji debugowania  
 Domyślnie podczas uruchamiania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacji programu SharePoint, jego funkcje są automatycznie aktywowane automatycznie na serwerze programu SharePoint. Jednak powoduje problemy podczas debugowania odbiorcy zdarzeń funkcji, ponieważ po aktywowaniu funkcji przez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], działa w ramach innego procesu niż debugera. Oznacza to, że niektóre funkcje debugowania, takie jak punkty kontrolne, nie będą działać poprawnie.  
  
 Aby wyłączyć automatyczną aktywację funkcji w programie SharePoint i zezwolenia na debugowanie prawidłowego elementu odbiorcy zdarzeń funkcji, należy ustawić wartość projektu **aktywnej konfiguracji wdrożenia** właściwości **aktywacji nie** przed debugowania. Następnie, po rozpoczęciu debugowania aplikacji programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ręcznie aktywować tej funkcji w programie SharePoint. Aby włączyć funkcję, otwórz **Akcje witryny** menu w programie SharePoint, wybierz **ustawienia lokacji**, wybierz **Zarządzanie funkcji witryny** łącza, a następnie wybierz pozycję **Aktywuj** przycisk Dalej, funkcji, aby kontynuować debugowanie normalnego.  
  
##  <a name="EnhancedDebug"></a>Włączanie rozszerzonej informacji o debugowaniu  
 Z powodu złożonych czasami interakcje między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesu (devenv.exe) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procesu hosta (vssphost4.exe), SharePoint i warstwy WCF programu SharePoint można diagnozowanie błędów występujących podczas tworzenia, wdrażania i tak dalej żądanie. Aby pomóc w rozwiązaniu takie błędy, można włączyć rozszerzone informacje debugowania. Aby to zrobić, przejdź do następującego klucza rejestru w rejestrze systemu Windows:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools]  
  
 Jeśli "EnableDiagnostics" **REG_DWORD** wartość jeszcze nie istnieje, utworzenie go ręcznie. Ustaw wartość "EnableDiagnostics" na "1".  
  
 Ustawienie tej wartości klucza 1 powoduje, że stos śledzenia informacji w wynikach **dane wyjściowe** okna zawsze, gdy projekt błędów systemowych są wykonywane, gdy są uruchomione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby wyłączyć rozszerzone informacje debugowania, ustawić EnableDiagnostics 0 lub usuwania wartości.  
  
 Aby uzyskać więcej informacji na temat kluczy rejestru programu SharePoint, zobacz [Debugowanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z rozwiązaniami SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  