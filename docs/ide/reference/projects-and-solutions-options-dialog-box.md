---
title: Opcje projektów i rozwiązań — okno dialogowe
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbd3fe20377cd2aa4954e904fec50702cc9b7120
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843994"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Strona Projekty i rozwiązania, opcje — Okno dialogowe

Ustawia zachowanie programu Visual Studio związane z projektów i rozwiązań. Aby uzyskać dostęp do tych opcji, zaznacz **narzędzia** > **opcje**, rozwiń węzeł **projekty i rozwiązania**, a następnie wybierz **ogólne** .

Do ustawiania domyślnych ścieżek folderów projektów i szablon **lokalizacje** kartę w tym samym oknie dialogowym.

> [!NOTE]
> Opcje dostępne w interfejsie użytkownika mogą różnić się z tym, co opisano w tym miejscu, w zależności od wersji lub aktywne ustawienia. Ten artykuł dotyczy z **programowanie ogólne ustawienia** pamiętać. Aby wyświetlić lub zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Strona Ogólne

Poniższe opcje są dostępne na **ogólne** strony.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Zawsze pokazuj listy błędów Jeżeli kompilacja zakończy się z błędami

Otwiera **listy błędów** okna po zakończeniu kompilacji, tylko wtedy, gdy nie można utworzyć projektu. Są wyświetlane błędy występujące podczas procesu kompilacji. Po wyłączeniu tej opcji nadal występują błędy, ale nie można otworzyć okna po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.

### <a name="track-active-item-in-solution-explorer"></a>Śledzenie aktywnego elementu w Eksploratorze rozwiązań

Po wybraniu **Eksploratora rozwiązań** automatycznie zostanie otwarty i aktywny element jest zaznaczony. Zmiany wybranego elementu podczas pracy z różnych plików w projekcie lub rozwiązaniu lub różnych składników w projektancie. Jeśli ta opcja jest wyczyszczone, zaznaczenie w **Eksploratora rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.

### <a name="show-advanced-build-configurations"></a>Pokaż zaawansowane konfiguracje kompilacji

Po wybraniu opcji konfiguracji kompilacji są wyświetlane na **stron właściwości projektów** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe. Po wyczyszczeniu opcji konfiguracji kompilacji nie występują na **stron właściwości projektów** okno dialogowe i **strony właściwości rozwiązania** okno dialogowe dla projektów Visual Basic i C#, które zawierają jedną Konfiguracja lub dwóch konfiguracji debugowania i wydania. Jeśli projekt ma konfigurację zdefiniowane przez użytkownika, są wyświetlane opcje konfiguracji kompilacji.

Jeśli niezaznaczone, poleceń na **kompilacji** menu, takich jak **Kompiluj rozwiązanie**, **Kompiluj ponownie rozwiązanie**, i **czystą rozwiązania**, są wykonać konfigurację wydania i poleceń na **debugowania** menu, takich jak **Rozpocznij debugowanie** i **uruchomić bez debugowania**, są wykonywane na Konfiguracja debugowania.

### <a name="always-show-solution"></a>Zawsze pokazuj rozwiązania

Po wybraniu rozwiązanie i wszystkie polecenia, które mają wpływ na rozwiązania są zawsze wyświetlane w IDE. Po wyczyszczeniu wszystkich projektów są tworzone jako autonomiczny projekty i rozwiązania w Eksploratorze rozwiązań lub poleceń, które działają nie jest wyświetlany na rozwiązań w środowisku IDE, jeśli rozwiązanie zawiera tylko jeden projekt.

### <a name="save-new-projects-when-created"></a>Zapisz nowe projekty podczas tworzenia

W przypadku wybrania, można określić lokalizację projektu w **nowy projekt** okno dialogowe. Po wyczyszczeniu wszystkich nowych projektów są tworzone jako tymczasowe projekty. Podczas pracy z tymczasowe projekty można tworzyć i eksperymentować projektu bez konieczności określania lokalizacji na dysku.

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Ostrzega użytkownika, gdy lokalizacja projektu nie jest zaufany

Próba utworzenia nowego projektu lub otworzyć istniejącego projektu w lokalizacji, która nie jest w pełni zaufany (na przykład na ścieżkę UNC lub ścieżki HTTP), zostanie wyświetlony komunikat. Ta opcja umożliwia określenie, czy komunikat jest wyświetlany za każdym razem, który przystąpieniem do tworzenia lub otwierania projektu w lokalizacji, która nie jest w pełni zaufany.

### <a name="show-output-window-when-build-starts"></a>Pokaż okno dane wyjściowe, gdy rozpoczyna się kompilacja

Automatycznie wyświetla [okno danych wyjściowych](../../ide/reference/output-window.md) w IDE na początku rozwiązania kompilacji.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Monituj o symboliczną zmianę nazwy podczas zmiany nazwy plików

Po wybraniu programu Visual Studio wyświetla komunikat z pytaniem, czy go należy również zmienić nazwę wszystkich odwołań do projektu do elementu kodu.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Monituj przed przeniesieniem pliki do nowej lokalizacji

Po wybraniu programu Visual Studio wyświetla komunikat potwierdzenia przed lokalizacji plików są zmieniane przez akcje w **Eksploratora rozwiązań**.

### <a name="reopen-documents-on-solution-load"></a>Otwórz dokumenty na ładowania rozwiązania

**Nowa w programie Visual Studio 2017 wersji 15.8 preview 2 lub nowszej**

Po wybraniu, dokumentów, które pozostały Otwórz poprzednio rozwiązanie zostało zamknięte są automatycznie otwierane po otwarciu rozwiązania.

Otworzyć niektórych typów plików lub projektanci można opóźnić ładowania rozwiązania. Usuń zaznaczenie tej opcji, aby [poprawić wydajność obciążenia rozwiązania](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) Jeśli nie chcesz przywrócić poprzedni kontekst tego rozwiązania.

## <a name="locations-page"></a>Lokalizacje strony

Poniższe opcje są dostępne na **lokalizacje** strony.

### <a name="projects-location"></a>Lokalizacja projektów

Określa domyślną lokalizację, w którym program Visual Studio tworzy nowe projekty i rozwiązania folderów. Kilka okien dialogowych również użyć lokalizacji zestawu w tej opcji dla folderu punkty początkowe. Na przykład **Otwórz projekt** okno dialogowe korzysta z tej lokalizacji dla **Moje projekty** skrótów.

### <a name="user-project-templates-location"></a>Lokalizacja szablonów projektu użytkownika

Określa domyślną lokalizację który **nowy projekt** okno dialogowe używa w celu utworzenia listy **Moje szablony**. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Lokalizacja szablonów elementu użytkownika

Określa domyślną lokalizację który **Dodaj nowy element** okno dialogowe używa w celu utworzenia listy **Moje szablony**. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Okno dialogowe Opcje, projekty i rozwiązania, tworzenie i uruchamianie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Okno dialogowe Opcje, projekty i rozwiązania, projekty sieci Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
