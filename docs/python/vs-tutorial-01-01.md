---
title: "Praca z języka Python w programie Visual Studio, krok 1 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: a9dbfba9-192a-42b2-8f6f-0c5f0b4a605b
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: bdffa1de6b291c1c4e0a7b99708c353deffda5e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-python-in-visual-studio"></a>Praca z języka Python w programie Visual Studio

Python to niezawodne, elastyczne, łatwe dowiedzieć się, bez używania we wszystkich systemach operacyjnych i obsługiwanych przez społeczność deweloperów silne i wiele bibliotek wolnego popularnych język programowania. Język obsługuje wszystkie środki projektowanie, łącznie z aplikacji sieci web, usług sieci web, aplikacji klasycznych, skrypty i obliczanie naukowe i jest używany przez wiele uczelni, służące zwykłych deweloperzy i deweloperów podobne.

Visual Studio obsługuje najwyższej jakości języka Python. W tym samouczku prowadzi użytkownika przez następujące kroki:

- [Krok 0: instalacji](vs-tutorial-01-00.md)
- [Krok 1: Tworzenie projektu języka Python (w tym temacie)](#step-1-create-a-new-python-project)
- [Krok 2: Zapisywanie i wykonywanie kodu, aby zobaczyć Visual Studio IntelliSense w miejscu pracy](vs-tutorial-01-02.md)
- [Krok 3: Tworzenie więcej kodu w oknie interaktywny REPL](vs-tutorial-01-03.md)
- [Krok 4: Uruchom program ukończone w debugerze programu Visual Studio](vs-tutorial-01-04.md)
- [Krok 5: Instalowanie pakietów i zarządzania nimi środowiska Python](vs-tutorial-01-05.md)
- [Krok 6: Praca z usługą Git](vs-tutorial-01-06.md)

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 z obciążeniem Python zainstalowane. Zobacz [krok 0](vs-tutorial-01-00.md) instrukcje.

## <a name="step-1-create-a-new-python-project"></a>Krok 1: Utwórz nowy projekt języka Python

A *projektu* jest jak Visual Studio zarządza wszystkie pliki, które w celu utworzenia pojedynczą aplikacją, łącznie z kodu źródłowego, zasobów, konfiguracji i tak dalej. Projekt rozmieszczony i obsługuje relacji między projektu wszystkie pliki, a także zasobów zewnętrznych, które są wspólne dla wielu projektów. Tak projektu Zezwalaj aplikacji bez wysiłku rozwiń oraz wzrostu znacznie łatwiejsze niż po prostu zarządzanie relacjami projektu w folderach ad hoc, skrypty, pliki tekstowe i nawet własnych zdanie.

W tym samouczku rozpoczynać prostego projektu zawierającego jeden pusty plik kodu.

1. W programie Visual Studio, wybierz **Plik > Nowy > Projekt** (Ctrl + Shift + N), co spowoduje uruchomienie **nowy projekt** okna dialogowego. W tym miejscu możesz przeglądać szablony w różnych językach, następnie wybierz jedną dla projektu i określ, gdzie umieszcza pliki w Visual Studio.

1. Zaznacz, aby wyświetlić szablony Python **Szablony > inne języki > Python** w lewej lub wyszukiwanie "Python". Używanie wyszukiwania jest doskonałym sposobem znaleźć szablonu, jeśli nie pamiętasz lokalizacji w drzewie języków.

    ![Okno dialogowe nowego projektu z projektami Python pokazano](media/vs-getting-started-python-01-new-project.png)

1. Zwróć uwagę, jak obsługę języka Python w Visual Studio zawiera szereg szablony projektów, w tym aplikacji sieci web przy użyciu struktury Bottle, Flask i Django. Na potrzeby tego przewodnika jednak Zacznijmy pusty projekt. 

1. Wybierz **aplikacji Python** szablonu, określ nazwę dla projektu i wybierz **OK**. 

1. Po kilku chwilach Visual Studio zawiera struktury projektu w **Eksploratora rozwiązań** okna (1). Domyślny plik kodu jest otwarty w edytorze, (2). Aby wyświetlić dodatkowe informacje dla dowolnego elementu wybranego w Eksploratorze rozwiązań, jego dokładnej lokalizacji na dysku w tym również zostanie wyświetlone okno właściwości [3].
 
    ![Eksplorator rozwiązań z projektów języka Python](media/vs-getting-started-python-02-windows.png)
 
1. Zapoznaj się z Eksploratora rozwiązań, czyli gdzie przeglądać pliki i foldery w projekcie może chwilę potrwać.
    
    ![Eksplorator rozwiązań rozwinięty, ukazując różnych funkcji](media/vs-getting-started-python-03-solution-explorer.png)

    (1) wyróżnione czcionką pogrubioną jest projekt używa tej nazwy, podany w oknie dialogowym Nowy projekt. Na dysku, ten projekt jest reprezentowana przez `.pyproj` pliku w folderze projektu.

    (2) na najwyższym poziomie jest *rozwiązania*, która domyślnie ma taką samą nazwę jak projektu. Rozwiązanie reprezentowane przez `.sln` plików na dysku, to kontener dla jednego lub więcej projektów powiązanych. Na przykład rozszerzenia C++ podczas pisania aplikacji Python, projektu C++ może znajdować się w tym samym rozwiązaniu. Rozwiązanie może także zawierać projekt usługi sieci web, wraz z projektów dla programów dedykowanych testu. 

    (3) w obszarze projektu Zobacz pliki źródłowe, w tym przypadku tylko jeden `.py` pliku. Wybranie pliku powoduje wyświetlenie jej właściwości w oknie właściwości. Dwukrotne kliknięcie pliku spowoduje otwarcie go w dowolnie wybrany sposób jest odpowiedni dla tego pliku.

    (4) również w projekcie jest **środowiska Python** węzła. Po rozwinięciu, zobaczysz dostępne tłumaczy Python, które są dostępne dla Ciebie. Rozwiń węzeł interpreter, aby zobaczyć bibliotek, które są zainstalowane w tym środowisku [5].

    Kliknij prawym przyciskiem myszy dowolny węzeł lub elementu w Eksploratorze rozwiązań, aby uzyskać dostęp do menu odpowiednich poleceń. Na przykład **zmienić** polecenie umożliwia zmianę nazwy węzła lub elementu, łącznie z projektu i rozwiązania.
    
## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Zapisywanie i uruchamiania kodu](vs-tutorial-01-02.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Projekty języka Python w programie Visual Studio](python-projects.md).
- [Dowiedz się więcej o języku Python w python.org](https://www.python.org)
- [Python dla początkujących](https://www.python.org/about/gettingstarted/) (python.org)
- [Bezpłatne kursy Python w Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Górny Python pytania wirtualna Akademia firmy Microsoft](https://aka.ms/mva-top-python-questions)
