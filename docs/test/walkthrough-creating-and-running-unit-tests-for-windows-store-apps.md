---
title: "Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: "21"
ms.author: douge
manager: douge
ms.openlocfilehash: 32cab11dd909fc8b60134ebff0d5f37c0b14dcd6
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="walkthrough-creating-and-running-unit-tests-for-uwp-apps"></a>Wskazówki: Tworzenie i Uruchamianie testów jednostkowych dla aplikacji platformy uniwersalnej systemu Windows
Visual Studio obsługuje do przeprowadzania testów jednostkowych zarządzanego [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji i zawiera szablony bibliotek testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.  
  
> [!TIP]
>  Aby uzyskać więcej informacji o tworzeniu [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji, zobacz [wprowadzenie do aplikacji platformy UWP](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 Program Visual Studio oferuje następujące jednostki testowanie funkcji logowania:  
  
-   [Tworzenie projektów testów jednostkowych](#CreateAndRunUnitTestWin8Tailored_Create)  
  
-   [Edytuj Manifest jednostkowy projekt testowy](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
-   [Kod testu jednostkowego](#CreateAndRunUnitTestWin8Tailored_Code)  
  
-   [Uruchom testy jednostkowe](#CreateAndRunUnitTestWin8Tailored_Run)  
  
 W poniższych procedurach opisano kroki tworzenia, uruchamiania i debugowania testów jednostkowych dla zarządzanych systemu Windows 8 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Visual Studio  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Create"></a>Tworzenie projektów testów jednostkowych  
  
#### <a name="to-create-a-unit-test-project-for-a-uwp-app"></a>Aby utworzyć jednostkowy projekt testowy dla aplikacji platformy uniwersalnej systemu Windows  
  
1.  Z **pliku** menu, wybierz **nowy projekt**.  
  
     Wyświetla okno dialogowe Nowy projekt.  
  
2.  W obszarze Szablony, wybierz język programowania, które chcesz utworzyć testu jednostkowego w, a następnie wybierz pozycję skojarzony [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Biblioteka testów jednostkowych. Na przykład wybrać **Visual C#** , a następnie wybierz **uniwersalnych systemu Windows**, a następnie wybierz pozycję **Biblioteka testów jednostkowych (uniwersalna systemu Windows)**.  
  
    > [!NOTE]
    >  Visual Studio zawiera szablony bibliotek testów jednostkowych dla języka Visual C#, Visual Basic i Visual C++.  
  
3.  (Opcjonalnie) W **nazwa** pole tekstowe, wprowadź nazwę, którego chcesz użyć dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]jednostkowy projekt testowy.  
  
4.  (Opcjonalnie) Zmodyfikuj ścieżkę, w której chcesz utworzyć projekt, wprowadzając go w **lokalizacji** pole tekstowe, lub wybrać **Przeglądaj** przycisku.  
  
5.  (Opcjonalnie) W **rozwiązania** Nazwa pola tekstowego, wprowadź nazwę, że chcesz użyć dla rozwiązania.  
  
6.  Pozostaw **Utwórz katalog rozwiązania** opcja wybrana i wybierz **OK** przycisku.  
  
     ![Biblioteka testów jednostkowych dostosowane](../test/media/unit_test_win8_1.png "Unit_Test_Win8_1")  
  
     Eksplorator rozwiązań jest wypełniana z nowej [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]jednostkowy projekt testowy i edytora kodu wyświetla zatytułowany UnitTest1 testu jednostkowego domyślne.  
  
     ![Nowe dopasowane jednostkowy projekt testowy](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a>Edytuj Manifest jednostkowy projekt testowy  
 Konieczne może być Edytuj manifest jednostkowy projekt testowy w celu zapewnienia możliwości wymaganych do uruchomienia aplikacji.  
  
#### <a name="to-edit-the-unit-test-projects-uwp-application-manifest-file"></a>Aby edytować plik manifestu aplikacji platformy uniwersalnej systemu Windows jednostkowy projekt testowy  
  
1.  W Eksploratorze rozwiązań w nowym [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] jednostkowy projekt testowy, kliknij prawym przyciskiem myszy plik Package.appxmanifest i wybierz polecenie **Otwórz**.  
  
     Projektant manifestu Wyświetla do edycji.  
  
2.  W Projektancie manifestu wybierz **możliwości** kartę.  
  
3.  Na liście w obszarze **możliwości**, wybierz możliwości należy z testu jednostkowego i kod ten test, aby mieć. Na przykład wybierz **Internet** pole wyboru, jeśli wymaga testu jednostkowego i kod jest testowania muszą mieć możliwość uzyskania dostępu do Internetu.  
  
    > [!NOTE]
    >  Możliwości wybrania powinien zawierać możliwości, które są niezbędne dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] testu jednostkowego do poprawnego działania. Nigdy nie ma możliwości uwzględnienie możliwości, które nie są częścią [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji są przetestowane i zwykle powinny być podzestawem możliwości określony dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]aplikacji w ramach testu.  
  
     Aby uzyskać więcej informacji na temat projektanta manifestu, zobacz [skonfigurować pakiet aplikacji Windows 8.1 za pomocą projektanta manifestu](http://msdn.microsoft.com/Library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).  
  
     ![Manifest testów jednostkowych](../test/media/unit_test_win8_.png "Unit_Test_Win8_")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Code"></a>Kod testu jednostkowego  
  
#### <a name="to-code-the-unit-test-for-a-uwp-app"></a>Kod testu jednostkowego dla aplikacji platformy uniwersalnej systemu Windows  
  
1.  W edytorze kodu edytowanie testu jednostkowego i Dodaj potwierdzeń i logiki wymagane dla testu.  
  
     Aby uzyskać więcej informacji, zobacz w [korzystanie z klas potwierdzeń](http://go.microsoft.com/fwlink/?LinkID=224991) w bibliotece MSDN.  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Run"></a>Uruchom testy jednostkowe  
  
#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Aby skompilować rozwiązanie i uruchamianie testu jednostkowego za pomocą Eksploratora testów  
  
1.  Na **testu** menu, wybierz **Windows**, a następnie wybierz pozycję **Eksploratora testów**.  
  
     Testowanie Explorer wyświetla bez testu są wymienione.  
  
2.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
     Znajduje się teraz z testu jednostkowego.  
  
    > [!NOTE]
    >  Należy utworzyć rozwiązanie, aby zaktualizować listę testów jednostkowych w Eksploratorze testów.  
  
    > [!WARNING]
    >  Visual Studio znany problem: należy otworzyć Eksploratora testów, zanim zostanie zbudowana projektu testowego.  
  
3.  W Eksploratorze testów wybierz testu jednostkowego, który został utworzony.  
  
    > [!TIP]
    >  Eksplorator testów Link do kodu źródłowego obok **źródła:**.  
  
4.  Wybierz **uruchomić wszystkie**.  
  
     ![Eksplorator testów jednostkowych &#45; Uruchamianie testu jednostkowego](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")  
  
    > [!TIP]
    >  Możesz wybrać jeden lub więcej testów jednostkowych wymienionych w Eksploratorze i kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom wybrane testy**.  
    >   
    >  Ponadto istnieje możliwość **Debuguj zaznaczone testy**, **Otwórz testu**i użyj **właściwości** opcji.  
    >   
    >  ![Eksplorator testów jednostkowych &#45; menu kontekstowe testu UNI](../test/media/unit_test_win8_unittestexplorer_contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")  
  
     Jednostka uruchomień testów. Po zakończeniu Eksploratora testów Wyświetla stan testów, czas, który upłynął oraz link do źródła.  
  
     ![Eksplorator testów jednostkowych &#45; Test ukończony](../test/media/unit_test_win8_unittestexplorer_done.png "Unit_Test_Win8_UnitTestExplorer_Done")  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 [Channel 9: Testowanie aplikacji platformy uniwersalnej systemu Windows utworzony przy użyciu języka XAML jednostkowe](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Fora  
 [Testy jednostkowe programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="msdn-library"></a>Biblioteki MSDN  
 [Biblioteka MSDN — tworzenie i Uruchamianie testów jednostkowych dla istniejącego kodu (Visual Studio 2010)](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Tworzenie i testowanie aplikacji platformy uniwersalnej systemu Windows, za pomocą Team Foundation Build](http://msdn.microsoft.com/Library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)
