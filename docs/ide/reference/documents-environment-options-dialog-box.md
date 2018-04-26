---
title: Dokumenty, środowisko, opcje — Okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb14ae44dd137d7bf600cec505fe17fa6e105a42
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="documents-environment-options-dialog-box"></a>Dokumenty, środowisko, opcje — Okno dialogowe
Ta strona **opcje** okno dialogowe, aby kontrolować wyświetlanie dokumentów w zintegrowane środowisko programistyczne (IDE) i zarządzanie zewnętrzne zmiany dokumentów i plików. Dostęp do tego okna dialogowego, klikając **opcje** na **narzędzia** menu, a następnie wybierając **dokumenty** w **środowiska** węzła. Jeśli **dokumenty** nie ma na liście, wybierz opcję **Pokaż wszystkie ustawienia** w **opcje** okno dialogowe.

> [!NOTE]
> Opcje dostępne w oknach dialogowych i nazwy i lokalizacje poleceń menu, które zostanie wyświetlone, może się różnić od co to jest opisany w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


 **Użyj ponownie bieżące okno dokumentu, jeśli zapisane** po wybraniu zamyka bieżący dokument, jeśli został zapisany i zostanie otwarty nowy dokument w tym samym oknie. Jeśli bieżący dokument nie został zapisany, pozostaje otwarty i nowy dokument jest otwarty w osobnym oknie. Gdy ta opcja jest zaznaczona, nowych dokumentów zawsze otwieraj w oddzielnych okien.

 Użyj tej opcji, wykonaj wycinania wielu dokumentów i wklejania rzadko, aby zminimalizować liczbę otwarte dokumenty i systemu windows w obszarze roboczym.

 **Wykryj, kiedy plik jest zmieniany poza środowiskiem** po wybraniu tej opcji wiadomości natychmiast powiadamia o zmianach w otwartego pliku, które zostały wprowadzone przez Edytor poza IDE. Ten komunikat informuje, należy ponownie załadować plik z magazynu.

 **Automatyczne ładowanie zmian, jeśli zapisane** Jeśli masz **Wykryj, kiedy plik jest zmieniany poza środowiskiem** zaznaczone, a plik zmian IDE poza IDE komunikat ostrzegawczy jest generowany domyślnie. Jeśli ta opcja jest włączona, zostanie wyświetlone ostrzeżenie i dokumentu zostanie ponownie załadowana w IDE w celu zastosowania zmian zewnętrznych.

 **Zezwól na edytowanie plików tylko do odczytu. Ostrzegaj przy próbie zapisu** po włączeniu tej opcji można otwierać i edytować plik tylko do odczytu. Gdy skończysz, należy użyć **Zapisz jako**polecenie, aby zapisać plik przez nową nazwę, jeśli chcesz zapisać rekord zmiany.

 **Otwórz plik używając katalogu aktualnie aktywnego dokumentu** po wybraniu tej opcji oznacza, że **Otwórz plik** okno dialogowe wyświetla katalog aktywnego dokumentu. Gdy ta opcja jest zaznaczona, **Otwieranie pliku** okno dialogowe wyświetla katalog ostatnio używany do otwierania pliku.

 **Sprawdź spójność zakończenia wierszy przy ładowaniu** wybierz tę opcję, aby edytora skanowania zakończenia wierszy w pliku i wyświetlać okno komunikatu, jeśli zostaną wykryte niespójności w sposób zakończenia wierszy są sformatowane.

 **Wyświetl ostrzeżenie, gdy globalne cofanie modyfikuje edytowane pliki** wybierz tę opcję, aby wyświetlić komunikat dialogowe **globalne cofanie** polecenia cofnie refaktoryzacji zmiany wprowadzone w plikach, które zostały zmienione od Operacja refaktoryzacji. Zwracanie pliku do stanu sprzed refaktoryzacji elementu może odrzucić kolejne zmiany wprowadzone w pliku.

 **Pokaż różne pliki w Eksploratorze rozwiązań** wybierz tę opcję, aby wyświetlić **różne pliki** w węźle **Eksploratora rozwiązań**. Różne pliki to pliki, które nie są skojarzone z projektu lub rozwiązania, ale może występować w **Eksploratora rozwiązań** dla Twojej wygody.

> [!NOTE]
> Wybierz tę opcję, aby włączyć **Wyświetl w przeglądarce** na **pliku** menu dla dokumentów sieci Web nie jest uwzględniony w aktywnej aplikacji sieci Web.

 **\<** *n* **> Elementy zapisywane w projekcie plików pozostałych** określa liczbę plików, aby trwale w **MiscellaneousFiles** folderu **Eksploratora rozwiązań**. Pliki te są wyświetlane, nawet jeśli nie są już otwarty w edytorze. Można określić liczbę całkowitą z zakresu od 0 do 256. Wartość domyślna to 0.

 Na przykład jeśli Ustaw tę opcję na wartość 5 i otworzył 10 różne pliki, po zamknięciu wszystkich plików 10, 5 pierwszych będą nadal wyświetlane w **różne pliki** folderu.

 **Zapisz dokumenty jako Unicode, gdy nie można zapisać danych w stronie kodowej** wybierz tę opcję, aby spowodować, że pliki zawierające informacje niezgodne z wybranych stronę kodową do zapisania jako Unicode domyślnie.

## <a name="see-also"></a>Zobacz też

- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
- [Różne pliki](../../ide/reference/miscellaneous-files.md)
- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)