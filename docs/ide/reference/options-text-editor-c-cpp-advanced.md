---
title: Opcje, Edytor tekstu, C/C++, zaawansowane | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords: Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6870313900da464bb2e8a9ae7facfea8c87b72d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="options-text-editor-cc-advanced"></a>Opcje, edytor tekstu, C/C++, zaawansowane
Zmieniając opcje te można zmienić zachowanie związane z IntelliSense i przeglądania bazy danych w przypadku programowania C lub C++.  
  
 Dostępu do tej strony, w **opcje** okno dialogowe, w lewym okienku rozwiń **Edytor tekstu**, rozwiń węzeł **C/C++**, a następnie wybierz pozycję **zaawansowane**.  
  
> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="browsingnavigation"></a>Przeglądanie nawigacji  
 Nigdy nie należy wybierać tych opcji, chyba że w rzadkich przypadkach, gdy rozwiązanie jest tak duży, że działanie bazy danych wykorzystuje niedopuszczalne ilość zasobów systemowych.  
  
 **Wyłączanie bazy danych**  
 Wszelkie wykorzystanie przeglądania bazy danych (SDF), wszystkie inne opcje przeglądania/nawigacji i wszystkie funkcje IntelliSense, z wyjątkiem kodu # Autouzupełnianie include są wyłączone.  
  
 **Wyłącz aktualizacje bazy danych**  
 Baza danych zostanie otwarta tylko do odczytu, a aktualizacje nie będą wykonywane są edycji plików. Większość funkcji będą nadal działać. Jednak ponieważ zmiany zostały wprowadzone, dane staną się przestarzała i niepoprawne wyniki.  
  
 **Wyłącz Aktualizacje automatyczne bazy danych**  
 Baza danych przeglądania kodu nie będzie aktualizowana automatycznie, gdy pliki źródłowe zostaną zmodyfikowane. Jednak po otwarciu **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **ponownego skanowania rozwiązania**, wszystkie nieaktualne pliki będą sprawdzane i baza danych zostanie zaktualizowana.  
  
 **Wyłącz niejawne pliki**  
 Baza danych przeglądania kodu nie zbierania danych dla plików, które nie są określone w projekcie. Projekt zawiera pliki źródłowe i pliki nagłówkowe, które zostały jawnie określone. Niejawnych plików znajdują się w jawnej plików (na przykład afxwin.h, windows.h i atlbase.h). Zazwyczaj system znajduje tych plików i je również indeksów dla różnych funkcji przeglądania (w tym przejdź do). Jeśli wybierzesz tę opcję, te pliki nie są indeksowane i niektóre funkcje nie są dostępne dla nich. Jeśli wybierzesz tę opcję, "Wyłącz niejawne czyszczenie" i "Wyłącz zewnętrzne zależności" są również domyślnie wybrany.  
  
 **Wyłącz niejawne czyszczenie**  
 Baza danych przeglądania kodu nie czyszczenia niejawnych plików, które nie są już używane w górę. Ta opcja uniemożliwia niejawnych plików przed usunięciem z bazy danych, gdy są one już używane. Na przykład, jeśli dodasz `#include` w dyrektywie, który odwołuje się mapi.h do jednego z plików źródłowych, mapi.h zostanie znaleziony i indeksowane. Jeśli następnie usuń #include i plik nie jest używany w innym miejscu, informacje o nim zostaną usunięte po pewnym czasie, chyba że zostanie wybrana ta opcja. (Zobacz **interwał ponownego skanowania rozwiązania** opcję.) Ta opcja jest ignorowane w przypadku jawnie ponownego skanowania rozwiązania.  
  
 **Wyłącz foldery zależności zewnętrznych**  
 Folder zewnętrznych zależności, dla każdego projektu nie jest tworzony lub aktualizowany. W **Eksploratora rozwiązań**, każdy projekt zawiera folder zewnętrznych zależności, który zawiera wszystkie niejawnych plików dla tego projektu. Jeśli wybierzesz tę opcję, nie jest wyświetlany wybrany folder.  
  
 **Ponowne utworzenie bazy danych**  
 Utwórz ponownie przeglądania bazy danych z nic ładuje rozwiązania przy następnym uruchomieniu kodu. Jeśli wybierzesz tę opcję, plik bazy danych SDF jest usuwany podczas następnego ładowania rozwiązania, powodując w bazie danych do odtworzenia i wszystkie pliki indeksowane.  
  
 **Interwał ponownego skanowania rozwiązania**  
 Zadanie "Przeskanuj teraz ponownie rozwiązanie" zaplanowano dla interwału, który określisz. Podaj od 0 do 5000 minut. Wartość domyślna to 60 minut. Gdy rozwiązanie jest ponownie skanowana, sygnatury czasowe plików są sprawdzane w celu określenia, czy plik został zmieniony poza IDE. (Automatycznie są śledzone zmiany wprowadzone w środowisku IDE, a pliki są aktualizowane). Niejawnie dołączonych plików są sprawdzane w celu określenia, czy ich w przypadku wszystkich nadal odwołuje się do.  
  
## <a name="diagnostic-logging"></a>Rejestrowanie diagnostyczne  
 Te opcje są dostarczane na wypadek, gdyby firma Microsoft zaleca zbieranie zaawansowanych informacji do zdiagnozowania problemu. Informacje o rejestrowaniu nie jest przydatne dla użytkowników, i zaleca się pozostawić ją wyłączoną.  
  
 **Włączanie rejestrowania**  
 Umożliwia rejestrowanie diagnostyczne w oknie danych wyjściowych.  
  
 **Poziom rejestrowania**  
 Ustaw poziom szczegółowości dziennika, od 0 do 5.  
  
 **Filtr rejestrowania**  
 Filtry wyświetlane typy zdarzeń za pomocą maski.  
  
 Ustaw za pomocą sum któregokolwiek z następujących opcji:  
  
-   0 — Brak  
  
-   1 — Ogólne  
  
-   2 — w stanie bezczynności  
  
-   4 - elementu pracy  
  
-   8 - IntelliSense  
  
-   16 - ACPerf  
  
-   32 - ClassView  
  
## <a name="fallback-location"></a>Lokalizacji rezerwowej  
 Rezerwowej lokalizacji jest, gdzie pliki obsługi IntelliSense i SDF (na przykład iPCH) są wprowadzane podczas lokalizacji głównej (tym samym katalogu co rozwiązania) nie jest używany. Taka sytuacja może wystąpić, użytkownik nie ma uprawnień do zapisu do katalogu rozwiązania lub katalog rozwiązania jest powolne urządzenia. Domyślnej lokalizacji rezerwowej znajduje się w katalogu temp użytkownika.  
  
 **Zawsze używać rezerwowej lokalizacji**  
 Wskazuje, że kod bazy danych plików przeglądania i IntelliSense zawsze powinny być przechowywane w folderze wskazanym jako sieci "Lokalizacja rezerwowa", nie razem z plikiem .sln. IDE nigdy nie próbuje umieścić pliki SDF lub iPCH obok katalog rozwiązania i będzie zawsze używać rezerwowej lokalizacji.  
  
 **Nie ostrzegaj o wykorzystaniu lokalizacji rezerwowej**  
 Nie ma informacji lub zostanie wyświetlony monit, jeśli używane jest "Lokalizacja rezerwowa". Zwykle IDE informuje należało użycie rezerwowej lokalizacji. Ta opcja powoduje wyłączenie tego ostrzeżenia.  
  
 **Lokalizacji rezerwowej**  
 Ta wartość jest używana jako lokalizacja pomocnicza do przechowywania przeglądania bazy danych lub pliki IntelliSense kodu. Domyślnie katalog tymczasowy jest Twojej lokalizacji rezerwowej. IDE utworzy podkatalogu w ramach określonej ścieżki (lub katalogu tymczasowego) zawierający nazwę rozwiązania oraz skrót pełną ścieżkę do rozwiązania, które pozwala uniknąć problemów z nazwami rozwiązania są identyczne.  
  
## <a name="intellisense"></a>IntelliSense  
 **Automatyczna szybka podpowiedź**  
 Włącza etykietki narzędzia skrócone informacje, gdy Przesuń wskaźnik myszy nad tekstem.  
  
 **Wyłącz IntelliSense**  
 Wyłącza wszystkie funkcje IntelliSense. IDE nie tworzy VCPkgSrv.exe procesów do obsługi żądań IntelliSense, a nie funkcji IntelliSense będzie działać (skrócone informacje, listy członków Autouzupełnianie, Param pomocy). Kolorowanie semantyczne i podświetlanie odwołań również są wyłączone. Ta opcja nie wyłączać funkcje przeglądania, które polegać wyłącznie na bazie danych (w tym okna na pasku nawigacyjnym, ClassView i właściwości).  
  
 **Wyłącz automatyczne aktualizowanie**  
 Aktualizowanie IntelliSense jest opóźnione aż do rzeczywistego żądania o IntelliSense. To opóźnienie może spowodować dłuższy czas wykonania pierwszej operacji IntelliSense w pliku, ale może być przydatne ustawić tę opcję na maszynach bardzo wolno lub ograniczone zasobów. Jeśli wybierzesz tę opcję, należy również niejawnie wybierz opcje "Wyłącz raportowanie błędów" i "Wyłącz zygzaki".  
  
 **Wyłączyć raportowanie błędów**  
 Wyłącza raportowanie błędów IntelliSense przez zygzaki i okno Lista błędów. Dodatkowo wyłącza analizowanie w tle skojarzone z raportowania błędów. Jeśli wybierzesz tę opcję, należy również niejawnie wybierz opcję "Wyłącz zygzaki".  
  
 **Wyłącz zygzaki**  
 Wyłącza zygzaki sygnalizujące błędy IntelliSense. Nie pokazuj red "zygzaki", w oknie edytora, ale błąd nadal będą wyświetlane w oknie Lista błędów.  
  
 **Wyłącz # Autouzupełnianie include**  
 Wyłącza automatyczne uzupełnianie `#include` instrukcje.  
  
 **Użyj ukośnik w # Autouzupełnianie include**  
 Wyzwala automatycznego uzupełniania `#include` instrukcje po "/" jest używany. Domyślnym ogranicznikiem jest odwrotny ukośnik "\'. Kompilator może zaakceptować albo, więc ta opcja umożliwia określenie kodzie używa.  
  
 **Maksymalna liczba buforowanych jednostek tłumaczenia**  
 Maksymalna liczba jednostek tłumaczenia, które pozostaną jednocześnie aktywne dla żądań IntelliSense. Należy określić wartość z zakresu od 2 do 15. Ta liczba bezpośrednio dotyczy maksymalną liczbę procesów VCPkgSrv.exe, które będą działać (dla danego wystąpienia programu Visual Studio). Wartość domyślna to 2, ale jeśli masz dostępną pamięć, można zwiększyć tę wartość i prawdopodobnie osiągnąć nieco większą wydajność na IntelliSense.  
  
 Aby uzyskać więcej informacji na temat jednostek tłumaczenia, zobacz [fazy tłumaczenia](/cpp/preprocessor/phases-of-translation).  

 **Element członkowski listy kropki na strzałkę**  
 Zastępuje "." strzałką "->" Jeśli ma to zastosowanie do listy członków.

 **Wyłącz agresywne listy**  
 Podczas wpisywania nazwy typu lub zmienna nie jest wyświetlana lista elementów członkowskich. Ta lista jest wyświetlana tylko wtedy, gdy jeden ze znaków zatwierdzania wpisz zgodnie z definicją w **znaki zatwierdzania listy Członkowskie** opcji.  
  
 **Wyłącz słowa kluczowe listy elementu członkowskiego**  
 Słowa kluczowe języka, takich jak `void`, `class`, `switch` nie są wyświetlane w element członkowski listy sugestii.  
  
 **Wyłącz fragmenty kodu**  
 Wstawki kodu nie są wyświetlane w element członkowski listy sugestii.  
  
 **Wyłącz kolorowanie semantyczne**  
 Powoduje wyłączenie wszystkich kolorowania kodu z wyjątkiem słów kluczowych języka, ciągi i komentarze.  
  
 **Zatwierdzanie List Członkowskich inteligentne**  
 Dodaje wiersz po wybraniu klawisz Enter na końcu pełni wprowadzonego słowa.  
  
 **Tryb filtrowania listy elementu członkowskiego**  
 Ustawia typ algorytm dopasowania. **Rozmytego** znajdzie najwięcej możliwości zgodny, ponieważ używa algorytmu, która jest podobna do sprawdzania pisowni, aby znaleźć dopasowań, które są podobne, lecz nie są identyczne. **Filtrowanie inteligentne** odpowiada podciągów, nawet jeśli nie ma na początku słowo. **Prefiks** zgodny tylko na identyczne podciągi rozpocząć od początku słowo.  
  
 **Znaki zatwierdzania listy elementu członkowskiego**  
 Określa znaki, które powodują aktualnie zaznaczony uwag listy elementów członkowskich do można zatwierdzić. Można dodawać i usuwać znaków z tej listy.  
  
## <a name="references"></a>Odwołania  
 **Wyłącz Rozwiązywanie**  
 Ze względu na wydajność "Znajdź wszystkie odwołania" wyświetli nieprzetworzone wyniki wyszukiwania tekstowego domyślnie zamiast wykorzystania IntelliSense do weryfikacji każdej możliwości. Można wyczyść to pole wyboru, aby uzyskać dokładniejsze wyniki na wszystkich operacji wyszukiwania. Aby filtrować na podstawie ciągu wyszukiwania, otwórz menu skrótów dla listy wyników i następnie wybierz pozycję "Rozwiąż wyniki".  
  
 **Ukryj niepotwierdzone**  
 Ukryj niepotwierdzone elementy w wynikach "Znajdź wszystkie odwołania". Jeśli nie ustawiono "Wyłącz rozwiązywanie" opcji, które można tę opcję, Ukryj niepotwierdzone elementy w wynikach.  
  
 **Wyłącz podświetlanie odwołań**  

 ## <a name="text-editor"></a>Edytor tekstu
 **Włącz rozwijanie zakresów**  
 Jeśli opcja jest włączona, zostanie otoczona zaznaczonego tekstu w nawiasach klamrowych, wpisując "{" do edytora tekstu.  
  
 **Włącz rozwiń pierwszeństwa**  
 Jeśli opcja jest włączona, zostanie otoczona zaznaczonego tekstu w nawiasach, wpisując "(" do edytora tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
