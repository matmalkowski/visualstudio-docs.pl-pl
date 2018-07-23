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
ms.openlocfilehash: ceccf3c051e3c85fa4b8e64ecbc33c388e9a884f
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178183"
---
# <a name="documents-environment-options-dialog-box"></a>Dokumenty, środowisko, opcje — Okno dialogowe
Ta strona **opcje** okno dialogowe, aby kontrolować wyświetlanie dokumentów w zintegrowanym środowisku programistycznym (IDE) i zarządzanie zmianami zewnętrzne dokumenty i pliki. To okno dialogowe można skorzystać, klikając **opcje** na **narzędzia** menu, a następnie wybierając **dokumenty** w **środowiska** węzła. Jeśli **dokumenty** nie ma na liście, wybierz opcję **Pokaż wszystkie ustawienia** w **opcje** okno dialogowe.

> [!NOTE]
> Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się od opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


 **Użyj ponownie bieżące okno dokumentu, jeśli zapisane** po wybraniu zamyka bieżącego dokumentu, jeśli zostały zapisane i zostanie otwarty nowy dokument, w tym samym oknie. Jeśli nie został zapisany bieżącego dokumentu, pozostaje otwarty, a nowy dokument jest otwarty w osobnym oknie. Gdy ta opcja jest zaznaczona, nowe dokumenty zawsze Otwórz w oddzielnych okien.

 Jeśli wykonania wielu dokumentów wycinania i wklejania rzadko i chcesz zminimalizować liczbę otwartych dokumentów i systemu windows w obszarze roboczym, użyj tej opcji.

 **Wykryj, kiedy plik jest zmieniany poza środowiskiem** po wybraniu tej opcji wiadomości natychmiast powiadamia o zmianach w otwartego pliku, które zostały wprowadzone przez Edytor poza IDE. Komunikat informuje, jak ponownie załadować plik z magazynu.

 **Automatyczne ładowanie zmian, jeśli zapisane** , gdy masz **Wykryj, kiedy plik jest zmieniany poza środowiskiem** zaznaczone, a domyślnie generowany jest plikiem otwartym w zmiany w środowisku IDE poza IDE komunikat ostrzegawczy. Jeśli ta opcja jest włączona, zostanie wyświetlone nie ostrzeżenie i dokument zostanie ponownie załadowana w środowisku IDE w celu zastosowania zmian zewnętrznych.

 **Zezwól na edytowanie plików tylko do odczytu. Ostrzegaj przy próbie zapisu** po włączeniu tej opcji można otwierać i edytować plik tylko do odczytu. Gdy to zrobisz, musisz użyć **Zapisz jako**polecenie, aby zapisać plik przez nową nazwę, jeśli chcesz zapisać rekord zmiany.

 **Otwórz plik używając katalogu aktualnie aktywnego dokumentu** po wybraniu tej opcji określa, że **Otwórz plik** okno dialogowe wyświetla katalog aktywnego dokumentu. Gdy ta opcja jest wyczyszczone, **Otwórz plik** okno dialogowe wyświetla katalog ostatnio używany do otwierania pliku.

 **Sprawdź spójność końców wierszy przy ładowaniu** wybierz tę opcję, aby edytora skanowania końce wierszy w pliku i wyświetlić okno komunikatu, jeśli zostaną wykryte niespójności, w jak sformatowane końce wierszy.

 **Wyświetlana ikona ostrzeżenia, gdy globalne cofanie modyfikuje edytowane pliki** wybierz tę opcję, aby wyświetlić komunikat przypadku **globalne cofanie** polecenia wycofa refaktoryzacji zmiany wprowadzone w plikach, które zostały zmienione od Operacja refaktoryzacji. Zwraca plik do stanu refaktoryzacji pre może odrzucić kolejne zmiany wprowadzone w pliku.

 **Pokaż różne pliki w Eksploratorze rozwiązań** wybierz tę opcję, aby wyświetlić **różne pliki** w węźle **Eksploratora rozwiązań**. Różne pliki to pliki, które nie są skojarzone z projektu lub rozwiązania, ale może być wyświetlany w **Eksploratora rozwiązań** dla Twojej wygody.

> [!NOTE]
> Wybierz tę opcję, aby umożliwić **Pokaż w przeglądarce** polecenie **pliku** menu dla dokumentów sieci web, które nie są uwzględnione w aplikacji sieci web usługi active.

 **\<** *n* **> Elementy zapisywane w projekcie plików pozostałych** określa liczbę plików, aby trwale w **MiscellaneousFiles** folderu **Eksploratora rozwiązań**. Te pliki są wyświetlane, nawet jeśli nie są już otwarty w edytorze. Można określić liczbę całkowitą z zakresu od 0 do 256. Wartość domyślna to 0.

 Na przykład, jeśli dla tej opcji do 5, otwartych 10 różne pliki, gdy zamkniesz wszystkie 10 plików 5 pierwszych będzie nadal widoczny we **różne pliki** folderu.

 **Zapisz dokumenty jako Unicode, gdy nie można zapisać danych w stronie kodowej** wybierz tę opcję, aby spowodować, że pliki zawierające informacje niezgodne z wybranej strony kodowej można zapisać w formacie Unicode domyślnie.

## <a name="see-also"></a>Zobacz też

- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
- [Różne pliki](../../ide/reference/miscellaneous-files.md)
- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)