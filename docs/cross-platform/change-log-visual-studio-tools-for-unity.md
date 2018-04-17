---
title: Zmienianie dziennika (Visual Studio Tools for Unity, system Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/23/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 4d7f965cd2a0cd34ea3cb889f25809d32bee2270
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Dziennik zmian (Visual Studio Tools for Unity, system Windows)
Visual Studio Tools for Unity dziennika zmian.

## <a name="3605"></a>3.6.0.5
 Wydanych 2018-03-13

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę dla generatora nowego projektu w Unity 2018.1

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Stałe obsługi uszkodzony stanów z niestandardowych projektów.

-   **Debuger:**

    -   Stałe ustawienie następnej instrukcji.

## <a name="3604"></a>3.6.0.4
 Wydanych 2018-03-05

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Wykrywanie wersji Mono stałej.

-   **Integracja:**

    -   Stałe problemy dotyczące synchronizacji z 2018.1 i wtyczki aktywacji.

## <a name="3603"></a>3.6.0.3
 Wydanych 2018-02-23

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę dla platformy .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Stały wykrywania framework docelowej platformy Unity.

-   **Debuger:**

    -   Stałe podziału na wyjątki, które są generowane poza usercode.

## <a name="3602"></a>3.6.0.2
 Wydanych 2018-02-07

### <a name="new-features"></a>Nowe funkcje

-   **Integracja:**

    -   Zaktualizuj powierzchni interfejsu API UnityMessage dla 2017.3.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Ponownie ładować tylko projekty na zewnętrzne zmiany (po zastosowaniu ograniczania).
 
## <a name="3601"></a>3.6.0.1
 Wydanych 2018-01-24

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Stałej pdb automatycznego do konwersji symbolu debugowania pliku mdb.
    
    -   Wywołanie pośrednie stałym EditorPrefs.GetBool wpływające na Inspektor podczas próby zmiany rozmiaru tablicy.
 
## <a name="3600"></a>3.6.0.0
 Wydanych 2018-01-10

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę 2018.1 MonoIsland odwołanie modelu.

-   **Ocena:**

    -   Dodano obsługę $exception identyfikator.

-   **Debuger:**

    -   Dodano obsługę atrybutów DebuggerHidden/DebuggerStepThrough o nowe środowisko uruchomieniowe platformy Unity.
    
-   **Kreatorzy:**

    -   Wprowadzenie "Najnowszej" wersji dla kreatorów.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Stałe obliczeń identyfikator guid projektu dla projektów player.

-   **Debuger:**

    -   Stałe wyścigu podczas obsługi zdarzenia podziału.
    
-   **Kreatorzy:**

    -   Odśwież kontekst roslyn przed wstawieniem metody.

## <a name="3503"></a>3.5.0.3
 Wydanych 2018-01-09.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Stałej pdb automatycznego do konwersji symbolu debugowania pliku mdb.

## <a name="3502"></a>3.5.0.2
 Wydanych 2017 12-04-

### <a name="new-features"></a>Nowe funkcje

-   **Integracja:**

    -   Projekty Unity są teraz automatycznie ponownie ładowane w programie Visual Studio po dodaniu skryptu do środowiska Unity lub jego usunięciu.

-   **Debuger:**

    -   Dodano możliwość użycia Mono debuger współużytkowane przez Xamarin i Visual Studio for Mac do debugowania Edytor platformy Unity.

    -   Dodano obsługę plików symboli debugowania przenośnej.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja:**

    -   Naprawić problemy z instalacją zależności.

    -   Menu Pomoc stałym Unity interfejsu API nie są wyświetlane.

-   **Generowanie projektu:**

    -   Generowanie projektu player stały podczas pracy z gier platformy uniwersalnej systemu Windows z zapleczem IL2CPP/.NET 4.6.

    -   Stałe rozszerzenie .dll dodatkowe błędnie dodane do nazwy pliku zestawu.

    -   Stałe użycie określonego projektu interfejsu API poziom zgodności zamiast jedną globalnego.

    -   Nie Wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, zgodnie z wartością domyślną jest teraz 'true'.

## <a name="3402"></a>3.4.0.2
 Wydanych 2017-09-19

### <a name="new-features"></a>Nowe funkcje

-   **Generowanie projektu:**

    -   Dodano obsługę assembly.json jednostki kompilacji.

    -   Zatrzymać kopiowanie Unity zestawów w folderze projektu.

-   **Debuger:**

    -   Dodano obsługę ustawienie następnej instrukcji z nowe środowisko uruchomieniowe platformy Unity.

    -   Dodano obsługę dla typu Decimal o nowe środowisko uruchomieniowe platformy Unity.

    -   Dodano obsługę niejawnej/jawnej konwersji.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ocena:**

    -   Tworzenie tablicy o ustalonym o rozmiarze niejawnej.

    -   Stałe kompilatora generowane elementy zmiennych lokalnych.

-   **Generowanie projektu:**

    -   Stałe odwołanie do Microsoft.CSharp 4.6 poziom interfejsu API.

## <a name="3302"></a>3.3.0.2
 Wydanych 2017-08-15

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Stałe generowania rozwiązania Visual Studio na Unity 5.5 i poprzednich wersjach.

## <a name="3300"></a>3.3.0.0
 Wydanych 2017-08-14

### <a name="new-features"></a>Nowe funkcje

-   **Ocena:**

    -   Dodano obsługę tworzenia struktury o nowe środowisko uruchomieniowe platformy Unity.

    -   Dodano obsługę minimalist wskaźników.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ocena:**

    -   Stała wywołania metody na nim elementów podstawowych.

    -   Pole stałej oceny z typami oznaczony atrybutem BeforeFieldInit.

    -   Stałego połączenia z systemem innym niż obsługiwany z operatorami dwuargumentowymi (odejmowanie).

    -   Rozwiązane problemy podczas dodawania elementów do czujki programu Visual Studio.

-   **Generowanie projektu:**

    -   Stałych Nazwa odwołania do zestawu za pomocą mcs.rsp plików.

    -   Stałe zdefiniowane z poziomu interfejsu API.

## <a name="3200"></a>3.2.0.0
 Wydanych 2017-05-10

### <a name="new-features"></a>Nowe funkcje

-   **Instalator:**

    -   Dodano obsługę czyszczenia pamięci podręcznej MEF.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Edytor kodu:**

    -   Stałe klasyfikacji/zakończenia z atrybutów niestandardowych.

    -   Stałe migotanie komunikatów, Unity.

## <a name="3100"></a>3.1.0.0
 Wydanych 2017-04-07

### <a name="new-features"></a>Nowe funkcje

-   **Debuger:**

    -   Dodano obsługę nowe środowisko uruchomieniowe Unity (z .NET 4.6 / zgodność języka C# 6).

-   **Generowanie projektu:**

    -   Dodano obsługę profilu .NET 4.6.

    -   Dodano obsługę mcs.rsp plików.

    -   Zawsze włączaj przełącznika niebezpieczny kompilacji stosowania Unity 5.6.

    -   Dodano obsługę Generowanie projektu "Player" gdy przy użyciu Sklepu Windows platformy i il2cpp wewnętrznej bazy danych.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Edytor kodu:**

    -   Stałe położenia karetki po wstawieniu metodę z automatycznego uzupełniania.

-   **Generowanie projektu:**

    -   Usunięto zestawu wersji przetwarzania końcowego.

## <a name="3001"></a>3.0.0.1
 Wydanych 2017-03-07

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Ta wersja zawiera wszystkie nowe funkcje i poprawki wprowadzone w systemie 2.8.x serii.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 w wersji zapoznawczej 3
 Wydanych 2017-01-25

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Stała regresji, gdy projekty wtyczek w przypadku, gdy dwa razy, do których odwołuje się najpierw jako binarne DLL następnie jako projekt odniesienie.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 preview 2
 Wydanych 2017-01-23

### <a name="bug-fixes"></a>Poprawki błędów

-   **Edytor kodu:**

    -   Stała awarii podczas uruchamiania deklaracji atrybutu bez ukończenia nawiasu klamrowego.

-   **Debuger:**

    -   Punkty przerwania funkcji stałej z procedury wspólnej w obszarze nowe Unity kompilatora/środowisko uruchomieniowe.

    -   Dodano ostrzeżenie w przypadku unbindable punktu przerwania (po znalezieniu nie odpowiedniej lokalizacji źródłowej).

-   **Generowanie projektu:**

    -   Generowanie stałym csproj specjalne/zlokalizowanych znaków.

    -   Stałe odwołań poza zasobów, takich jak biblioteki (takich jak Facebook zestawu SDK).

-   **Różne:**

    -   Dodano wyboru być uruchamiany po zainstalowaniu lub odinstalowaniu Unity.

    -   Przełączono HTTPS pod kątem zdalnego dokumentacji Unity.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 w wersji zapoznawczej
 Wydanych 2016-11-17

### <a name="new-features"></a>Nowe funkcje

-   **Ogólne:**

    -   Dodano obsługę Instalator Visual Studio 2017 r.

    -   Dodano obsługę rozszerzenia programu Visual Studio 2017 r.

    -   Obsługa dodanych lokalizacji.

-   **Edytor kodu:**

    -   Dodano C# IntelliSense dla Unity wiadomości.

    -   Dodano C# kodu zabarwienie Unity komunikatów.

-   **Debuger:**

    -   Dodano obsługę `is`, `as`, bezpośrednie rzutowania, `default`, `new` wyrażenia.

    -   Dodano obsługę wyrażenia concat parametrów.

    -   Dodano obsługę szesnastkowe wyświetlania wartości będące liczbami całkowitymi.

    -   Dodano obsługę tworzenia nowe zmienne tymczasowe (instrukcje).

    -   Dodano obsługę niejawne konwersje pierwotnych.

    -   Dodawane lepiej komunikaty o błędach podczas typu jest oczekiwany lub nie można odnaleźć.

-   **Generowanie projektu:**

    -   Usunięte z sufiksem CSharp z nazwy projektu.

    -   Usunięto odwołanie do pliku cele szeroki msbuild systemu.

-   **Kreatorzy:**

    -   Dodano obsługę dla typów innych niż zachowania, takich jak edytor lub EditorWindow Unity wiadomości.

    -   Przełączenie do Roslyn wstrzyknąć i format wiadomości Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Debuger:**

    -   Stałe usterki awarii Unity podczas oceny typów ogólnych.

    -   Stałe obsługi typów dopuszczających wartości zerowe.

    -   Stałe obsługi wyliczenia.

    -   Stałe obsługi typów zagnieżdżonych elementów członkowskich.

    -   Stały dostęp indeksatora kolekcji.

    -   Stałe obsługę debugowania iteratora ramki z nowy kompilator języka C#.

-   **Generowanie projektu:**

    -   Stały błąd uniemożliwił kompilacji, jeśli celem player Unity sieci Web.

    -   Stały usterki, który uniemożliwił kompilacji podczas kompilowania skryptu z sieci web zakodowane nazwy pliku.

## <a name="2300"></a>2.3.0.0
 Wydanych 2016-07-14

### <a name="new-features"></a>Nowe funkcje

-   **Ogólne:**

    -   Dodano możliwość wyłączenia Unity konsoli Dzienniki w Visual Studio na liście błędów.

    -   Dodano opcję Zezwalaj na właściwości wygenerowanego projektu do zmodyfikowania.

-   **Debuger:**

    -   Dodano Text, XML, HTML i JSON ciąg wizualizatorów.

-   **Kreatorzy:**

    -   Dodaje, brak MonoBehaviors.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ogólne:**

    -   Stałe konflikt z ReSharper, który uniemożliwił formanty ustawień programu Visual Studio będą wyświetlane.

    -   Stałe konflikt z platformą Xamarin, który uniemożliwił debugowania w niektórych przypadkach.

-   **Debuger:**

    -   Rozwiązano problem powodujący Visual Studio zawiesza się podczas debugowania.

    -   Rozwiązano problem z punkty przerwania funkcji w programie Visual Studio 2015.

    -   Stałe wyrażenie kilka problemów oceny.

## <a name="2200"></a>2.2.0.0
 Wydanych 2016-02-04

### <a name="new-features"></a>Nowe funkcje

-   **Kreatorzy:**

    -   Dodano inteligentne wyszukiwania w **MonoBehavior wdrożenie** kreatora.

    -   Dokonano kreatorów kontekstu pamiętać; na przykład NetworkBehavior wiadomości są dostępne tylko podczas pracy z NetworkBehavior.

    -   Dodano obsługę wiadomości NetworkBehavior w kreatorze.

-   **INTERFEJS UŻYTKOWNIKA:**

    -   Dodano opcję, aby skonfigurować widoczność MonoBehavior wiadomości.

    -   Usunięte stron właściwości programu Visual Studio, które nie są ważnego do projektów platformy Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Stałe odwołania do UnityEngine i UnityEditor na Unity 4.6.

    -   Stałe Generowanie plików projektu, gdy Unity działa w systemie OSX.

    -   Stałe obsługi nazwy projektu zawierające znaki hashmark (#).

    -   Ograniczone wygenerowane projekty do 4 C#.

-   **Debuger:**

    -   Rozwiązano problem z Szacowanie wyrażeń podczas debugowania w procedurze wspólnej Unity.

    -   Rozwiązano problem powodujący Visual Studio zawiesza się podczas debugowania.

-   **INTERFEJS UŻYTKOWNIKA:**

    -   Stały niezgodność z [Studio karty](https://tabsstudio.com/) rozszerzenie programu Visual Studio.

-   **Instalator:**

    -   Obsługuje instalację komputera pomocą rozszerzenia VSTU (Instalacja dla wszystkich użytkowników) przez utworzenie HKLM wpisów rejestru.

    -   Rozwiązane problemy z dezinstalacji pomocą rozszerzenia VSTU po zainstalowaniu tej samej wersji pomocą rozszerzenia VSTU wiele różnych wersji programu Visual Studio. Na przykład, jeśli pomocą rozszerzenia VSTU **2015** 2.1.0.0 i pomocą rozszerzenia VSTU **2013** 2.1.0.0 zostały zainstalowane.

## <a name="2100"></a>2.1.0.0
 Wydanych 2015-09-08

### <a name="new-features"></a>Nowe funkcje

-   Obsługa platformy Unity 5.2

### <a name="bug-fixes"></a>Poprawki błędów

-   Wyświetlanie elementów menu na Unity < 4.2

-   Komunikat o błędzie nie są wyświetlane, gdy program Visual Studio blokuje pliki intellisense XML.

-   Obsługa <\<po zmianie >> warunkowych punktów przerwania podczas warunkowego argument nie jest wartością logiczną.

-   Stałe odwołania do zestawów UnityEngine i UnityEditor dla aplikacji ze Sklepu Windows.

-   Stałe błędu przy przechodzeniu w debugerze: nie można krok ogólny wyjątek.

-   Stałej liczby trafień punkty przerwania w programie Visual Studio 2015.

## <a name="2000"></a>2.0.0.0
 Wydanych 2015-07-20

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja platformy Unity:**

    -   Stałe konwersji symboli debugowania utworzone za pomocą programu Visual Studio 2015 podczas importowania biblioteki DLL i jego symboli debugowania (PDB).

    -   Zawsze generuj pliki MDB podczas importowania biblioteki DLL i jego symboli debugowania (PDB), z wyjątkiem przypadków, gdy jest również udostępniany pliku MDB.

    -   Stałe zanieczyszczenie Unity katalogu projektu z katalogu.

    -   Stałe Generowanie odwołania do System.Xml.Link i System.Runtime.Serialization.

    -   Przechwytuje dodano obsługę wielu subskrybentom Generowanie pliku projektu interfejsu API.

    -   Generowanie pliku zawsze kompletnego projektu nawet wtedy, gdy jeden z plików, który ma być generowany jest zablokowany.

    -   Dodano obsługę * symbole wieloznaczne w rozszerzeniu filtrowania, określając plików do uwzględnienia w projekcie C#.

-   **Integracja z programem Visual Studio:**

    -   Rozwiązany problem ze zgodnością z zaawansowanych narzędzi wydajności.

    -   Stałe generowania MonoBehaviors wokół deklaracje zdarzeń i delegatów.

-   **Debuger:**

    -   Stała potencjalnych blokowanie podczas debugowania.

    -   Rozwiązano problem, na którym zmiennych lokalnych, nie będzie wyświetlana w niektórych ramki stosu.

    -   Stałe sprawdzania puste tablice.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 — wersja zapoznawcza 2
 Wydanych 2015-04-02

### <a name="new-features"></a>Nowe funkcje

-   **Eksplorator projektów Unity:**

    -   Automatycznie Zmień nazwę klasy, zmieniając nazwę pliku, w obszarze Eksplorator projektów Unity (zobacz **opcje** okna dialogowego).

    -   Automatycznie wybierz nowo utworzony skryptów w obszarze Eksplorator projektów Unity.

    -   Śledzenie aktywnego skryptu w Eksploratorze projektu Unity (zobacz **opcje** okna dialogowego).

    -   Podwójny zsynchronizować Eksploratora rozwiązań programu Visual Studio (zobacz **opcje** okna dialogowego).

    -   Przyjmuje ikony programu Visual Studio w obszarze Eksplorator projektów Unity.

-   **Debuger:**

    -   Wybierz cel debugowania active z listy celów debugowania zapisana lub ostatnio używanych (zobacz **opcje** okna dialogowego).

    -   Utwórz punkty przerwania funkcji w metodach MonoBehavior i zastosować je do wielu klas MonoBehavior.

    -   Obsługuje wprowadzić identyfikator obiektu w debugerze.

    -   Obsługa liczba w debugerze trafiony punkt przerwania.

    -   Obsługuje podział na wyjątek w debugerze (eksperymentalne. Zobacz **opcje** okna dialogowego).

    -   Obsługuje tworzenie obiektów i tablic przy obliczaniu wyrażeń w debugerze.

    -   Obsługuje porównania wartości null podczas obliczania wyrażenia w debugerze.

    -   Przestarzali członkowie w oknach debugera czujki filtrowania.

-   **Instalator:**

    -   Zoptymalizowane Visual Studio Tools for Unity rejestracji rozszerzenia.

    -   Zainstaluj program Visual Studio Tools dla pakietu Unity Unity 5.

-   **Dokumentacja:** poprawić wydajność generowania dokumentacji.

-   **Kreatorzy:** obsługę nowych metod MonoBehavior Unity 4.6 i Unity 5.

-   **Unity:** flagi niebezpieczny wyszukiwania i niestandardowe definiuje .rsp — pliki podczas generowania pliku projektu.

-   **Interfejs użytkownika:** dodane Visual Studio Tools for Unity **opcje** okna dialogowego w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Eksplorator projektów Unity:**

    -   Eksplorator projektów Unity należy odświeżyć, po pliki są przenoszone lub zmieniona z Eksploratora rozwiązań programu Visual Studio.

    -   Zachowaj opcje podczas zmiany nazwy plików w obszarze Eksplorator projektów Unity.

    -   Zapobiegaj automatyczne rozwijanie i zwijanie Jeśli pliki są podwójnego kliknięcia w obszarze Eksplorator projektów Unity.

    -   Upewnij się, że nowo wybrane pliki są widoczne w obszarze Eksplorator projektów Unity.

-   **Debuger:**

    -   Zapobiega to możliwe, Zablokuj Visual Studio przy obliczaniu wyrażeń w debugerze.

    -   Upewnij się, że wywołań metody opisywanego się tak zdarzyć na odpowiednie domeny w debugerze.

-   **Unity:**

    -   Popraw lokalizację UnityVS.OpenFile z Unity 5.

    -   Popraw lokalizację pdb2mdb z Unity 5.

    -   Zapobiegaj możliwe wyjątek podczas generowania pliku projektu.

    -   Zapobiegaj można zablokować uruchomionej w systemie OSX Unity.

    -   Obsługa wyjątków wewnętrznych.

    -   Wyślij dzienniki konsoli Unity do listy błędów VS.

-   **Dokumentacja:** Popraw Generowanie dokumentacji dla nowej dokumentacji unity.

-   **Projekt:** Przenieś i Zmień nazwy plików .meta Unity w razie potrzeby, nawet w folderach.

-   **Kreatorzy:** Popraw kolejność parametrów metody MonoBehavior podczas generowania kodu.

-   **Interfejs użytkownika:** motywy obsługi programu Visual Studio dla menu kontekstowe i ikony.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 — wersja zapoznawcza
 Wydanych 2014-11-12

### <a name="new-features"></a>Nowe funkcje

-   Obsługa programu Visual Studio 2015.

-   Kod zabarwienie dla programów do cieniowania Unity w programie Visual Studio 2015.

-   Ulepszone wizualizacji wartości podczas debugowania:

    -   Lepsze wizualizacje ArrayLists, list, obiektach HashTable i słowników.

    -   Pokaż niepubliczne elementy członkowskie i statyczne elementy członkowskie jako kategorie czujki i lokalnych widoków.

    -   Ulepszone wyświetlanie SerializedProperty firmy Unity do oceny, tylko pola wartości, które jest nieprawidłowa dla właściwości.

    -   Debuggerdisplayattribute — Obsługa klas i struktur.

    -   Debuggertypeproxyattribute — pomocy technicznej.

-   Należy wstawiania metod MonoBehaviour za pomocą naszych kreatorów przestrzegać użytkownika konwencje kodowania.

-   Implementuje obsługę szablony tekstu czasu kompilacji w projektach UnityVS wygenerowany.

-   Implementuje obsługę ResX zasobów w projektach UnityVS wygenerowany.

-   Obsługa otwierania programów do cieniowania w programie Visual Studio z Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   Oczyszczanie gniazda przed rozpoczęciem gry w Unity po Attach i Play zostało wyzwolone w programie Visual Studio. To rozwiązuje niektóre problemy z stabilności połączenie między Unity i VS, korzystając z przełącznikami Attach i odtwarzania.

-   Należy unikać wywoływania metod w Unity przez interfejs debugera skryptów aparatu, które są podatne na blokowanie Unity. Rozwiązuje blokowanie Unity, gdy dołączanie debugera.

-   Napraw wyświetlaniu callstacks, jeśli nie są dostępne nie symboli.

-   Rejestruje wywołanie zwrotne dziennika, jeśli nie trzeba było.

## <a name="1920"></a>1.9.2.0
 Wydanych 2014-10-09

### <a name="new-features"></a>Nowe funkcje

-   Poprawa wykrywania odtwarzaczy Unity.

-   Korzystając z naszych użytkownika otwierającego plik, należy Unity przekazać numer wiersza, a także nazwę pliku.

-   Domyślnie w dokumentacji online Unity, jeśli istnieje nie lokalne dokumentacji.

### <a name="bug-fixes"></a>Poprawki błędów

-   Napraw potencjalnych awarii Unity podczas aktywując punkt przerwania po domeny Załaduj ponownie.

-   Usuń wyjątki podane w konsoli platformy Unity podczas zamykania naszych konfiguracji lub dotyczące systemu windows, po domeny Załaduj ponownie.

-   Napraw wykrywania Unity 64-bitowy uruchomionej na komputerze lokalnym.

-   Usuń filtrowanie według wersji środowiska Unity w kreatorach MonoBehaviours.

-   Poprawka usterki, gdzie wszystkie zasoby zostały uwzględnione w plikach projektu, jeśli filtr rozszerzenia był pusty.

## <a name="1910"></a>1.9.1.0
 Wydanych 2014-09-22

### <a name="new-features"></a>Nowe funkcje

-   Optymalizuj punktu przerwania powiązania do lokalizacji źródłowej.

-   Obsługa przeciążonych metod w debugera Obliczanie wyrażenia.

-   Obsługa opakowanie w nim elementów podstawowych i typów wartości podczas obliczania wyrażenia debugera.

-   Obsługuje odtworzenie środowiska zmienne lokalne C# podczas debugowania metod anonimowych.

-   Usuń, a następnie zmień nazwy plików .meta podczas usuwania lub zmiany nazwy plików w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

-   Napraw obsługi motywów programu Visual Studio. Wcześniej, okna dialogowe na czarnym motywy może być pusta (Połącz problemy [#932637](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/932637/) i [#936439](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/936439/)).

-   Poprawka Unity Zablokuj podczas łączenia debugera, gdy Unity jest ponownej kompilacji (Połącz problemy [#947119](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/947119/) i [#969211](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/969211/)).

-   Napraw punktów przerwania podczas debugowania zdalnego edytory lub graczy na innym systemie.

-   Usuń możliwe awarii programu Visual Studio, gdy punkt przerwania zostaje trafiony.

-   Punkty przerwania poprawka powiązanie w celu uniknięcia punktów przerwania przedstawiający jako zwolnione.

-   Usuń obsługę zakres zmiennej w debugerze, aby uniknąć na żywo zmienne, które pojawiają się poza zakresem.

-   Usuń wyszukiwania statycznych elementów członkowskich na debugera Obliczanie wyrażenia (Połącz problem [#953379](https://connect.microsoft.com/VisualStudio/feedbackdetail/view/953379/)).

-   Napraw wyświetlanie typów podczas obliczania wyrażenia debugera, aby wyświetlić właściwości i pola statyczne.

-   Napraw generowania rozwiązanie, gdy Unity nazwy projektu zawiera znaki specjalne, że program Visual Studio zabrania (Połącz problem #948666).

-   Napraw pakietu Visual Studio Tools Unity, aby natychmiast zatrzymać wysyłanie zdarzeń konsoli po opcji unchecked (Połącz problem #933357).

-   Napraw wykrywania odwołania do odwołania do nowych interfejsów API, takich jak UnityEngine.UI w projektach UnityVS wygenerowany został poprawnie wygenerowany.

-   Poprawka Instalatora, aby wymagać czy Visual Studio został zamknięty przed rozpoczęciem instalacji, aby uniknąć uszkodzenia instalacji.

-   Poprawka Instalatora w celu zainstalowania zestawy referencyjne Unity jako składnik autonomicznej z właściwego współużytkowane przez wszystkie wersje pomocą rozszerzenia VSTU.

-   Usuń skrypty Otwieranie za pomocą rozszerzenia VSTU w 64-bitowej wersji platformy Unity.

## <a name="1900"></a>1.9.0.0
 Wydanych 2014-07-29

### <a name="new-features"></a>Nowe funkcje

-   W oknie dołączyć debuger Unity Dodaj możliwość wprowadź niestandardowe adresu IP i portu do debugowania.

-   Dodaj opcję konfiguracji, aby ustawić Unity do uruchamiania w tle, czy nie.

-   Dodaj opcję konfiguracji, aby wygenerować pliki rozwiązań i projektów lub tylko pliki projektu.

-   Docelowym uruchomienia: dołączanie do Unity lub dołączanie do Unity i odtwarzania.

-   Wyświetlanie tablic wielowymiarowych w debugerze.

-   Obsługa nowych Player Unity debugowania portów.

-   Dojście odwołania do zestawów Unity nowe, takich jak 4.6 zestawy graficznego interfejsu użytkownika na platformie Unity.

-   Deconstructs zamknięcia do prawidłowego wyświetlenia zmiennych lokalnych podczas debugowania.

-   Deconstructs wygenerowanego Iteratory zmienne do argumentów podczas debugowania.

-   Zachowaj stan Eksplorator projektów Unity po ponownie Załaduj projekt.

-   Dodaj polecenie do synchronizowania Unity Eksplorator projektów z bieżącego dokumentu.

### <a name="bug-fixes"></a>Poprawki błędów

-   Napraw warunkowych punktów przerwania, których warunki są ustawiane przed rozpoczęciem debugera.

-   Usuń odwołania do UnityEngine, aby uniknąć ostrzeżenia.

-   Napraw analizy wersje beta Unity.

-   Rozwiąż problem, w którym zmienne nie było wyświetlane w oknie zmienne lokalne podczas aktywując punkt przerwania lub wykonywanie krok po kroku.

-   Usuń etykietki narzędzi zmienne w Visual Studio 2013.

-   Napraw generowania dokumentacji IntelliSense dla Unity 4.5.

-   Usuń jednolitości / komunikacji programu Visual Studio po domeny Załaduj ponownie (w Unity Odtwórz/Zatrzymaj).

-   Usuń obsługę części motywów programu Visual Studio.

> [!IMPORTANT]
>  C# jest dominujący języka w ekosystemie Unity — nowe zasoby próbki są w języku C#, zostaną domyślnie Unity dokumentacji C# — usunęliśmy naszych podstawowej obsługi UnityScript i coś lepiej skoncentrować się na środowisko C#. W związku z tym pomocą rozszerzenia VSTU rozwiązania są teraz C# tylko i znacznie szybsze do załadowania.

## <a name="1820"></a>1.8.2.0
 Wydanych 2014-01-07

### <a name="new-features"></a>Nowe funkcje

-   Obejścia problemu w warstwie sieci Unity przez aparat skryptów na Mavericks zdalnego odnajdywania edytory.

-   Obsługa nowych portów, aby odnaleźć zdalnego odtwarzacze Unity.

-   Odwołanie do określonego zestawu UnityEngine do bieżącej kompilacji docelowej.

-   Dodaj ustawienie do filtr plików do uwzględnienia w wygenerowanym projektów.

-   Dodaj ustawienie, aby wyłączyć wysyłanie dzienniki konsoli do listy błędów programu Visual Studio. Jest to przydatne, jeśli używasz PlayMaker lub konsoli Pro, ponieważ może istnieć tylko jedno wywołanie zwrotne zarejestrowane w Unity, aby odbierać dzienniki konsoli.

-   Dodaj ustawienie, aby wyłączyć generowanie pliku mdb symboli debugowania. Jest to przydatne, jeśli użytkownik mdb jest generowany.

### <a name="bug-fixes"></a>Poprawki błędów

-   Usuń regresji, gdy pliki otwarte w PORÓWNANIU z Unity > = 4.2 spowoduje utratę IntelliSense.

-   Napraw naszych okien dialogowych w PORÓWNANIU do obsługi niestandardowych kompozycji.

-   Poprawka zamknięcia UPE menu kontekstowego.

-   Zapobiec awarii w Unity, gdy określonej wersji zestawu wygenerowany, jeśli zsynchronizowane.

## <a name="1810"></a>1.8.1.0
 Wydanych 2013-11-21

### <a name="new-features"></a>Nowe funkcje

-   Dostosowany kreatorów MonoBehaviour z interfejsami API 4.3 Unity.

-   Kreatorzy MonoBehaviour filtrowania interfejsów API środowiska Unity w zależności od używanej wersji.

-   Dodaj odwołanie do System.Xml.Linq do projektów dla Unity > 4.1.

-   Prettify naszych wywołania Debug.Log zawiera na początku ślad stosu w komunikacie.

### <a name="bug-fixes"></a>Poprawki błędów

-   Rozwiązany usterki, w którym firma Microsoft może zakłócać domyślna obsługa plików JavaScript programu Visual Studio.

-   Stałe białe piksel znajdujących się w programie VS rzeczywiste teraz.

-   Stałe usunięcie zestawu UnityVS.VersionSpecific, jeśli jest oznaczony jako tylko do odczytu przez SCM.

-   Stałe wyjątków podczas tworzenia pakietu UnityVS gniazda.

-   Stała awarię programu Visual Studio podczas ładowania obrazów standardowych z zestawów programu Visual Studio.

-   Rozwiązane usterki w Generowanie UnityVS.VersionSpecific dla źródła kompilacje Unity.

-   Stała można zablokować podczas otwierania pakietu Unity gniazda.

-   Usunięto obsługę Unity projektu z łącznikiem (-) w ich nazwy.

-   Stałe otwierania skryptów w Unity, aby nie należy mylić kolejności ALT + TAB dla Unity 4.2 lub nowszej.

## <a name="1800"></a>1.8.0.0
 Wydanych 2013-09-24

### <a name="new-features"></a>Nowe funkcje

-   Znaczne zwiększenie szybkości połączenia debugera.

-   Automatycznie obsługiwać Nawigacja do plików i wierszy w Unity 4.2 lub nowszym.

-   Warunkowe punkty przerwania.

-   Generator pliku projektu obsługuje teraz szablony T4.

-   Zaktualizuj MonBehavior kreatorów z nowych interfejsów API.

-   Dokumentacja IntelliSense w języku C# dla typów Unity.

-   Obliczanie wyrażenia arytmetyczne i logicznych.

-   Lepsze odnajdywanie edytory zdalnego do zdalnego debugowania podglądu.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stała usterki których firma Microsoft będzie wyciek wątku VS po odłączeniu debugera.

-   Stałe białe piksel w wersji programu VS.

-   Stała Obsługa kliknięć na ikony paska stanu.

-   Stałe Generowanie odwołań z zestawami w folderach wtyczek.

-   Stałe Tworzenie gniazda z pakietu UnityVS w przypadku wyjątków.

-   Stałe wykrywanie nowych wersji UnityVS.

-   Stałych monit Menedżera licencji, jeśli licencja wygasła.

-   Stałe usterkę, która może renderować listę procesów pusta w debugerze dołączanie do procesu okna programu VS.

-   Stałe zmiany wartości z wartości logiczne, w widoku lokalny.

## <a name="1220"></a>1.2.2.0
 Wydanych 2013-07-09.

### <a name="bug-fixes"></a>Poprawki błędów

-   Obsługują w pełni kwalifikowane nazwy w ewaluatorze wyrażeń.

-   Stałej blokowanie związane z obsługi wyjątków, gdy aparat Unity skryptów jest przesłanie danych niepoprawny stackframe.

-   Stałe procesu kompilacji dla celów sieci Web.

-   Stałe błędu, który może się zdarzyć, jeśli program Visual Studio została uruchomiona i został usunięty plik na liście plików, aby otworzyć podczas uruchamiania.

-   Stałe UnityVS.OpenFile do obsługi plików z systemem innym niż skryptów, takich jak skompilować programów do cieniowania.

-   Firma Microsoft odwoływać Boo.Lang i UnityScript.Lang z wszystkich C# projektów.

-   Stałe Generowanie odwołań w projektach, jeśli projekt zawiera znaki specjalne.

-   Gdzie wywołań metody usunięty projektów problem rozwiązania VS spowoduje wywołanie wielu NullReferenceException MessageBox.

-   Stałe obsługi zestawów Unity 4.2 Beta.

## <a name="1210"></a>1.2.1.0
 Wydanych 2013-04-09.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe lokalnego wdrożenia Unity zestawów do uzupełniania kodu w przypadku wystąpienia błędu We/Wy (takich jak pliki tylko do odczytu, lub pliki zablokowane przez program Visual Studio).

-   Stała regresji, gdzie otworzenie skryptu z Unity czy skupiają się plik, jeśli został on już otwarty w programie Visual Studio.

-   Rozwiązany problem z wydajnością dla nowego obsługi wyjątków.

-   Stałym powiązaniem punkty przerwania w niektórych zewnętrznej biblioteki dll.

## <a name="1200"></a>1.2.0.0
 Wydanych 2013-03-25

### <a name="new-features"></a>Nowe funkcje

-   Znaczne zwiększenie szybkości połączenia debugera.

-   Eksplorator projektów zoptymalizowane Unity większych projektów.

-   Uznawać ustawienia programu Visual Studio, aby przerwać (lub nie) na obsługiwane i nieobsługiwane wyjątki.

-   Uwzględnić ustawienie programu Visual Studio, aby wywołać ToString dla zmiennych lokalnych.

-   Dodaj nowe menu Debugowanie -> Unity dołączanie debugera, która służy do debugowania odtwarzacze Unity.

-   Zachowaj projektów niestandardowe dodane do rozwiązania UnityVS podczas generowania pliku rozwiązania.

-   Dodawanie nowego skrótu klawiaturowego CTRL + ALT + M -> CTRL + H, aby wyświetlić dokumentację Unity funkcja Unity lub elementu członkowskiego w położeniu karetki.

-   Pliki odpowiedzi kompilatora (źródło) należy wziąć pod uwagę podczas kompilowania w programie Visual Studio.

-   Deconstruct typy wygenerowanego przez kompilator do wyświetlenia zmiennych podczas debugowania generator metody.

-   Uproszczenie zdalnego debugowania przez usunięcie trzeba skonfigurować folder udostępniony na platformie Unity. Teraz wystarczy mieć dostęp do projektu Unity z systemu Windows.

-   Zainstaluj niestandardowego profilu Unity jako profil standardowy docelowej platformy .net. To rozwiązanie wszystkich fałszywych alarmów, które można wyświetlić ReSharper.

-   Obejść Unity skryptów błąd aparatu, aby debuger nie zostanie poprawnie przerwane na z systemem innym niż zarejestrowana wątków.

-   Zmiana zasad użytkownika otwierającego plik, aby uniknąć sytuacji wyścigu w wersji programu VS, gdzie twierdzi, aby można było otworzyć plików, podczas awarii na żądanie Otwórz plik.

-   UnityVS jest teraz pytaniem odświeżyć kompilacji podczas VS jest skompilowanie projektu, a nie w pliku Zapisz już.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe naszych niestandardowego profilu platformy .net

-   Stała integracji motywów i to rozwiązać problemy z naszym z motywu ciemny VS 2012.

-   Skrót stałym zachowanie szybkie VS 2012.

-   Stała wykonywania krokowego problem, który może się zdarzyć, gdy debugowanie i wątku głównego z systemem innym niż czy trafiony punkt przerwania.

-   Stałe uzupełnianie UnityScript i coś typ aliasów, takich jak int.

-   Stałe wyjątek podczas zapisywania nowego ciągu UnityScript lub coś.

-   Stałe wyjątków w menu Unity, gdy rozwiązanie nie została załadowana.

-   Usunięte usterki 48 UV: wpisywanie podwójnego cudzysłowu czasami utworzyć błąd i Przerwij wszystkie funkcje (uzupełnianie kodu, wyróżnianie składni itp.).

-   Usunięte usterki 46 UV: zduplikowane pliku skryptu otwarty (UnityScript), po kliknięciu przycisku na błąd listy programu Visual Studio.

-   Usunięte usterki 42 UV: logo łączności platformy Unity na pasku stanu nie obsługuje zdarzenia myszy w VS 2012.

-   Usunięte usterki 44 UV: CTRL + SHIFT + Q, nie jest dostępna w VS 2012 dla MonoBehaviours szybkie.

-   Usunięte usterki 40 UV: wybrane elementy w obszarze Eksplorator projektów Unity są nieczytelne, gdy okno jest nieaktywne w VS2012 motywu "ciemny".

-   Usunięte usterki 39 UV: problem tokenizację wpisywany ciągów.

-   Usunięte usterki 35 UV: wywołanie ToString na obiektach podczas sprawdzania zmiennych.

-   Usunięte usterki 27 UV: Symbol przejdź do okna niespójność "ciemny" kompozycji w VS2012.

-   Usunięte usterki UV-11: zmiennych lokalnych w procedurach wspólnych.

## <a name="1100---beta-release"></a>1.1.0.0 — wydanie beta
 Wydanych 2014-10-09

## <a name="10130"></a>1.0.13.0
 Wydanych 2013-01-21

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe blokowanie programu Visual Studio, która może się zdarzyć, jeśli debugowany obiekt docelowy wysyła zdarzenia nieprawidłowy wątku. Zwykle będzie zachodzące podczas debugowania zdalnego środowiska Unity w systemie OSX.

-   Stałe blokowanie programu Visual Studio, która może się zdarzyć, jeśli wyjątek zamknięcie debugera.

-   Stała naszych pomocników MonoBehavior po MonoBehavior C# w przestrzeni nazw.

-   Stałe debugera etykietki narzędzi dla UnityScript w programie Visual Studio 2012.

-   Stałe zmiany tylko stałe debugowania z Unity Generowanie projektu.

-   Stała klawiatury nawigacji w obszarze Eksplorator projektów Unity.

-   Stałe kolorowania UnityScript zmienionym ciągów.

-   Stałe naszych użytkownika otwierającego plik do odgadnięcia lepsze nazwę projektu, gdy używane poza Unity. Może to być konieczne, gdy użytkownik używa trzeci użytkownika otwierającego plik części w Unity, który deleguje do UnityVS.

-   Stałe obsługi długich komunikatów wysłanych z Unity UnityVS. Wcześniej długich mogło powodować awarię naszych komunikatów część UnityVS. W rezultacie czasami UnityVS nie Otwórz plik z Unity.

## <a name="10120"></a>1.0.12.0
 Wydanych 2013-01-03

### <a name="bug-fixes"></a>Poprawki błędów

-   Stały blokowanie programu Visual Studio, która może się zdarzyć, gdy program Visual Studio usuwania punktu przerwania.

-   Stałe usterki, gdzie niektórych punktów przerwania nie będzie trafień, po Unity ponownie kompilowana gier skryptów.

-   Stałe debugera tak, aby prawidłowo powiadamiania programu Visual Studio zostały niezwiązanego punktów przerwania.

-   Rozwiązany problem rejestracji, który może uniemożliwić debuger programu Visual Studio do debugowania natywnego programów.

-   Usunięto wyjątek, który może się zdarzyć, gdy obliczenia UnityScript i rezer wyrażenia.

-   Stała regresji, gdzie zmieniając poziom interfejsu API platformy .net w Unity nie spowoduje aktualizację plików projektu.

-   Stałe usterkę interfejsu API, gdy kod użytkownika nie może uczestniczyć w funkcji wywołania zwrotnego dziennika.

## <a name="10110"></a>1.0.11.0
 Wydanych 2012-11-28

### <a name="new-features"></a>Nowe funkcje

-   Oficjalne wsparcie Unity 4.

-   Manipulowanie skryptów w Eksploratorze projektu platformy Unity.

-   Integracja w programie Visual Studio przejdź do okna.

-   Podczas analizowania informacji komunikatu konsoli, tak, aby kliknięcie na liście błędów przejście do pierwszego stackframe przy użyciu symboli.

-   Dodaj [interfejsu API](../cross-platform/customize-project-files-created-by-vstu.md) aby umożliwić użytkownikowi uczestniczyć w Generowanie projektu.

-   Dodaj [interfejsu API](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby umożliwić użytkownikowi uczestniczyć w LogCallback.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe regresji w tle Eksplorator projektów środowiska Unity w programie Visual Studio 2012.

-   Stałe Generowanie projektu dla użytkowników Pełna profilu platformy .net.

-   Stałe Generowanie projektu dla użytkowników w docelowej sieci Web.

-   Generowanie stałym projektu, aby uwzględnić debugowania i śledzenia symbole kompilacji jako Unity jest.

-   Stałe awarii, używając znaków specjalnych w naszym Symbol przejdź do okna.

-   Stałe awarii, jeśli firma Microsoft nie można wstrzyknąć naszych ikonę na pasku stanu programu Visual Studio.

## <a name="10100"></a>1.0.10.0
 Wydanych 2012-10-09.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stała tła Eksplorator projektów środowiska Unity w programie Visual Studio 2010.

-   Stałe blokowanie programu Visual Studio, która może się zdarzyć, jeśli UnityVS próbowano Dołącz debuger do Unity, którego interfejs debugera wcześniej awaria.

-   Stałe blokowanie programu Visual Studio, która może się zdarzyć, gdy punkt przerwania został ustawiony i wystąpiłyby ponowne załadowanie obiektu AppDomain.

-   Stałe, jak zestawy są pobierane z Unity należy unikać blokowania plików i mylić Unity procesu kompilacji.

## <a name="1090"></a>1.0.9.0
 Wydanych 2012-10-03

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe Generowanie projektu, gdy projekt Unity zawiera rzeczywiste zasoby JavaScript.

-   Stałe obsługi błędów w Obliczanie wyrażenia.

-   Stałe ustawienie nowe wartości z polami typów wartości.

-   Stałe możliwe efekty uboczne przy aktywowaniu wyrażenia w edytorze kodu.

-   Stałe, jak typy są przeszukiwane w zestawów załadowanych dla wyrażenia.

-   Usunięte usterki UV 21: oceny przypisania Unity obiektów nie ma wpływu.

-   Usunięte usterki UV 21: nieprawidłowy wskaźnik podczas obliczania wywołania metody, Unity matematyczne API.

## <a name="1080"></a>1.0.8.0
 Wydanych 2012-09-26

### <a name="bug-fixes"></a>Poprawki błędów

-   Stały, sposób naszych obiekt otwierający skryptu ścieżka do projektu, aby można się, że jego jest w stanie otworzyć skrypty i Visual Studio.

-   Usunięte usterki punkty utworzone podczas sesji debugowania działała, która może spowodować, że Visual Studio, aby blokować.

-   Stałe, jak UnityVS jest zarejestrowany w programie Visual Studio 2010.

## <a name="1070"></a>1.0.7.0
 Wydanych 2012-09-14

### <a name="new-features"></a>Nowe funkcje

-   Obsługa programu Visual Studio 2012.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe Generowanie zgodności zachowanie środowiska Unity w edytorze i wtyczek plików projektu.

-   Stałe tłumaczenia .pdb symbole na Unity 4.

> [!IMPORTANT]
>  Dzięki obsłudze programu Visual Studio 2012 było zmienić nazwę kilka plików i innymi przenoszenia. Pakiet UnityVS do zaimportowania Unity ma teraz nazwę UnityVS 2010 lub UnityVS 2012 odpowiednio programu Visual Studio 2010 i Visual Studio 2012. Ta wersja wymaga również, że pliki projektu UnityVS są generowane.

## <a name="1060---internal-build"></a>1.0.6.0 — wewnętrzny kompilacji
 Wydanych 2012-09-12

## <a name="1050"></a>1.0.5.0
 Wydanych 2012-09-10

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe Generowanie plików projektu, gdy skryptów i programów do cieniowania musiało znaku nieprawidłowy kod xml.

-   Stałe wykrywania wystąpień Unity, gdy Unity był połączony z serwerem zasobów. To wyzwalane błędów, aby otworzyć pliki z Unity i automatyczne połączenie debugera programu Visual Studio.

## <a name="1040"></a>1.0.4.0
 Wydanych 2012-09-05

### <a name="new-features"></a>Nowe funkcje

-   Automatyczna konwersja symboli debugowania w Unity.

     Jeśli w folderze zasobów zestawu .dll .NET z jego skojarzony .pdb, po prostu ponownie zaimportować zestaw i UnityVS przekonwertuje .pdb do pliku symboli debugowania, że rozumie Unity przez aparat skryptów, i będziesz mieć do kroku do ponownie zestawy .NET, z UnityVS.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stała UnityVS awarii podczas debugowania spowodowane wyjątków zgłaszanych przez metody lub właściwości wewnątrz Unity.

## <a name="1030"></a>1.0.3.0
 Wydanych 2012-09-04

### <a name="new-features"></a>Nowe funkcje

-   Nowa opcja konfiguracji można wyłączyć użycie UnityVS do otwierania plików z Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe Generowanie odwołania do UnityEditor dla projektów z systemem innym niż edytora.

-   Stałe definicji symbolu UNITY_EDITOR dla projektów z systemem innym niż edytora.

-   Stałe losowe VS awaria spowodowane przez naszych pasek stanu niestandardowych.

## <a name="1020"></a>1.0.2.0
 Wydanych 2012-08-30

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe konflikt z PythonTools debugera.

-   Stałe odwołania do Mono.Cecil.

-   Usunięte usterki w zestawach jak skryptów zostały pobrane z Unity z b7 Unity 4.

## <a name="1010"></a>1.0.1.0
 Wydanych 2012-08-28

### <a name="new-features"></a>Nowe funkcje

-   Obsługa podglądu Unity 4.0 Beta.

### <a name="bug-fixes"></a>Poprawki błędów

-   Stałe kontroli właściwości zgłaszanie wyjątków.

-   Stałe malejącej do obiektów podstawowych, podczas sprawdzania obiektów.

-   Listy rozwijanej puste stałego punktu wstawiania w Kreatorze MonoBehavior.

-   Stałe uzupełnianie dla biblioteki dll znajdujące się w folderze zasobów UnityScript i coś.

## <a name="1000---initial-release"></a>1.0.0.0 - początkowego wydania
 Wydanych 2012-08-22
