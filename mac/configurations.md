---
title: "Ogólne informacje o konfiguracjach kompilacji"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: e435418c0c77f1577e9db8ab35d76d6bd54f8447
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="understanding-build-configurations"></a>Opis konfiguracji kompilacji

## <a name="project-build-configurations"></a>Konfiguracje kompilacji projektu 

Projekty może mieć wiele konfiguracji i przełączania między nimi umożliwia różne wyniki podczas kompilacji. Na przykład podczas korzystania z konfiguracji debugowania, dane wyjściowe uwzględni profilowanie symbole, dzięki czemu debugera do rozpoznania nazwy funkcji, parametry lub zmienne z ślad stosu awaria aplikacji. Przy użyciu konfiguracji debugowania, jednak prowadzi do rozmiaru pliku nadmuchany i dlatego nie będzie idealne dla aplikacji przeznaczonych do dystrybucji.

Każdej z platform będzie mieć określone konfiguracje dla jego kompilacji. Programowanie Xamarin.Android zawsze będą mieć wyłącznie debugowania lub wersji konfiguracji. Xamarin.iOS ma więcej konfiguracje. Nowsze systemu iOS, które projekty będzie mieć tylko debugowania lub wersji konfiguracji, ale te opcje można ustawić dla dowolnego zainstalowanego symulatorze lub urządzenia.

## <a name="solution-configurations"></a>Konfiguracje rozwiązania

Podobnie konfiguracje projektu konfiguracje rozwiązania są używane do tworzenia konfiguracje niestandardowe dla całego projektu. Za pomocą **mapowania konfiguracji** w obszarze **kompilacji > konfiguracje** elementu, można przypisać konfiguracji docelowej, dla każdego elementu rozwiązania, jak przedstawiono poniżej:


 ![Opcje mapowania konfiguracji](media/projects-and-solutions-image3.png)

Aby uzyskać więcej informacji, zapoznaj się [programu Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) wideo przez James Montemagno.

## <a name="run-configuration"></a>Uruchom konfigurację

W poprzednich wersjach programu Xamarin Studio, można wybrać możliwość ustawienia projektu jako **projekt startowy**, która jest projekt, który uruchomienia/debugowania korzystając z polecenia globalnego uruchomienia/debugowania. To była wskazywana przez bold krój czcionki dla nazwy projektu w konsoli do projektu.

W programie Visual Studio dla komputerów Mac, a ustawienie Projekt startowy, można ustawić _Uruchom konfigurację_. Konfiguracje działania są przedstawione na liście rozwijanej na pasku narzędzi, obok selektora konfigurację kompilacji, jak przedstawiono poniżej:

 ![Uruchom rozwijanej konfiguracji](media/projects-and-solutions-image8.png)

Konfigurację uruchomieniową to zestaw opcji wykonywania z nazwą i kilka konfiguracji, które są zdefiniowane w projekcie do różnych celów. Konfiguracje wykonywania są definiowane na poziomie projektu i domyślnie zostaną utworzone automatycznie dla każdego projektu pliku wykonywalnego, chociaż jest możliwie dodanie maksymalnie potrzebne. Niektóre typy projektów automatycznie wygenerować dodatkowe konfiguracje wykonywania. Na przykład może generować projekty watchOS _konfiguracji dostępu i powiadomień._ 
 
Konfiguracje mogą współużytkowane z innymi deweloperami (w takim przypadku konfiguracje będą przechowywane w pliku .csproj) lub przechowywane lokalnie (w takim przypadku będą przechowywane w pliku .user).

### <a name="android-run-configurations"></a>Uruchom konfiguracji systemu android
 
Uruchom konfiguracje dla projektów dla systemu Android umożliwiają określenie, które działania, usługi lub odbiornika emisji do uruchomienia podczas uruchamiania lub debugowania projektu. Można przekazywać konwersji dodatkowe dane i Ustaw flagi konwersji, aby można było składniki warunkach różnych uruchomienia testu.

Działania innych niż `MainLauncher` musi mieć `Exported=true` dodać atrybut działania do debugowania na urządzeniu fizycznym lub zdefiniowano konwersji filtrów.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Przykładowe dane, które mogą być uwzględnione w konfiguracji uruchomienia

Na poniższej liście podano przykładowe dane, które mogłyby zostać włączone konfiguracje wykonywania:

* Regularne .NET projektu
    * Alternatywne uruchamianie aplikacji
    * Początek argumentów
    * Katalog roboczy
    * Zmienne środowiskowe
    * Opcje środowiska uruchomieniowego mono (ma być używany tylko wtedy, gdy jest uruchomiona na Mono)
* Projekt systemu android
    * Punkt wejścia (działania, usługi, odbiorcy)
    * Argumenty metody konwersji i danych
* Projekt dla systemu iOS
    * Tryb (normalny, pobieranie w tle)
* Projekt rozszerzenia systemu iOS
    * Uruchamianie aplikacji: domyślna lub niestandardowego
* WatchKit projektu
    * Tryb (pierwszy rzut oka, powiadomienia)
    * Ładunek powiadomienia
