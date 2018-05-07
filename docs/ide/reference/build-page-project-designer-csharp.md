---
title: Strona kompilacji, Projektant projektu (C#)
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b003b3f965ab4f3857e2a532ae715d99533aa8e7
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)
Użyj **kompilacji** strony **projektanta projektu** można określać właściwości konfiguracji kompilacji projektu. Ta strona dotyczy [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tylko projekty.

Aby uzyskać dostęp do **kompilacji** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz pozycję **widoku**, **strony właściwości** w menu. Gdy pojawi się w Projektancie projektu, wybierz **kompilacji** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguracja i platforma
Poniższe opcje pozwalają wybrać configuration i platform, aby wyświetlić lub zmodyfikować.

> [!NOTE]
> Z konfiguracjami kompilacji uproszczony system projektu określa, czy do kompilacji debugowania lub wersji. Dlatego te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie debugowania i konfiguracje wydania](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfiguracja** Określa, które ustawienia konfiguracji, aby wyświetlić lub zmodyfikować. Te ustawienia mogą być **aktywny (debugowanie)** (to jest wartość domyślna), **debugowania**, **wersji**, lub **wszystkie konfiguracje**.

**Platforma** Określa, które ustawienia platformy, aby wyświetlić lub zmodyfikować. Ustawieniem domyślnym jest **aktywny (Any CPU)**. Można zmienić przy użyciu aktywnej platformy **programu Configuration Manager**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i edycja konfiguracji](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Ogólne
Poniższe opcje pozwalają skonfigurować kilka ustawień kompilatora C#.

**Symbole kompilacji warunkowej** określa symbole, na którym ma być wykonywana kompilacja warunkowa. Symbole należy oddzielić średnikiem (";"). Aby uzyskać więcej informacji, zobacz [/ define (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Zdefiniuj stała debugowania** definiuje debugowania jako symbol w kodzie źródłowym wszystkie pliki w aplikacji. Wybranie tej opcji jest odpowiednikiem przy użyciu `/define:DEBUG` opcji wiersza polecenia.

**Zdefiniuj stała śledzenia** definiuje śledzenia jako symbol w kodzie źródłowym wszystkie pliki w aplikacji. Wybranie tej opcji jest odpowiednikiem przy użyciu `/define:TRACE` opcji wiersza polecenia.

**Platformy docelowej** określa procesora, które ma zostać skonfigurowany przy użyciu pliku wyjściowego. Wybierz **x86** dla dowolnego 32-bitowego procesora zgodnych z Intel, wybierz **x64** dla dowolnego 64-bitowy procesor Intel zgodnego wybierz **ARM** kątem procesorów ARM lub wybierz  **Wszelkie Procesora** do określenia, czy dopuszczalny jest dowolnego procesora. **Wszelkie Procesora** jest wartością domyślną dla projektów, ponieważ umożliwia aplikacji do uruchamiania na szerokiej gamy sprzętu.

Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Preferowane jest 32-bitowych** Jeśli **Prefer32-bitowego** pole wyboru jest zaznaczone, aplikacja zostanie uruchomiona jako 32-bitowej aplikacji na zarówno 32-bitowe i 64-bitowych wersjach systemu Windows. Jeśli pole wyboru jest wyczyszczone, aplikacja zostanie uruchomiona jako aplikacja 32-bitowego w 32-bitowych wersjach systemu Windows i jako 64-bitowej aplikacji w 64-bitowych wersjach systemu Windows.

Jeśli uruchomienia aplikacji jako aplikacji 64-bitowych, podwaja rozmiar wskaźnika, i z innych bibliotek, które są dostępne wyłącznie 32-bitowe mogą wystąpić problemy ze zgodnością. Jest przydatna do uruchamiania aplikacji 64-bitowych tylko wtedy, gdy wymaga więcej niż 4 GB pamięci lub 64-bitowe instrukcje Podaj poprawy wydajności znaczące.

To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie poniższe warunki:

-   Na **kompilacji strony**, **platformy docelowej** ma ustawioną wartość listy **Any CPU**.

-   Na **strony aplikacji**, **Output typu** lista określa, czy projekt jest aplikacją.

-   Na **strony aplikacji**, **platformy docelowej** listy określa .NET Framework 4.5.


**Niebezpiecznego kodu** umożliwia kod, który używa [niebezpieczne](/dotnet/csharp/language-reference/keywords/unsafe) — słowo kluczowe do skompilowania. Aby uzyskać więcej informacji, zobacz [/ unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Optymalizuj kod** Włącza lub wyłącza wykonywanie optymalizacji przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne. Aby uzyskać więcej informacji, zobacz [/ optimize (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia
Następujące ustawienia są używane do konfigurowania błąd i ostrzeżenie opcji procesu kompilacji.

**Poziom ostrzeżeń** określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/ warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Pomijanie ostrzeżeń** blokuje możliwość kompilatora generowania co najmniej jedno ostrzeżenie. Wiele numerów ostrzeżeń, które należy oddzielić przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy
Następujące ustawienia są używane do określenia, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z poniższych opcji, aby wskazać pod jakimi warunkami do zwrócenia wystąpił błąd podczas kompilacji napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Brak** traktuje nie ostrzeżenia jako błędy.

**Określone ostrzeżenia** traktuje określonych ostrzeżeń jako błędy. Wiele numerów ostrzeżeń, które należy oddzielić przecinkami lub średnikami.

**Wszystkie** traktuje wszystkie ostrzeżenia jako błędy.

## <a name="output"></a>Dane wyjściowe
Następujące ustawienia są używane do konfigurowania opcji danych wyjściowych dla procesu kompilacji.

**Ścieżka wyjściowa** Określa lokalizację plików wyjściowych dla tej konfiguracji projektu. Wprowadź ścieżkę danych wyjściowych kompilacji w tym polu, lub wybierz **Przeglądaj** przycisk, aby określić ścieżkę. Należy pamiętać, że ścieżka względna; Jeśli wprowadź ścieżkę bezwzględną, będzie można zapisać jako względną. Domyślna ścieżka to bin\Debug lub bin\Release\\.

Z konfiguracjami kompilacji uproszczony system projektu określa, czy do kompilacji debugowania lub wersji. **Kompilacji** polecenie **debugowania** menu (F5) umieści kompilacji w lokalizacji debugowania, niezależnie od tego **ścieżka wyjściowa** określisz. Jednak **kompilacji** polecenie **kompilacji** menu umieszcza je w lokalizacji użytkownika. Aby uzyskać więcej informacji, zobacz [opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md).

**Plik dokumentacji XML** Określa nazwę pliku, do których dokumentacji będą przetwarzane komentarze. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Zarejestruj dla międzyoperacyjności z modelem COM** wskazuje, że obiekt COM (wywoływana otoka COM), który umożliwia obiektu COM na interakcję z Twoją aplikacją zarządzaną powoduje to udostępnienie zarządzanych aplikacji. **Output typu** właściwości w [strony aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) z **projektanta projektu** ta aplikacja musi mieć ustawioną **biblioteki klas** w kolejność dla **Zarejestruj dla międzyoperacyjności z modelem COM** właściwości, które mają być dostępne. Na przykład klasy, która może obejmować w Twojej [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] aplikacji i Ujawnij jako obiekt COM, zobacz [klasa COM — przykład](/dotnet/csharp/programming-guide/interop/example-com-class).

**Wygenerować zestawu serializacji** Określa, czy kompilator będzie korzystać z narzędzia generatora serializatora XML (Sgen.exe) można utworzyć zestawy serializacji XML. Zestawy serializacji może poprawić wydajność uruchamiania <xref:System.Xml.Serialization.XmlSerializer> przypadku użycia tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na **automatycznie**, który określa, że zestawy serializacji generowane tylko wtedy, gdy jest używanych <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie XML. **Wyłącz** Określa, czy zestawy serializacji nigdy nie można wygenerować, niezależnie od tego, czy używa Twój kod <xref:System.Xml.Serialization.XmlSerializer>. **Na** Określa, czy zestawy serializacji zawsze być generowany. Zestawy serializacji są nazywane `TypeName`. XmlSerializers.dll. Aby uzyskać więcej informacji, zobacz [narzędzie generowania serializatora XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Zaawansowane** kliknij, aby wyświetlić [zaawansowane kompilacji okno dialogowe Ustawienia (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) okno dialogowe.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index)