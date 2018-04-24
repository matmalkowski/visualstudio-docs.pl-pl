---
title: Wskazówki — w tym pakietu NuGet w projekcie
description: W tym dokumencie opisano, jak dołączyć pakietu NuGet w projekcie Xamarin. Przeprowadzi Cię on przez wyszukiwanie i pobieranie pakietu, a także wprowadzenie do funkcji integracji IDE.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.openlocfilehash: 05762df8b06a69647c6c7a628db54ac499248374
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="including-a-nuget-package-in-your-project"></a>W tym pakietu NuGet w projekcie

NuGet jest najbardziej popularnym Menedżer pakietów dla .NET — rozwój i korzysta z wbudowanej w Visual Studio for Mac i Visual Studio w systemie Windows. Można wyszukiwać i dodawanie pakietów do projektów platformy Xamarin.iOS i platformy Xamarin.Android przy użyciu albo IDE.

Ten dokument przegląda sposobu uwzględniania pakietu NuGet w projekcie i pokazuje łańcucha narzędzia, która sprawia, że proces bezproblemowe.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet w programie Visual Studio dla komputerów Mac

Aby zademonstrować funkcje pakietu NuGet najpierw omówimy Tworzenie nowej aplikacji i dodawanie pakietu do niego. Następnie omówiono funkcje IDE, które ułatwiają zarządzanie pakietami.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Najpierw utwórz projekt o nazwie `HelloNuget` jak przedstawiono poniżej. W tym przykładzie przedstawiono szablon pojedynczego widoku aplikacji systemu iOS, ale będzie działać dowolnego typu obsługiwanych projektu:

![Utwórz nowy projekt dla systemu iOS](media/nuget-walkthrough-NewProject.png)

<a name="Adding_a_Package" class="injected"></a>

## <a name="adding-a-package"></a>Dodawanie pakietu

W projekcie, Otwórz w programie Visual Studio for Mac, kliknij prawym przyciskiem myszy **pakiety** folderu w **konsoli rozwiązania** i wybierz **Dodawanie pakietów...** :

![Dodaj nową akcję kontekstu pakietu NuGet](media/nuget-walkthrough-PackagesMenu.png)

Spowoduje to uruchomienie _Dodawanie pakietów..._  okna. Upewnij się, że rozwijanej źródła, jest ustawiony na `nuget.org`:

![Źródło listy rozwijanej](media/nuget-walkthrough-Source.png)

Gdy zostanie otwarte okno załaduje listę pakietów z domyślnego pakietu źródła: nuget.org. Początkowe wyniki wyglądają następująco:

![Lista pakietów NuGet](media/nuget-walkthrough-AddPackages1.png)

Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć określony pakiet, na przykład `azure`. Po znalezieniu pakietu, który ma zostać użyty, zaznacz go i kliknij przycisk **Dodaj pakiet** przycisk, aby rozpocząć instalację.


[Dodaj pakiet NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

Po pobraniu pakietu zostanie dodany do projektu. Rozwiązanie zmieni się w następujący sposób:

*   **Odwołania** węzeł będzie zawierać listę zestawów, które są częścią pakietu NuGet.
*   **Pakiety** węzeł Wyświetla każdego pakietu NuGet, który został pobrany. Można zaktualizować lub usunąć pakiet z tej listy.
*   A **packages.config** plik zostanie dodany do projektu. Ten plik XML służy IDE do śledzenia wersji pakietu, które są przywoływane w tym projekcie. Ten plik nie należy ręcznie modyfikować, ale należy go przechowywać w kontroli wersji. Należy pamiętać, że plik project.json mogą być używane zamiast pliku packages.config. Plik project.json jest nowy format pliku pakietu, wprowadzone w systemie 3 NuGet, który obsługuje przechodnie przywracania. Bardziej szczegółowe informacje o pliku project.json znajdują się w [dokumentacji NuGet](http://docs.microsoft.com/NuGet/Schema/Project-Json). Plik project.json musi je dodać ręcznie i projekt zamknięty i otwarty ponownie, aby plik project.json jest używany w programie Visual Studio dla komputerów Mac.

## <a name="using-nuget-packages"></a>Za pomocą pakietów NuGet

Po dodaniu pakietu NuGet i zaktualizować odwołania do projektu może programu przed interfejsy API na odwołanie do projektu.

Upewnij się, Dodaj wszelkie wymagane `using` dyrektywy na początku pliku:


    using Newtownsoft.json;

Większość NuGet zawierają dodatkowe informacje, takie jak łącze stronę README lub projekt do źródła Nuget. Łącze do tej zwykle można znaleźć w notka pakietu na stronie Dodawanie pakietów:

[Link do wyświetlenia strony projektu](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Pakietu aktualizacji

Pakiet aktualizacji może odbywać się albo w całości, klikając prawym przyciskiem myszy **pakiety** węzła, lub osobno dla każdego składnika.

Kliknij prawym przyciskiem myszy **pakiety** dostęp do menu kontekstowego:

![Menu pakietów](media/nuget-walkthrough-PackagesMenu.png)

*   **Dodawanie pakietów** — powoduje otwarcie okna, aby dodać więcej pakietów do projektu.
*   **Aktualizacja** — sprawdza serwer źródłowy dla każdego pakietu i pobiera wszystkie nowsze wersje.
*   **Przywróć** -pobiera wszystkie brakujące pakiety (bez aktualizowania istniejących pakietów do nowszych wersji).

Aktualizacja opcje przywracania są również dostępne na poziomie rozwiązania i wpływają na wszystkie projekty w rozwiązaniu. 

Użytkownik może również kliknij prawym przyciskiem myszy poszczególnych pakietów na dostęp do menu kontekstowego:

![Menu pakietów](media/nuget-walkthrough-PackageMenu.png)

*   **Numer wersji** — numer wersji jest wyłączonego elementu menu — podano tylko w celach informacyjnych.
*   **Aktualizacja** — sprawdza serwer źródłowy i pliki do pobrania nowszej wersji (jeśli istnieje).
*   **Usuń** — usuwa pakiet z tego projektu i usuwa odpowiednie zestawy z odwołania do projektu.


## <a name="adding-package-sources"></a>Dodawanie źródła pakietów

Dostępne do zainstalowania pakietów początkowo są pobierane z nuget.org. Jednak dodać innych lokalizacji pakietu dla programu Visual Studio dla komputerów Mac. Może to być przydatne w przypadku testowania własnych pakietów NuGet w fazie projektowania oraz za pośrednictwem prywatnego serwera NuGet wewnątrz firmy lub organizacji.

W programie Visual Studio dla komputerów Mac, przejdź do **programu Visual Studio > Preferencje... > NuGet > źródeł** do wyświetlania i edytowania listy źródeł pakietów. Należy pamiętać, że źródła można (określony przez adres URL) serwera zdalnego lub katalogiem lokalnym. 

![Źródła pakietów](media/nuget-walkthrough-PackageSource.png)

Kliknij przycisk **Dodaj** do konfigurowania nowego źródła. Wprowadź przyjazną nazwę i adres URL (lub ścieżki pliku) do źródła pakietu. Jeśli źródło jest bezpiecznym serwerem sieci web, wprowadź nazwę użytkownika i hasło, a także, w przeciwnym razie pozostaw puste te wpisy:

![Dodawanie źródła pakietów](media/nuget-walkthrough-PackageSource2.png)

Następnie można wybrać różne źródła podczas wyszukiwania dla pakietów:

![Dodawanie źródła pakietów](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Kontrola wersji

W tym artykule omówiono dokumentacji NuGet [bez zatwierdzania pakietów do kontroli źródła przy użyciu narzędzia NuGet](https://docs.microsoft.com/nuget/consume-packages/packages-and-source-control). Jeśli nie chcesz przechowywać pliki binarne i nieużywanych informacji w kontroli źródła, można skonfigurować programu Visual Studio for Mac automatycznie przywrócić pakietów z serwera. Oznacza to, że jeśli dewelopera pobiera projektu z kontroli źródła po raz pierwszy, Visual Studio for Mac automatycznie pobierze i zainstaluje wymagane pakiety.

![Automatyczne przywracanie pakietów](media/nuget-walkthrough-AutoRestore.png)

Zapoznaj się z dokumentacją formantu określonego źródła informacji na temat do wykluczenia `packages` katalogu z śledzone.

