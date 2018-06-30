---
title: Pakowanie i wdrażanie rozwiązań programu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2421a1f39f2969563bc10a43367936ae499fac30
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120330"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Pakiet i wdrażanie rozwiązań SharePoint
  Zwykle rozwiązania SharePoint jest wdrażana na serwerze programu SharePoint przy użyciu rozwiązania pliku pakietu (wsp). Organizowanie elementów projektu SharePoint w funkcji i utworzyć pakiet do wdrożenia funkcji programu SharePoint, można użyć programu Visual Studio.  
  
 Ten temat zawiera następujące informacje:  
  
-   [Tworzenie funkcji i pakietów](#Creating)  
  
-   [Funkcja i utworzenie pakietu narzędzia pomocy technicznej](#Tools)  
  
-   [Wdrażanie rozwiązań SharePoint](#Deploying)  
  
-   [Wdrażanie plików rozwiązań SharePoint](#DeployingFiles)  
  
## <a name="create-features-and-packages"></a>Tworzenie funkcji i pakietów
 Można grupować powiązane elementy programu SharePoint w Visual Studio *funkcji*. Na przykład funkcja dla definicji listy kontaktów może zawierać wystąpienia listy i definicji listy. Można połączyć tych dwóch elementów w jednym funkcji do celów wdrożenia. Aby uzyskać więcej informacji o funkcjach, zobacz [bloków konstrukcyjnych: funkcje](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Następnie można utworzyć pakietu rozwiązania programu SharePoint (*WSP*) zawierać wiele funkcji, lokacji definicje, zestawy i inne pliki w jeden pakiet, który przechowuje pliki w formacie potrzebne do wdrożenia plików do programu SharePoint serwer. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: rozwiązań](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
## <a name="feature-and-packaging-tool-support"></a>Funkcja i obsługę narzędzia pakowania
 Narzędzia deweloperskie programu SharePoint w Visual Studio umożliwia szybko organizować pliki programu SharePoint w funkcji i pakietów rozwiązania łatwiejsze wdrożenia. Można użyć następujących narzędzi do konfigurowania funkcji i rozwiązań pakietu.  
  
-   Funkcja projektanta i projektanta pakietu.  
  
-   Eksploratora pakietów okna narzędzia.  
  
-   Eksplorator rozwiązań.  
  
### <a name="feature-designer-and-package-designer"></a>Funkcja projektanta i projektanta pakietów
 Można utworzyć funkcji, ustaw zakresy i inne funkcje chcesz oznaczyć jako zależności przy użyciu narzędzia Projektant funkcji. Projektant wyświetla również końcowego pliku XML, który opisuje każdej funkcji. Aby uzyskać więcej informacji, zobacz [funkcji tworzenia SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Zastosuj funkcję do określonej witryny sieci Web lub grupą witryn sieci Web przez ustawienie jej *zakres* w Projektancie funkcji. Jeśli funkcja została aktywowana dla poszczególnych witryn sieci Web, funkcja działa tylko w danej witryny sieci Web. Jeśli funkcja została aktywowana dla zbioru witryn, elementy w funkcji dotyczą kolekcji całej witryny. Aby uzyskać więcej informacji, zobacz [zakresu elementu](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Jeśli funkcja Twoje opiera się na inne funkcje, możesz ustawić *funkcji zależności aktywacji* do oznaczania funkcje zależne przed udostępnieniem funkcji programu. Zależność aktywacji funkcji sprawdza, czy funkcje zależne są już aktywowana w tym zakresie. Aby uzyskać więcej informacji, zobacz [zależności aktywacji i zakres](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 W Projektancie pakietu można grupować elementy programu SharePoint w pakiecie pojedyncze rozwiązanie i skonfigurować, czy można zresetować serwera sieci Web podczas wdrażania. Aby ustawić typ serwera wdrażania, użyj **właściwości** okna. Projektant także generuje plik XML, który opisuje zawartość pakietu. Aby uzyskać więcej informacji, zobacz [pakietów rozwiązania SharePoint Utwórz](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Podczas wdrażania usługi Internet Information Services (IIS) jest zatrzymana, aby skopiować pliki rozwiązania do serwera programu SharePoint. Przy użyciu projektanta pakietów w programie Visual Studio, możesz wybrać, czy serwer sieci Web powinien zostać uruchomiony ponownie. Aby skonfigurować, jeśli rozwiązanie jest wdrożone na serwerze frontonu sieci Web lub serwera aplikacji, użyj **właściwości** okna. Aby uzyskać więcej informacji, zobacz [Element rozwiązania (rozwiązanie)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Eksploratora pakietów  
 Uzupełnienie funkcji projektanta i projektanta pakietów, Eksploratora pakietów służy do grupowania plików programu SharePoint w funkcji i pakietów. Ponadto widać hierarchiczny widok projektu SharePoint pakietu, funkcje, elementów i plików. Eksploratora pakietów jest okna narzędzia, która umożliwia wykonywanie następujących zadań:  
  
-   Otwórz SharePoint — elementy projektu i plików.  
  
-   Przeciągnij i upuść jedną funkcję programu SharePoint — elementy projektu.  
  
-   Przeciągnij i upuść SharePoint — elementy projektu i funkcje z jednego pakietu.  
  
-   Dodawanie nowych funkcji do pakietu.  
  
-   Otwórz projektanta funkcji lub pakietu.  
  
-   Sprawdź poprawność funkcji i pakietów.  
  
 Narzędzia programistyczne programu SharePoint w Visual Studio ma reguł sprawdzania poprawności do zapewnienia, że pakietu rozwiązania jest poprawnie sformatowany. Ponadto zasady upewnij się, że *WSP* plik rozwiązania można pomyślnie wdrożyć i aktywować na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat schematu XML dla funkcji, zobacz [schematy funkcji](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Do systemu projektu SharePoint można dodać funkcji niestandardowej oraz zasady walidacji pakietu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Aby uzyskać więcej informacji na temat Eksploratora pakietów, zobacz [porady: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Eksplorator rozwiązań
 Przejdź do otwierania plików projektu SharePoint, można użyć Eksploratora rozwiązań. Użyj menu kontekstowego w Eksploratorze rozwiązań, aby dodać funkcje, odbiorcy zdarzeń funkcji oraz funkcji zasobów. Ponadto można otworzyć funkcji projektantów i projektantów pakiet do konfigurowania funkcji i pakietów dla wdrożenia.  
  
## <a name="deploy-sharepoint-solutions"></a>Wdrażanie rozwiązań SharePoint
 Po dostosowaniu funkcji i pakietów w programie Visual Studio, można utworzyć *WSP* plików do wdrożenia na serwerach programu SharePoint. Można użyć programu Visual Studio do debugowania i testowania. *wsp* tylko na serwerze programu SharePoint na komputerze dewelopera. Aby uzyskać więcej informacji na temat wdrażania rozwiązań SharePoint na serwerze zdalnym programu SharePoint, zobacz [wdrażanie rozwiązania](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Można również dostosować procedury wdrażania na komputerze dewelopera. Aby uzyskać więcej informacji, zobacz [wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
## <a name="deploy-files-in-sharepoint-solutions"></a>Wdrażanie plików rozwiązań SharePoint
 Zazwyczaj podczas dodawania elementu projektu SharePoint do rozwiązania programu SharePoint, wszystkie wymagane pliki są uwzględniane. Pliki, które mogą być kompilowana (pliki kodu) są wbudowane w zestawie danych wyjściowych rozwiązania. Jednak również może być konieczne Dodaj nie można skompilować dla plików, na przykład *.xml*, *.txt*, lub pliki zasobów, do projektu programu SharePoint. Te pliki nie są automatycznie spakowane w rozwiązaniu. Aby upewnić się, że są one umieszczone, albo Dodaj pliki do mapowanej folderu lub elementu projektu SharePoint.  
  
 Po wdrożeniu rozwiązania pliki dodane do folderów mapowanych automatycznie są kopiowane do gałęzi programu SharePoint. Pliki dodane do elementu projektu SharePoint są wdrażane do lokalizacji, która została określona w **lokalizacja wdrożenia** na podstawie właściwości dla każdego pliku, co jest ustawieniem częściowo **typu wdrożenia** właściwości. Domyślnie **typu wdrożenia** wartość właściwości jest **NoDeployment**, co oznacza, że plik nie jest wdrażany z rozwiązaniem. Należy ustawić inną wartość dla właściwości, które można dołączyć plik w pakiecie.  
  
 Na przykład, aby dodać *.xml* plik do projektu SharePoint, wykonaj jedną z następujących działań:  
  
-   Dodaj Folder mapowane programu SharePoint "Układów" do projektu. Spowoduje to utworzenie **Eksploratora rozwiązań** folder o nazwie **układów** mający podfolder dla projektu. Dodaj *.xml* plików do nowego podfolderu. Domyślnie plik jest wdrożony w systemie plików programu SharePoint, w obszarze *... \TEMPLATE\LAYOUTS\\\<nazwa folderu >*. Aby uzyskać informacje o sposobie dodawania zmapowane katalogi, zobacz [porady: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Dodaj *.xml* pliku do folderu elementu projektu SharePoint, a następnie zmień **typu wdrożenia** właściwość *.xml* plik z **NoDeployment**  z innym ustawieniem takich jak **RootFile** lub **ElementFile**. Odpowiednie **typu wdrożenia** ustawienie zależy od pliku i projektu. Aby uzyskać więcej informacji na temat **typu wdrożenia** właściwości ustawień, zobacz [rozwiązań SharePoint opracowanie](../sharepoint/developing-sharepoint-solutions.md).  
  
 Jeśli dodany plik nie ma zastosowania do danego projektu w rozwiązaniu, możesz dodać pusty projekt programu SharePoint do rozwiązania, a następnie dodaj dodatkowe pliki do go. Alternatywą dla wdrażania plików do programu SharePoint, zwłaszcza na bazę danych zawartości, jest dodanie modułu do projektu, a następnie dodaj pliki do modułu. Aby uzyskać więcej informacji, zobacz [Użyj modułów podczas dołączania plików rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
