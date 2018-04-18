---
title: Czcionki i kolory, środowisko, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPag.Environment.Fonts_And_Colors
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a089bc9fe61d1ddc8e4510c4da03235c7ab782ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Czcionki i kolory, środowisko, opcje — Okno dialogowe
**Czcionki i kolory** strony **opcje** okno dialogowe umożliwia określenia niestandardowego schematu czcionek i kolorów dla różnych elementów interfejsu użytkownika w zintegrowane środowisko programistyczne (IDE). Dostęp do tego okna dialogowego, klikając **narzędzia / Opcje**, a następnie wybierając **środowiska / czcionki i kolory**. Jeśli ta strona nie ma na liście, wybierz **Pokaż wszystkie ustawienia** w **opcje** okno dialogowe.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 Zmiany schematu kolorów nie zostały wprowadzone podczas sesji, w którym należy. Zmiany kolorów można ocenić, otwierając inne wystąpienie programu Visual Studio i tworzenie warunków, w których oczekujesz zmiany do zastosowania.  
  
 **Pokaż ustawienia dla**  
 Wyświetla listę wszystkich elementów interfejsu użytkownika, dla których można zmienić schematy czcionek i kolorów. Po wybraniu elementu z tej listy można dostosować ustawienia kolorów dla elementu wybranego w **wyświetlania elementów**.  
  
-   **Edytor tekstu**  
  
     Zmiany w styl czcionki, rozmiaru i koloru ustawienia wyświetlania dla edytora tekstu dotyczą wyglądu tekstu w edytorze tekstu domyślnego. Te ustawienia nie wpłynie dokumentów utworzonych w edytorze tekstów poza IDE.  
  
-   **Drukarki**  
  
     Zmiany styl czcionki, rozmiaru i koloru ustawienia wyświetlania dla drukarki na wygląd tekstu w dokumentach.  
  
    > [!NOTE]
    >  W razie potrzeby można wybrać różne domyślne czcionki drukowanie niż używany do wyświetlenia w edytorze tekstu. Może to być przydatne podczas drukowania kod, który zawiera znaki dwubajtowe i jednobajtowych.  
  
-   **Uzupełnianie składni**  
  
     Zmienia styl i rozmiar czcionki tekstu wyświetlanego w uzupełniania wyskakujących w edytorze.  
  
-   **Etykietka narzędzia Edytora**  
  
     Zmienia styl czcionki i rozmiar tekst wyświetlany w etykietkach narzędzi wyświetlanych w edytorze.  
  
-   **Środowisko czcionki**  
  
     Zmienia styl czcionki i rozmiar wszystkich IDE elementy interfejsu użytkownika nie ma jeszcze osobną opcją w **Pokaż ustawienia dla.** Na przykład, ta opcja ma zastosowanie do **— strona początkowa** , ale nie wpłynie **dane wyjściowe** okna.  
  
-   **[Wszystkie okna narzędzi tekstu]**  
  
     Zmiany styl czcionki, rozmiaru i koloru Wyświetl ustawienia dla tego elementu wpływ wyglądu tekstu w okna narzędzia, które ma okienka wyjściowego w IDE. Na przykład okno danych wyjściowych, okno polecenia, okno bezpośrednie itp.  
  
    > [!NOTE]
    >  Zmienia się na tekst **[wszystkie okna narzędzi tekstu]** elementy nie zostały wprowadzone podczas sesji, w którym należy. Takie zmiany mogą ocenić, otwierając inne wystąpienie programu Visual Studio.  
  
**Użyj wartości domyślnych**  
Resetuje wartości czcionek i kolorów elementu listy wybranego w **Pokaż ustawienia dla**. **Użyj** przycisk pojawia się po innych systemów wyświetlania są dostępne do wyboru. Na przykład możesz wybrać z dwóch systemów drukarki.  
  
**Czcionka (Pogrubienie oznacza czcionkę o stałej szerokości)**  
Wyświetla listę wszystkich czcionek zainstalowanych w systemie. Po menu rozwijanego pierwszym wyświetleniu bieżącą czcionkę dla elementu zaznaczonego w **Pokaż ustawienia dla** zostanie wyróżniona pola. Stałe czcionek — które są łatwiejsze do Dopasuj w edytorze — są pogrubione.  
  
**Rozmiar**  
Wyświetla dostępne punktu rozmiarów wyróżnione czcionki. Zmiana rozmiaru czcionki dotyczy wszystkich **wyświetlania elementów** dla **Pokaż ustawienia dla** zaznaczenia.  
  
**Wyświetl elementy**  
Wyświetla listę elementów, dla których można zmienić kolor pierwszego planu i tła.  
  
> [!NOTE]
>  **Zwykły tekst** jest domyślnym elementem wyświetlania. W efekcie właściwości przypisane do **w postaci zwykłego tekstu** zostaną zastąpione przez właściwości, przypisane do innych elementów wyświetlania. Na przykład przypisać kolor niebieski do **w postaci zwykłego tekstu** i kolor zielony do **identyfikator**, wszystkie identyfikatory pojawią się na zielono. W tym przykładzie **identyfikator** zastąpienie właściwości **w postaci zwykłego tekstu** właściwości.  
  
 Wyświetl elementy, należą:  
  
|Element ekran|Opis|  
|------------------|-----------------|  
|**Zwykły tekst**|Tekst w edytorze.|  
|**Zaznaczony tekst**|Tekst, który znajduje się w bieżącym zaznaczeniu, po aktywowaniu edytora.|  
|**Nieaktywnego zaznaczonego tekstu**|Tekst, który jest uwzględniana w bieżącym zaznaczeniu Edytor utraciła fokus.|  
|**Margines wskaźnika**|Margines po lewej stronie z edytora kodu gdzie są wyświetlane punkty przerwania i ikony zakładki.|  
|**Numery wiersza**|Opcjonalne numery, które są wyświetlane obok każdego wiersza kodu|  
|**Widoczne biały znak**|Spacje, tabulatory i word zawijać wskaźników|  
|**Zakładka**|Wierszy, które mają zakładki. **Zakładka** jest widoczna tylko po margines wskaźnika jest wyłączona.|  
|**Parowanie nawiasów klamrowych (Highlight)**|Wyróżnianie, która jest zazwyczaj pogrubienie do dopasowania nawiasów klamrowych.|  
|**Parowanie nawiasów klamrowych (prostokąt)**|Wyróżnianie, która jest zazwyczaj szare prostokąt w tle.|  
|**Punkt przerwania (wyłączone)**|Nie używany.|  
|**Punkt przerwania (włączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające proste punktów przerwania. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające punkty przerwania, które znajdują się w stanie błędu. Dotyczy tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające punkty przerwania, które znajdują się w stanie ostrzeżenia. Dotyczy tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — Zaawansowane (wyłączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające wyłączony warunkowego najmniej zliczane trafień punktu przerwania. Dotyczy tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — Zaawansowane (włączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające warunkowego najmniej zliczane trafień punktu przerwania. Dotyczy tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — Zaawansowane (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające warunkowych lub zliczane trafień punktów przerwania, które znajdują się w stanie błędu. Dotyczy tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — Zaawansowane (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające warunkowych lub zliczane trafień punktów przerwania, które znajdują się w stanie ostrzeżenia. Dotyczy tylko wtedy, gdy poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — mapowane (wyłączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające wyłączone zamapowanych punktów przerwania. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — mapowane (włączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające mapowane punktów przerwania. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — mapowane (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające mapowane punktów przerwania w stanie błędu. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Punkt przerwania — mapowane (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające mapowane punktów przerwania z ostrzeżeniami. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Słowa kluczowe języka C/C++ użytkownika**|Stała w pliku kodu określonego zdefiniowany za pomocą klasy `#define` dyrektywy.|  
|**Powrót z wywołania**|Określa kolor wyróżnienia dla instrukcji źródła lub wiersze, które wskazują punkty zwracany wywołania po przełączeniu kontekstu do ramki stosu-top podczas debugowania.|  
|**Pole zależne od fragmentu kodu**|Pola, które zostaną zaktualizowane, jeśli pole można edytować bieżącego zostanie zmodyfikowana.|  
|**Pole wstawek kodu**|Edytowalne pola fragmentu kodu jest aktywny.|  
|**Zwijanej tekstu**|Blok tekstu lub kodu, które mogą być przełączane i widoku edytora kodu.|  
|**Komentarz**|Komentarze w kodzie.|  
|**Błąd kompilatora**|Niebieski zygzaki w edytorze wskazujący błąd kompilatora.|  
|**Obszar bez pokrycia**|Kod, który ma nie pasuje do żadnego testu jednostkowego.|  
|**Obszar częściowo pokryty**|Kod, który ma zostać częściowo objętych testu jednostkowego.|  
|**Pokrycie dotknięciu obszaru**|Kod, który ma zostać całkowicie objęte testu jednostkowego.|  
|**Komentarz CSS**|Komentarz w kaskadowych arkuszy stylów. Na przykład:<br /><br /> / * komentarza \*/|  
|**CSS — słowo kluczowe**|Słowa kluczowe w kaskadowego arkusza stylów.|  
|**Nazwa właściwości CSS**|Nazwa właściwości, takie jak tła.|  
|**Wartość właściwości CSS**|Wartość przypisana do właściwości, takie jak niebieski.|  
|**Selektor CSS**|Ciąg, który identyfikuje elementy odpowiadająca im zasada ma zastosowanie do. Selektora może być prosty selektor, takich "H1" lub kontekstowe selektora, takie jak "B H1", która składa się z kilku selektorów prostych.|  
|**Wartość ciągu CSS**|Ciąg w kaskadowych arkuszy stylów.|  
|**Bieżąca lokalizacja listy**|W oknie narzędzia listy, takich jak okno danych wyjściowych i znaleźć wyników windows przejście, bieżącego wiersza.|  
|**Bieżąca instrukcja**|Określa kolor wyróżnienia dla instrukcji źródła lub wiersza, który wskazuje bieżącą pozycję w kroku podczas debugowania.|  
|**Zmienione dane debugera**|Kolor tekstu używany do wyświetlania danych wewnątrz **rejestruje** i **pamięci** systemu windows.|  
|**Tło okna definicji**|Kolor tła **definicji kodu** okna.|  
|**Bieżące dopasowanie okna definicji**|W bieżącej definicji **definicji kodu** okna.|  
|**Nazwa pliku dezasemblacji**|Kolor tekstu używany do wyświetlania plików nazwa podziału wewnątrz **dezasemblacji** okna.|  
|**Źródło dezasemblacji**|Kolor tekstu używany do wyświetlania wierszy źródłowych wewnątrz **dezasemblacji** okna.|  
|**Symbol dezasemblacji**|Kolor tekstu używany do wyświetlania nazwy symbolu wewnątrz **dezasemblacji** okna.|  
|**Tekst dezasemblacji**|Kolor tekstu używany do wyświetlania kod operacji i danych wewnątrz **dezasemblacji** okna.|  
|**Wykluczone kodu**|Kod, który nie może być skompilowany, na warunkowego dyrektywy preprocesora takich jak `#if`.|  
|**Identyfikator**|Identyfikatory w kodzie, takich jak nazwy klasy, nazwy metod i nazwy zmiennych.|  
|**Keyword**|Słowa kluczowe dla danego języka, które są zastrzeżone. Na przykład: klasa i przestrzeni nazw.|  
|**Adres pamięci**|Kolor tekstu używany do wyświetlania kolumny adres wewnątrz **pamięci** okna.|  
|**Zmienione pamięci**|Kolor tekstu używany do wyświetlania danych wewnątrz **pamięci** okna.|  
|**Danych pamięci**|Kolor tekstu używany do wyświetlania danych wewnątrz M**szyfrowanie** okna.|  
|**Nie można go odczytać pamięci**|Kolor tekstu używany do wyświetlania obszary pamięci nie można go odczytać w **pamięci** okna.|  
|**Numer**|Numer w kodzie, który reprezentuje rzeczywistą wartość liczbową.|  
|**Operator**|Operatory, takich jak +, -, i! =.|  
|**Inny błąd**|Inne typy błędów nieuwzględniony w innym zygzaki sygnalizujące błędy. Obecnie w tym niegrzeczny edycji Edytuj i Kontynuuj.|  
|**Preprocesora — słowo kluczowe**|Słowa kluczowe, takie jak używany przez preprocesora #include.|  
|**Region tylko do odczytu**|Kod, którego nie można edytować. Na przykład kod wyświetlany w oknie kodu definicji widoku lub kod, który nie może być modyfikowana podczas Edytuj i Kontynuuj.|  
|**Refaktoryzacja tła**|Kolor tła **podgląd zmian** okno dialogowe.|  
|**Refaktoryzacja bieżącego pola**|Kolor bieżącego elementu, aby być refaktoryzowane w tła **podgląd zmian** okno dialogowe.|  
|**Pole zależne od refaktoryzacji**|Kolor odwołania do elementu, aby być refaktoryzowane w **podgląd zmian** okno dialogowe.|  
|**Dane rejestru**|Kolor tekstu używany do wyświetlania danych wewnątrz **rejestruje** okna.|  
|**Zarejestruj translatora adresów Sieciowych**|Kolor tekstu używany do wyświetlania Nierozpoznane dane i obiektów wewnątrz **rejestruje** okna.|  
|**Tagów inteligentnych**|Używany do określenia konturu, gdy są wywoływane tagów inteligentnych.|  
|**Znacznik SQL DML**|Ma zastosowanie do edytora języka Transact-SQL. Instrukcje DML w tym edytorze są oznaczone obwiedni blue domyślnie.|  
|**Kod nieodświeżony**|Oczekiwanie na aktualizację zastąpione kodu. W niektórych przypadkach Edytuj i Kontynuuj nie można zastosować zmian w kodzie natychmiast, ale zastosuje je później w przypadku kontynuowania debugowania. Dzieje się tak, czy można edytować funkcji, która musi wywoływać funkcję aktualnie wykonywanych, czy dodać więcej niż 64 bajtów nowe zmienne oczekujące na stosie wywołań funkcji. W takim przypadku debuger wyświetla okno dialogowe "Ostrzeżenie o kodzie Nieodświeżonym" i zastąpione kodu kontynuuje wykonywanie do momentu w funkcji zakończy pracę i nie zostanie ponownie wywołany. Edytuj i Kontynuuj stosuje zmiany kodu, w tym czasie.|  
|**Ciąg**|Literały ciągu.|  
|**Ciąg (C# @ dosłownego wyrażenia)**|Literały w języku C#, które będą interpretowane verbatim ciągu. Na przykład:<br /><br /> @"x"|  
|**Błąd składni**|Analizy błędów.|  
|**Skrót do listy zadań**|Jeśli **listy zadań** skrót zostanie dodany do wiersza, a margines wskaźnika jest wyłączone, zostanie wyróżniony wiersz.|  
|**Śledzenia (wyłączone)**|Nie używany.|  
|**Śledzenia (włączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające tracepoints proste. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające tracepoints, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające tracepoints, które są w stanie ostrzeżenia. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - Zaawansowane (wyłączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające wyłączony tracepoints warunkowych lub zliczane trafień. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - Zaawansowane (włączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające tracepoints warunkowych lub zliczane trafień. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - Zaawansowane (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające tracepoints warunkowych lub zliczane trafień, które są w stanie błędu. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - Zaawansowane (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające tracepoints warunkowych lub zliczane trafień, które są w stanie ostrzeżenia. Ta opcja ma zastosowanie tylko wtedy, gdy poziom instrukcji tracepoints są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, opcje — Okno dialogowe](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - mapowane (wyłączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające wyłączone tracepoints mapowane. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - mapowane (włączone)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające mapowane tracepoints. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - mapowane (błąd)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające mapowane tracepoints w stanie błędu. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledzenia - mapowane (ostrzeżenie)**|Określa kolor wyróżnienia dla instrukcji lub wiersze zawierające mapowane tracepoints z ostrzeżeniami. Dotyczy ASP lub ASP.NET debugowania, jeśli poziom instrukcji punkty przerwania są aktywne lub **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji** zaznaczona jest opcja [ogólne, debugowanie, okno dialogowe Opcje Pole](../../debugger/general-debugging-options-dialog-box.md).|  
|**Śledź zmiany po zapisaniu**|Wiersze kodu, które zostały zmodyfikowane, ponieważ plik został otwarty, ale są zapisywane na dysku.|  
|**Śledź zmiany przed zapisaniem**|Wiersze kodu, które zostały zmodyfikowane, ponieważ plik został otwarty, ale nie są zapisywane na dysku.|  
|**Typy użytkownika**|Typy zdefiniowane przez użytkowników.|  
|**Użytkownik wpisze (obiekty delegowane)**|Typ kolor dla obiektów delegowanych.|  
|**Użytkownik wpisze (Typy wyliczeniowe)**|Wpisz kolor używany do wyliczenia.|  
|**Użytkownik wpisze (interfejsy)**|Wpisz kolor dla interfejsów.|  
|**Użytkownik wpisze (typy wartości)**|Wpisz kolor dla typów wartości, takich jak struktury w języku C#.|  
|**Znacznik tylko do odczytu Visual Basic**|Znacznik specyficzne dla języka Visual Basic, używany do wyznaczania kodera, takie jak wyjątek regionów, definicja metody i ramki wywołanie elementu członkowskiego typu liść.|  
|**Ostrzeżenie**|Ostrzeżenia kompilatora.|  
|**Ostrzeżenie linii ścieżki**|Używane w przypadku analizy statycznej ostrzeżenie wierszy.|  
|**Atrybut XML**|Nazwy atrybutów.|  
|**Cudzysłowy atrybutu XML**|Znaki cudzysłowu dla atrybutów XML.|  
|**Wartość atrybutu XML**|Zawartość atrybutów XML.|  
|**Sekcja Cdata XML**|Zawartość \<![CDATA[...]]>.|  
|**Komentarz XML**|Zawartość \<!---->.|  
|**Ogranicznik XML**|Ograniczniki składni XML, w tym <, <?, <!, \<!--,-->,?\>, \<! [,]] >, a [,].|  
|**Atrybut dokumentu XML**|Wartość dokumentacji xml atrybutów, takich jak \<param name = "I" > gdzie "I" pokolorowane.|  
|**Komentarz dokumentu XML**|Komentarze w komentarze dokumentacji xml.|  
|**Doc — znacznik XML**|Tagi w dokumencie XML komentarzy, takich jak<br /><br /> /// \<Podsumowanie >.|  
|**XML — słowo kluczowe**|Słowa kluczowe DTD CDATA, IDREF i NDATA.|  
|**Nazwa XML**|Nazwy elementów i nazwa docelowym instrukcji przetwarzania.|  
|**Instrukcji przetwarzania XML**|Zawartość instrukcji przetwarzania nie zawiera nazwy docelowej.|  
|**Tekst XML**|Zawartość elementu tekstowego.|  
|**XSLT — słowo kluczowe**|Nazwy elementów XSLT.|  
  
 **Element pierwszego planu**  
 Wyświetla dostępne kolory można wybierać dla pierwszego planu elementu wybranego w **wyświetlania elementów**. Ponieważ niektóre elementy są powiązane i w związku z tym należy zachować schemat spójne wyświetlanie, kolor tekstu również zmiana ustawień domyślnych dla elementów, takich jak błąd kompilatora, słowo kluczowe lub operatora.  
  
 **Automatyczne** elementów może dziedziczyć kolor pierwszego planu innych elementów wyświetlanej takie jak **zwykły tekst**. Przy użyciu tej opcji, jeśli zmienisz kolor elementów dziedziczonych wyświetlania, kolor elementów pokrewnych wyświetlania również zmienić automatycznie. Na przykład w przypadku wybrania **automatyczne** wartość **błąd kompilatora** i później zmienić kolor **zwykły tekst** czerwony, **błąd kompilatora**automatycznie odziedziczy kolor czerwony.  
  
 **Domyślna** kolor, który pojawia się po raz pierwszy element uruchamiania programu Visual Studio. Kliknięcie przycisku **Użyj ustawień domyślnych** przycisku powoduje przywrócenie tego koloru.  
  
 **Niestandardowy**  
 Wyświetla okno dialogowe kolorów, co pozwala na ustawianie koloru niestandardowego elementu wybranego w wyświetlania listy elementów.  
  
> [!NOTE]
>  Możliwość Definiuj kolory niestandardowe może być ograniczony przez ustawienia kolorów dla tego ekranu komputera. Na przykład, jeśli komputer jest skonfigurowany do wyświetlania 256 kolorów i wybierz niestandardowego koloru z **kolor** okno dialogowe IDE domyślnie najbardziej dostępne **kolor podstawowy** i wyświetla kolor czarny w **Kolor** okno podglądu.  
  
 **Tło elementu**  
 Udostępnia paletę kolorów, w którym można wybrać kolor tła dla elementu wybranego w **wyświetlania elementów**. Ponieważ niektóre elementy są powiązane i w związku z tym należy zachować schemat spójne wyświetlanie, zmiana koloru tła tekstu także zmianę ustawienia domyślne dla elementów, takich jak błąd kompilatora, słowo kluczowe lub operatora.  
  
 **Automatyczne** elementów może dziedziczyć kolor tła innych elementów wyświetlanej takie jak **zwykły tekst**. Przy użyciu tej opcji, jeśli zmienisz kolor elementów dziedziczonych wyświetlania, kolor elementów pokrewnych wyświetlania również zmienić automatycznie. Na przykład w przypadku wybrania **automatyczne** wartość **błąd kompilatora** i później zmienić kolor **zwykły tekst** czerwony, **błąd kompilatora**automatycznie odziedziczy kolor czerwony.  
  
 **Domyślna** kolor, który pojawia się po raz pierwszy element uruchamiania programu Visual Studio. Kliknięcie przycisku **Użyj ustawień domyślnych** przycisku powoduje przywrócenie tego koloru.  
  
 **Niestandardowy**  
 Wyświetla okno dialogowe kolorów, co pozwala na ustawianie koloru niestandardowego elementu wybranego w wyświetlania listy elementów.  
  
 **Bold**  
 Wybierz tę opcję, aby wyświetlić tekst wybranego **wyświetlania elementów** pogrubioną czcionką. Pogrubiony tekst jest łatwiej zidentyfikować w edytorze.  
  
 **próbki**  
 Przedstawia przykład styl czcionki, rozmiaru i schemat kolorów **Pokaż ustawienia dla** i **wyświetlania elementów** wybrane. To pole służy Podgląd wyników, Eksperymentując z różnymi opcjami formatowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno dialogowe opcji środowiska](../../ide/reference/environment-options-dialog-box.md)   
 [Opcje — okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)   
 [Porady: zmiana czcionek i kolorów](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)