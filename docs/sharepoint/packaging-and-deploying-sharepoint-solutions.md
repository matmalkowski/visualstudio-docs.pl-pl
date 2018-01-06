---
title: "Pakowanie i wdrażanie rozwiązań programu SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c584e4951289cd813a0f1d6bcf14920bd9713436
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>Rozwiązania pakowania i wdrażania SharePoint
  Zwykle rozwiązania SharePoint jest wdrażana na serwerze programu SharePoint przy użyciu rozwiązania pliku pakietu (wsp). Organizowanie elementów projektu SharePoint w funkcji i utworzyć pakiet do wdrożenia funkcji programu SharePoint, można użyć programu Visual Studio.  
  
 Ten temat zawiera następujące informacje:  
  
-   [Tworzenie funkcji i pakietów](#Creating)  
  
-   [Funkcja i utworzenie pakietu narzędzia pomocy technicznej](#Tools)  
  
-   [Wdrażanie rozwiązań SharePoint](#Deploying)  
  
-   [Wdrażanie plików rozwiązań SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a>Tworzenie funkcji i pakietów  
 Można grupować powiązane elementy programu SharePoint w Visual Studio *funkcji*. Na przykład funkcja dla definicji listy kontaktów może zawierać wystąpienia listy i definicji listy. Można połączyć tych dwóch elementów w jednym funkcji do celów wdrożenia. Aby uzyskać więcej informacji o funkcjach, zobacz [bloków konstrukcyjnych: funkcje](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Następnie można utworzyć SharePoint pakietu rozwiązań (wsp) zawierać wiele funkcji, definicje witryny zestawów i inne pliki w jednym pakiecie, służący do przechowywania plików w formacie potrzebne do wdrożenia plików na serwerze programu SharePoint. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: rozwiązań](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a>Funkcja i utworzenie pakietu narzędzia pomocy technicznej  
 Narzędzia deweloperskie programu SharePoint w Visual Studio umożliwia szybko organizować pliki programu SharePoint w funkcji i pakietów rozwiązania łatwiejsze wdrożenia. Można użyć następujących narzędzi do konfigurowania funkcji i rozwiązań pakietu.  
  
-   Funkcja projektanta i projektanta pakietu.  
  
-   Eksploratora pakietów okna narzędzia.  
  
-   Eksplorator rozwiązań.  
  
### <a name="feature-designer-and-package-designer"></a>Funkcja projektanta i projektanta pakietów  
 Można utworzyć funkcji, ustaw zakresy i inne funkcje chcesz oznaczyć jako zależności przy użyciu narzędzia Projektant funkcji. Projektant wyświetla również końcowego pliku XML, który opisuje każdej funkcji. Aby uzyskać więcej informacji, zobacz [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Zastosuj funkcję do określonej witryny sieci Web lub grupą witryn sieci Web przez ustawienie jej *zakres* w Projektancie funkcji. Jeśli funkcja została aktywowana dla poszczególnych witryn sieci Web, funkcja działa tylko w danej witryny sieci Web. Jeśli funkcja została aktywowana dla zbioru witryn, elementy w funkcji dotyczą kolekcji całej witryny. Aby uzyskać więcej informacji, zobacz [zakresu elementu](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Jeśli funkcja Twoje opiera się na inne funkcje, możesz ustawić *funkcji zależności aktywacji* do oznaczania funkcje zależne przed udostępnieniem funkcji programu. Zależność aktywacji funkcji sprawdza, czy funkcje zależne są już aktywowana w tym zakresie. Aby uzyskać więcej informacji, zobacz [zależności aktywacji i zakres](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 W Projektancie pakietu można grupować elementy programu SharePoint w pakiecie pojedyncze rozwiązanie i skonfigurować, czy można zresetować serwera sieci Web podczas wdrażania. Aby ustawić typ serwera wdrażania, użyj **właściwości** okna. Projektant także generuje plik XML, który opisuje zawartość pakietu. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Podczas wdrażania usługi Internet Information Services (IIS) jest zatrzymana, aby skopiować pliki rozwiązania do serwera programu SharePoint. Przy użyciu projektanta pakietów w programie Visual Studio, możesz wybrać, czy serwer sieci Web powinien zostać uruchomiony ponownie. Aby skonfigurować, jeśli rozwiązanie jest wdrożone na serwerze frontonu sieci Web lub serwera aplikacji, użyj **właściwości** okna. Aby uzyskać więcej informacji, zobacz [Element rozwiązania (rozwiązanie)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Eksploratora pakietów  
 Uzupełnienie funkcji projektanta i projektanta pakietów, Eksploratora pakietów służy do grupowania plików programu SharePoint w funkcji i pakietów. Ponadto widać hierarchiczny widok projektu SharePoint pakietu, funkcje, elementów i plików. Eksploratora pakietów jest okna narzędzia, która umożliwia wykonywanie następujących zadań:  
  
-   Otwórz SharePoint — elementy projektu i plików.  
  
-   Przeciągnij i upuść jedną funkcję programu SharePoint — elementy projektu.  
  
-   Przeciągnij i upuść SharePoint — elementy projektu i funkcje z jednego pakietu.  
  
-   Dodawanie nowych funkcji do pakietu.  
  
-   Otwórz projektanta funkcji lub pakietu.  
  
-   Sprawdź poprawność funkcji i pakietów.  
  
 Narzędzia programistyczne programu SharePoint w Visual Studio ma reguł sprawdzania poprawności do zapewnienia, że pakietu rozwiązania jest poprawnie sformatowany. Ponadto zasady Sprawdź plik rozwiązania WSP można pomyślnie wdrożone i aktywowana na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat schematu XML dla funkcji, zobacz [schematy funkcji](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Do systemu projektu SharePoint można dodać funkcji niestandardowej oraz zasady walidacji pakietu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie funkcji niestandardowej oraz zasady walidacji pakietu dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Aby uzyskać więcej informacji na temat Eksploratora pakietów, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Eksplorator rozwiązań  
 Przejdź do otwierania plików projektu SharePoint, można użyć Eksploratora rozwiązań. Użyj menu kontekstowego w Eksploratorze rozwiązań, aby dodać funkcje, odbiorcy zdarzeń funkcji oraz funkcji zasobów. Ponadto można otworzyć funkcji projektantów i projektantów pakiet do konfigurowania funkcji i pakietów dla wdrożenia.  
  
##  <a name="Deploying"></a>Wdrażanie rozwiązań SharePoint  
 Po dostosowaniu funkcji i pakietów w programie Visual Studio, można utworzyć pliku wsp do wdrożenia na serwerach programu SharePoint. Visual Studio umożliwia debugowania i testowania WSP tylko na serwerze programu SharePoint na komputerze dewelopera. Aby uzyskać więcej informacji na temat wdrażania rozwiązań SharePoint na serwerze zdalnym programu SharePoint, zobacz [wdrażanie rozwiązania](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Można również dostosować procedury wdrażania na komputerze dewelopera. Aby uzyskać więcej informacji, zobacz [wdrażanie, publikowanie i uaktualnianie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a>Wdrażanie plików rozwiązań SharePoint  
 Zazwyczaj podczas dodawania elementu projektu SharePoint do rozwiązania programu SharePoint, wszystkie wymagane pliki są uwzględniane. Pliki, które mogą być kompilowana (pliki kodu) są wbudowane w zestawie danych wyjściowych rozwiązania. Jednak również należy dodać do projektu SharePoint nie można skompilować dla plików, na przykład, XML, txt lub pliki zasobów. Te pliki nie są automatycznie spakowane w rozwiązaniu. Aby upewnić się, że są one umieszczone, albo Dodaj pliki do mapowanej folderu lub elementu projektu SharePoint.  
  
 Po wdrożeniu rozwiązania pliki dodane do folderów mapowanych automatycznie są kopiowane do gałęzi programu SharePoint. Pliki dodane do elementu projektu SharePoint są wdrażane do lokalizacji, która została określona w **lokalizacja wdrożenia** na podstawie właściwości dla każdego pliku, co jest ustawieniem częściowo **typu wdrożenia** właściwości. Domyślnie **typu wdrożenia** wartość właściwości jest **NoDeployment**, co oznacza, że plik nie jest wdrażany z rozwiązaniem. Należy ustawić inną wartość dla właściwości, które można dołączyć plik w pakiecie.  
  
 Na przykład aby dodać plik XML do projektu SharePoint, wykonaj jedną z następujących czynności:  
  
-   Dodaj Folder mapowane programu SharePoint "Układów" do projektu. Spowoduje to utworzenie **Eksploratora rozwiązań** folder o nazwie **układów** mający podfolder dla projektu. Dodaj plik XML do nowego podfolderu. Domyślnie plik jest wdrażany system plików programu SharePoint, w obszarze... \TEMPLATE\LAYOUTS\\*nazwa folderu*\\. Aby uzyskać informacje o sposobie dodawania zmapowane katalogi, zobacz [porady: Dodawanie i usuwanie folderów mapowane](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Dodawanie pliku XML do folderu elementu projektu SharePoint, a następnie zmień **typu wdrożenia** właściwości pliku XML z **NoDeployment** z innym ustawieniem takich jak **RootFile** lub **ElementFile**. Odpowiednie **typu wdrożenia** ustawienie zależy od pliku i projektu. Aby uzyskać więcej informacji na temat **typu wdrożenia** właściwości ustawień, zobacz [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md).  
  
 Jeśli dodany plik nie ma zastosowania do danego projektu w rozwiązaniu, możesz dodać pusty projekt programu SharePoint do rozwiązania, a następnie dodaj dodatkowe pliki do go. Alternatywą dla wdrażania plików do programu SharePoint, zwłaszcza na bazę danych zawartości, jest dodanie modułu do projektu, a następnie dodaj pliki do modułu. Aby uzyskać więcej informacji, zobacz [przy użyciu modułów pliki dołączane w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  