---
title: Strona kompilowania, Projektant projektu (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d1b5c55c3bc1732d0b394473f25c0b103c917f4
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compile-page-project-designer-visual-basic"></a>Strona kompilowania, Projektant projektu (Visual Basic)

Użyj **skompilować** strony projektanta projektu do określenia instrukcji kompilacji. Można również określić kompilatora zaawansowanych opcji i wstępnej kompilacji lub postkompilacyjnego zdarzeń na tej stronie.

Aby uzyskać dostęp do **skompilować** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz pozycję **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **skompilować** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma

Następujące ustawienia pozwalają wybrać configuration i platform, aby wyświetlić lub zmodyfikować.

> [!NOTE]
> Z konfiguracjami kompilacji uproszczony system projektu określa, czy do kompilacji debugowania lub wersji. W związku z tym **konfiguracji** i **platformy** list nie są wyświetlane.

 **Konfiguracja**

 Określa, które ustawienia konfiguracji, aby wyświetlić lub zmodyfikować. Ustawienia są **debugowania** (ustawienie domyślne), **wersji**, lub **wszystkie konfiguracje**. Aby uzyskać więcej informacji, zobacz [opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md) i [porady: tworzenie i edycja konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

 **Platformy**

 Określa, które ustawienia platformy, aby wyświetlić lub zmodyfikować. Można określić **Any CPU** (ustawienie domyślne), **x64**, lub **x86**.

## <a name="compiler-configuration-options"></a>Opcje kompilatora konfiguracji

Następujące ustawienia pozwalają włączyć ustawienia kompilatora opcji konfiguracji.

 **Ścieżka danych wyjściowych kompilacji**

 Określa lokalizację plików wyjściowych dla tej konfiguracji projektu. W tym polu wpisz ścieżkę danych wyjściowych kompilacji, lub kliknij przycisk **Przeglądaj** przycisk, aby wybrać ścieżkę. Należy pamiętać, że ścieżka względna; Jeśli wprowadź ścieżkę bezwzględną, będzie można zapisać jako względną. Domyślna ścieżka to bin\Debug\ lub bin\Release\\.

 Z konfiguracjami kompilacji uproszczony system projektu określa, czy do kompilacji debugowania lub wersji. **Kompilacji** polecenie **debugowania** menu (F5) umieści kompilacji w lokalizacji debugowania, niezależnie od tego **ścieżka wyjściowa** określisz. Jednak **kompilacji** polecenie **kompilacji** menu umieszcza je w lokalizacji użytkownika.
  
 **Opcja jawnego**  
 Określa, czy zezwalać na niejawne deklaracji zmiennych. Wybierz **na** wymagające jawnej deklaracji zmiennych. To powoduje, że kompilator może raportować błędy zmiennych nie jest zadeklarowana, zanim zostaną użyte. Wybierz **poza** umożliwia niejawne deklaracji zmiennych.  
  
 To ustawienie odpowiada [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) — opcja kompilatora.  
  
 Jeśli plik kodu źródłowego zawiera [Option Explicit — instrukcja](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), `On` lub `Off` wartości w instrukcji zastępuje **Option Explicit** ustawienie **kompilacji Strona**.  
  
 Podczas tworzenia nowego projektu **Option Explicit** ustawienie **strony kompilacji** ma ustawioną wartość **Option Explicit** w **opcje**  okno dialogowe. Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej **Option Explicit** w **domyślne VB** jest **na**.  
  
 Ustawienie **Option Explicit** do `Off` zwykle nie jest dobrym rozwiązaniem. Można wpiszesz nazwę zmiennej w przynajmniej jednej lokalizacji, co może spowodować nieoczekiwane wyniki, gdy program jest uruchamiany.  
  
 **Opcja strict**  
Określa, czy do wymuszania semantyki typu strict. Gdy **Option Strict** jest **na**, błąd kompilacji powodują następujące warunki:  
  
-   Niejawne konwersje zawężającej  
  
-   Późne powiązania  
  
-   Niejawne wpisanie, który daje w `Object` typu  
  
Niejawne błędy konwersji zawężającej wystąpić, gdy istnieje konwersja typu danych niejawne, który jest konwersji zawężającej. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Konwersje jawne i niejawne](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions), i [rozszerzanie i zwężanie konwersji](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
Obiekt jest późnym wiązaniem, gdy jest przypisany do właściwości lub metody zmienna, która jest zadeklarowana jako typu `Object`. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement) i [wczesnego i późne wiązanie](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).
  
Niejawne obiektu typu błędy występują, gdy nie może być odpowiedniego typu wywnioskowane dla zadeklarowana zmienna, więc typ `Object` jest wywnioskowany. To przede wszystkim występuje, gdy używasz `Dim` instrukcji, aby zadeklarować zmienną bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer — instrukcja](/dotnet/visual-basic/language-reference/statements/option-infer-statement)i [specyfikacja języka Visual Basic](/dotnet/visual-basic/reference/language-specification).  
  
**Option Strict** ustawienie odpowiada [/optionstrict —](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) — opcja kompilatora.  
  
Jeśli plik kodu źródłowego zawiera [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement), `On` lub `Off` wartości w instrukcji zastępuje **Option Strict** ustawienie **strony kompilacji** .  
  
Podczas tworzenia projektu, **Option Strict** ustawienie **strony kompilacji** ma ustawioną wartość **Option Strict** w **opcje** okno dialogowe. Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej **Option Strict** w **domyślne VB** jest **poza**.  
  
**Opcja Strict ostrzeżeń indywidualnych.** **Konfiguracje ostrzeżenie** sekcji **strony kompilacji** zawiera ustawienia, które odpowiadają trzy warunki, które spowodować błąd kompilacji podczas `Option Strict` znajduje się na. Te ustawienia są następujące:  
  
-   **Niejawna konwersja**  
  
-   **Późne wiązanie; Wywołanie może zakończyć się niepowodzeniem w czasie wykonywania**  
  
-   **Niejawne typu. założono, że obiekt**  
  
Podczas ustawiania **Option Strict** do **na**, wszystkie trzy ustawienia konfiguracji tych ostrzeżeń są ustawione na **błąd**. Podczas ustawiania **Option Strict** do **poza**, wszystkie trzy ustawienia **Brak**.  
  
Oddzielnie można zmienić ustawienie konfiguracji każdego ostrzeżenie **Brak**, **ostrzeżenie**, lub **błąd**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżenie **błąd**, `On` pojawia się w `Option strict` pole. Jeśli wszystkie trzy **Brak**, `Off` pojawia się w tym polu. Dla dowolnej kombinacji tych ustawień **(niestandardowy)** pojawi się.  
  
**Opcja compare**  
Określa typ porównania ciągów do użycia. Wybierz **binarne** nakazać kompilatorowi używanie porównania ciągu binarnego, z uwzględnieniem wielkości liter. Wybierz **tekst** umożliwia porównywanie ciągów tekstowych specyficzne dla ustawień regionalnych, bez uwzględniania wielkości liter.  
  
To ustawienie odpowiada [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) — opcja kompilatora.  
  
Jeśli plik kodu źródłowego zawiera [instrukcji porównanie opcji](/dotnet/visual-basic/language-reference/statements/option-compare-statement), `Binary` lub `Text` wartości w instrukcji zastępuje **Option Compare** ustawienie **kompilacji Strona**.  
  
Podczas tworzenia projektu, **Option Compare** ustawienie **strony kompilacji** ma ustawioną wartość **Option Compare** w **opcje** okno dialogowe. Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Początkowa domyślne ustawienie **Option Compare** w **domyślne VB** jest **binarne**.  
  
**Opcja infer**  
Określa, czy zezwalać na wnioskowanie o typie lokalnym w deklaracjach zmiennych. Wybierz **na** Aby zezwolić na użycie wnioskowania o typie lokalnym. Wybierz **poza** na wnioskowanie o typie lokalnym bloku.  
  
To ustawienie odpowiada [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) — opcja kompilatora.  
  
Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](/dotnet/visual-basic/language-reference/statements/option-infer-statement), `On` lub `Off` wartości w instrukcji zastępuje **Option Infer** ustawienie **strony kompilacji** .  
  
Podczas tworzenia projektu, **Option Infer** ustawienie **strony kompilacji** ma ustawioną wartość **Option Infer** w **opcje**okno dialogowe. Aby wyświetlić lub zmienić ustawienia w tym oknie dialogowym, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej **Option Infer** w **domyślne VB** jest **na**.  
  
**Docelowy Procesora**  
Określa procesor ma zostać skonfigurowany przy użyciu pliku wyjściowego. Określ **x86** dla dowolnego procesora Intel zgodnego 32-bitowych **x64** dla dowolnego 64-bitowy procesor Intel zgodnego **ARM** dla dowolnego procesora ARM lub **Any CPU**  do określenia, czy dopuszczalny jest dowolnego procesora. **Wszelkie Procesora** jest to wartość domyślna dla nowych projektów, ponieważ umożliwia aplikacji, aby działała z największą liczbą typów sprzętu.  
  
Aby uzyskać więcej informacji, zobacz [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
**Preferowane jest 32-bitowy**  
Jeśli **Prefer32-bitowego** pole wyboru jest zaznaczone, aplikacja zostanie uruchomiona jako 32-bitowej aplikacji na zarówno 32-bitowe i 64-bitowych wersjach systemu Windows. W przeciwnym razie aplikacja zostanie uruchomiona jako aplikacja 32-bitowego w 32-bitowych wersjach systemu Windows i jako 64-bitowej aplikacji w 64-bitowych wersjach systemu Windows.  
  
Uruchamianie zgodnie z aplikacją 64-bitową podwaja rozmiar wskaźnika i może spowodować problemy ze zgodnością z bibliotek, które są dostępne wyłącznie 32-bitowe. Warto, aby uruchomić aplikację jako 64-bitowych tylko wtedy, gdy działa znacznie szybciej, lub wymaga więcej niż 4 GB pamięci.  
  
To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie poniższe warunki:  
  
-   Na **skompilować strony**, **Procesora docelowej** ma ustawioną wartość listy **Any CPU**.  
  
-   Na **strony aplikacji**, **typu aplikacji** lista określa, czy projekt jest aplikacją.  
  
-   Na **strony aplikacji**, **platformy docelowej** listy określa .NET Framework 4.5.  
  
**Ostrzeżenie konfiguracji**  
Poniższa tabela zawiera warunki kompilacji i odpowiedniego poziomu powiadomień **Brak**, **ostrzeżenie**, lub **błąd** dla każdego.  
  
Domyślnie wszystkie ostrzeżenia kompilatora są dodawane do listy zadań podczas kompilacji. Wybierz **Wyłącz wszystkie ostrzeżenia** nakazać kompilator nie problem ostrzeżeń lub błędów. Wybierz **traktuje wszystkie ostrzeżenia jako błędy** Jeśli kompilator Traktuj ostrzeżenia jako błędy, które muszą zostać usunięte.  
  
**Wyłącz wszystkie ostrzeżenia**  
Określa, czy zezwalać kompilatora wysyłanie powiadomień, jak określono w **warunek i powiadomień** tabeli opisem we wcześniejszej części tego dokumentu. Domyślnie to pole wyboru jest wyczyszczone. Zaznacz to pole wyboru, aby poinstruować kompilator, aby nie wystawiać ostrzeżeń lub błędów.  
  
To ustawienie odpowiada [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) — opcja kompilatora.  
  
**Traktuje wszystkie ostrzeżenia jako błędy**  
Określa sposób Traktuj ostrzeżenia. Domyślnie to pole wyboru jest wyczyszczone, tak aby wszystkie powiadomienia ostrzeżenie pozostały należy ustawić **ostrzeżenie**. Zaznacz to pole wyboru, aby zmienić wszystkie ostrzeżenia powiadomienia do **błąd**.  
  
Ta opcja jest dostępna tylko wtedy, gdy **Wyłącz wszystkie ostrzeżenia** jest wyczyszczone.  
  
**Generuj plik dokumentacji XML**  
Określa, czy do generowania informacji w dokumentacji. Domyślnie to pole wyboru jest zaznaczone, poinstruowanie kompilatora, aby wygenerować informacje dokumentacji i uwzględnić go w pliku XML. Wyczyść to pole wyboru, aby nakazać kompilatora, aby pominąć tworzenie dokumentacji.  
  
To ustawienie odpowiada [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) — opcja kompilatora.  
  
**Zarejestruj dla międzyoperacyjności z modelem COM.**  
Określa, czy obiekt COM (COM-wywoływana otoka), który umożliwia obiektu COM do interakcji z aplikacją powoduje to udostępnienie zarządzanych aplikacji.  
  
Domyślnie to pole wyboru jest wyczyszczone, który określa, że aplikacja nie zezwala COM interop. Zaznacz to pole wyboru, aby umożliwić współdziałanie z COM.  
  
Ta opcja nie jest dostępne dla projektów aplikacji systemu Windows lub aplikacji konsoli.  
  
**Zdarzenia kompilacji**  
Kliknij ten przycisk, aby uzyskać dostęp do **zdarzeń kompilacji** okno dialogowe. To okno dialogowe służy do określenia instrukcji konfiguracji wstępnej kompilacji i mające miejsce po kompilacji dla projektu. To okno dialogowe dotyczy tylko projektów Visual Basic. Aby uzyskać więcej informacji, zobacz [kompilacji okno dialogowe zdarzenia (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
**Opcje zaawansowane kompilacji**  
Kliknij ten przycisk, aby uzyskać dostęp do **ustawienia AdvancedCompiler** okno dialogowe. Użyj **ustawienia AdvancedCompiler** okno dialogowe, aby określić projektu zaawansowane właściwości konfiguracji kompilacji. To okno dialogowe dotyczy tylko projektów Visual Basic. Aby uzyskać więcej informacji, zobacz [Zaawansowane z okno dialogowe Ustawienia kompilatora (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  


## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilator w wierszu polecenia programu Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Instrukcje: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md)