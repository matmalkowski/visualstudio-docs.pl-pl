---
title: Synchronizuj ustawienia
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 633767e66a4b3d976999574c885a3e6f7a06ddcf
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766132"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizacja ustawień w Visual Studio na wielu komputerach

Po zalogowaniu do programu Visual Studio na wielu komputerach przy użyciu tego samego konta personalizacji, ustawienia mogą być synchronizowane między komputerami.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia

Domyślnie synchronizowane są następujące ustawienia:

- Ustawienia środowiska deweloperskiego. Należy wybrać zestaw ustawień przy pierwszym uruchomieniu programu Visual Studio, ale można zmienić zaznaczenia w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

- Aliasy poleceń zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji na temat definiowania aliasy poleceń, zobacz [programu Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

- Układów okien zdefiniowanych przez użytkownika w **okna** > **Zarządzanie układów okien** strony.

- Następujące opcje w **narzędzia** > **opcje** stron:

   - Motyw ustawienia i menu paska wielkości liter na **środowiska** > **ogólne** strona Opcje.

   - Wszystkie ustawienia na **środowiska** > **czcionki i kolory** strona Opcje.

   - Wszystkie skróty klawiaturowe w **środowiska** > **klawiatury** strona Opcje.

   - Wszystkie ustawienia na **środowiska** > **zakładek i okien** strona Opcje.

   - Wszystkie ustawienia na **środowiska** > **uruchamiania** strona Opcje.

   - Wszystkie ustawienia na **Edytor tekstu** Opcje strony.

   - Wszystkie ustawienia na **projektanta XAML** Opcje strony.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Wyłącz synchronizowane ustawienia na określonym komputerze

Zsynchronizowane ustawienia dla programu Visual Studio jest domyślnie włączona. Zsynchronizowane ustawienia na komputerze można wyłączyć, przechodząc do **narzędzia** > **opcje** > **środowiska**  >   **Konta** strony i usunięcie zaznaczenia **synchronizację ustawień między urządzeniami po zalogowaniu do programu Visual Studio**. Na przykład jeśli nie chcesz synchronizować ustawienia programu Visual Studio na komputerze "A", zmiany ustawień na komputerze "A" nie są wyświetlane na komputerze "B" lub "C". Komputery, "B" i "C" będą w dalszym ciągu synchronizacji ze sobą, ale nie z komputera "A".

## <a name="reset-settings"></a>Zresetuj ustawienia

Można zresetować wszystkie ustawienia w kolekcji ustawień domyślnych, wykonaj następujące czynności:

1. W programie Visual Studio, wybierz **narzędzia** > **Import i eksport ustawień** otworzyć **Kreator importowania i eksportowania ustawień**.

1. W **Kreator importowania i eksportowania ustawień**, wybierz pozycję **zresetować wszystkie ustawienia** , a następnie wybierz **dalej**.

   ![Kreator importowania i eksportowania ustawień w programie Visual Studio](media/reset-all-settings.png)

1. Na **zapisać bieżące ustawienia** wybierz opcję **tak** lub **nr** , a następnie wybierz **dalej**.

1. Na **wybierz kolekcję z ustawień domyślnych** strony, wybierz kolekcję, a następnie wybierz **Zakończ**.

   ![Ustawienia kolekcji w programie Visual Studio](media/settings-collections.png)

1. Na **zresetować pełną** wybierz pozycję **Zamknij**.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizacja ustawień w produktach z rodziny Visual Studio oraz wersje

Ustawienia mogą być synchronizowane w dowolnej wersji programu Visual Studio, w tym Community edition. Ustawienia są synchronizowane między rodziny produktów Visual Studio. Jednak każdy z tych rodziny produktów może mieć własne ustawienia, które nie są współużytkowane z programem Visual Studio. Na przykład ustawienia właściwe dla jednego produktu na komputerze, który "A" są współużytkowane z innym produktem na komputerze "B", ale nie z programem Visual Studio na komputerach "A" lub "B".

## <a name="side-by-side-synchronized-settings"></a>Zsynchronizowane ustawienia Side-by-side

W wersji Visual Studio 2017 15.3 i nowszych niektórych ustawień, takich jak układ okna narzędzia nie są współużytkowane przez różnych side-by-side instalacji programu Visual Studio 2017 r. *CurrentSettings.vssettings* w pliku *%userprofile%\Documents\Visual 2017\Settings w Studio* znajduje się w folderze specyficznych dla instalacji, która jest podobna do *%localappdata%\ Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Aby korzystać z nowych ustawień specyficznych dla instalacji, czy nowa instalacja. Po wykonaniu uaktualnienia do najnowszej aktualizacji istniejącej instalacji programu Visual Studio 2017 używa istniejącej lokalizacji udostępnionej.

Jeśli obecnie korzystają z instalacji programu Visual Studio 2017 side-by-side i chcesz użyć do nowej lokalizacji pliku ustawień specyficznych dla instalacji, wykonaj następujące kroki:

1. Uaktualnienie do programu Visual Studio 2017 wersji 15.3 lub nowszej.

1. Użyj **ustawienia Import\Export** kreatora można wyeksportować wszystkie istniejące ustawienia do określonej lokalizacji poza *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* folderu.

1. Otwórz **wiersz polecenia dla programu VS 2017 deweloperów** uaktualnionego instalacji programu Visual Studio i uruchom `devenv /resetuserdata`.

1. Uruchom program Visual Studio i zaimportuj zapisane ustawienia z wyeksportowanego pliku ustawień.

## <a name="see-also"></a>Zobacz także

[Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
