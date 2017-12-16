---
title: "Rozwiązywanie problemów z przerwanymi odwołaniami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 453e01fd75e7eda2234979c7feaffd344728d0e3
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="troubleshoot-broken-references"></a>Rozwiązywanie problemów z przerwanymi odwołaniami

Jeśli aplikacja próbuje użyć uszkodzone odwołanie, generowany jest błąd wyjątku. W której nie można odnaleźć składnika, do którego istnieje odwołanie jest podstawowy wyzwalacza tego błędu, ale jest wiele sytuacji w których odwołanie jest uznawana za uszkodzony. Wystąpienia te są wyświetlane na poniższej liście:

- Ścieżka odwołania projektu jest nieprawidłowe lub niekompletne.

- Usunięto plik, do którego nastąpiło odwołanie.

- Zmieniono nazwę pliku, do którego nastąpiło odwołanie.

- Połączenie z siecią lub uwierzytelnianie nie powiodło się.

- Odwołanie jest składnika modelu COM, który nie jest zainstalowany na komputerze.

Poniżej przedstawiono środków zaradczych tych problemów.

> [!NOTE]
> Pliki w zestawach jest przywoływana za pomocą ścieżki bezwzględne w pliku projektu. W związku z tym jest możliwe w dla użytkowników, którzy pracują w środowisku projektowanie brakuje przywoływanego zestawu w środowisku lokalnym. Aby uniknąć tych błędów, zaleca się w takich przypadkach można dodać odwołania projektu do projektu. Aby uzyskać więcej informacji, zobacz [programowanie za pomocą zestawów](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Ścieżka odwołania jest nieprawidłowy

Jeśli projekty są udostępniane na różnych komputerach, niektórych odwołań może nie można odnaleźć, gdy składnik znajduje się w innym katalogu na każdym komputerze. Odwołania są przechowywane w obszarze nazwy pliku składnika (na przykład MyComponent). Po dodaniu odwołanie do projektu, lokalizacja folderu pliku składnika (na przykład C:\MyComponents\\) jest dołączany do **ReferencePath** właściwości projektu.

Po otwarciu projektu próbuje zlokalizować te pliki składnika przeszukując katalogi w ścieżce odwołania. Jeśli projekt zostanie otwarty na komputerze, który przechowuje składnika w innym katalogu, takie jak D:\MyComponents\\, nie można odnaleźć odwołania i pojawia się błąd na liście zadań.

Aby rozwiązać ten problem, można usunąć uszkodzone odwołanie i zastąp go za pomocą okna dialogowego Dodaj odwołanie. Innym rozwiązaniem jest użycie **ścieżkę odwołania** element na stronach właściwości projektu i zmodyfikować folderów na liście do punktu w poprawnych lokalizacjach. **Ścieżkę odwołania** właściwości jest trwały dla każdego użytkownika, na każdym komputerze. W związku z tym modyfikowanie ścieżce odwołania nie wpływa na innych użytkowników projektu.

> [!TIP]
> Odwołania projektu do projektu nie ma tych problemów. Z tego powodu ich używać zamiast odwołania do pliku, jeśli to możliwe.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Aby rozwiązać odwołania projektu przerwane rozwiązując ścieżkę odwołania

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i kliknij przycisk **właściwości**.

   **Projektanta projektu** pojawi się.

1. Jeśli używasz programu Visual Basic, wybierz **odwołania** i kliknij przycisk **ścieżek odwołania** przycisku. W **ścieżek odwołania** oknie dialogowym wpisz ścieżkę folderu, który zawiera element, który chcesz odwołać w **folderu** pola, a następnie kliknij przycisk **Dodaj Folder** przycisku.

    Jeśli używasz programu Visual C#, wybierz **ścieżek odwołania** strony. W **folderu** wpisz ścieżkę folderu, który zawiera element, który chcesz odwołać, a następnie kliknij przycisk **Dodaj Folder** przycisku.

## <a name="referenced-file-has-been-deleted"></a>Przywoływany plik został usunięty.

Jest to możliwe, że plik, do którego nastąpiło odwołanie, został usunięty i już nie istnieje na dysku.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Aby rozwiązać odwołania projektu przerwane dla pliku, który nie istnieje na dysku

- Usuń odwołanie do.

- Jeśli istnieje odwołanie w innej lokalizacji na komputerze, należy go odczytywać z tej lokalizacji.

## <a name="referenced-file-has-been-renamed"></a>Nazwa pliku została zmieniona

Istnieje możliwość, że zmieniono nazwę pliku, do którego nastąpiło odwołanie.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Aby naprawić uszkodzone odwołanie pliku, którego nazwa została zmieniona

- Usuń odwołanie do, a następnie dodaj odwołanie do pliku o zmienionej nazwie.

- Jeśli istnieje odwołanie w innej lokalizacji na komputerze, należy odczytywać je w tej lokalizacji.

## <a name="network-connection-or-authentication-has-failed"></a>Połączenie z siecią lub uwierzytelnianie nie powiodło się

Może istnieć wiele możliwe przyczyny niedostępności plików: połączenie sieciowe nie powiodło się lub niepowodzenia uwierzytelniania, na przykład. Każdy Przyczyna może być unikatowy sposób odzyskiwania; może być konieczne na przykład, skontaktuj się z administratorem lokalnym do uzyskiwania dostępu do wymaganych zasobów. Jednak usunięcie odwołania i zmianie kodu, których użyto go jest zawsze opcję.

## <a name="com-component-is-not-installed-on-computer"></a>Składnik COM nie jest zainstalowany na komputerze

Jeśli użytkownik dodał odwołanie do składnika modelu COM, a drugi użytkownik próbuje uruchomić kod na komputerze, na którym nie zainstalowano tego składnika, drugi użytkownik zostanie zwrócony błąd że odwołanie jest uszkodzona. Instalowanie składnika na drugim komputerze spowoduje Popraw błąd. Aby uzyskać więcej informacji o sposobie używania odwołania do składników modelu COM w projektach, zobacz [współdziałanie COM w aplikacjach .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Zobacz także

[Strona odwołań, Projektant projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
