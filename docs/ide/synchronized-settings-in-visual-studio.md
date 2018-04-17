---
title: Synchronizację ustawień w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/23/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0f289fb10cfdbd79a639247a3d14a5a8ced6c10
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="synchronize-your-settings-in-visual-studio"></a>Synchronizację ustawień w programie Visual Studio

Po zalogowaniu się do programu Visual Studio na wielu komputerach przy użyciu tego samego konta personalizacji, domyślne ustawienia są synchronizowane na wszystkich komputerach.

## <a name="synchronized-settings"></a>Zsynchronizowane ustawienia

Następujące ustawienia są domyślnie synchronizowane.

- Ustawienia środowiska deweloperskiego (należy wybrać zestaw ustawień przy pierwszym uruchomieniu programu Visual Studio, ale można zmienić zaznaczenia w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).)

- Następujące opcje w **narzędzia &#124; opcje** stron:

    - **Motyw** i paska na wielkość liter ustawienia menu **środowiska**, **ogólne** strona Opcje

    - Wszystkie ustawienia na **środowiska**, **czcionki i kolory** strona Opcje

    - Wszystkie skróty klawiaturowe, na **środowiska**, **klawiatury** strona Opcje

    - Wszystkie ustawienia na **środowiska, zakładek i okien** strona Opcje

    - Wszystkie ustawienia na **środowiska**, **uruchamiania** strona Opcje

    - Wszystkie ustawienia na **Edytor tekstu** Opcje strony

    - Wszystkie ustawienia na **projektanta XAML** Opcje strony

- Aliasy poleceń zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji na temat definiowania aliasy poleceń, zobacz [programu Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

- Układów okien zdefiniowanych przez użytkownika w **okna &#124; Zarządzanie układów okien** strony

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Wyłącz synchronizowane ustawienia na określonym komputerze

Zsynchronizowane ustawienia dla programu Visual Studio jest domyślnie włączona. Zsynchronizowane ustawienia na komputerze można wyłączyć, przechodząc do **narzędzia &#124; opcje &#124; środowiska &#124; kont** strony i usunięcie zaznaczenia pola wyboru.  Na przykład, jeśli nie chcesz synchronizować ustawienia programu Visual Studio na komputerze A, zmiany ustawień wprowadzone na komputerze czy, nie pojawiają się na komputerze B lub komputerze C. komputerze B i C będzie synchronizować ze sobą, ale nie z komputera A.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizacja ustawień w produktach z rodziny Visual Studio oraz wersje

Ustawienia mogą być synchronizowane w dowolnej wersji programu Visual Studio, w tym Community edition. Ustawienia są synchronizowane między rodziny produktów Visual Studio. Jednak każdy z tych rodziny produktów może mieć własne ustawienia, które nie są współużytkowane z programem Visual Studio. Na przykład ustawienia właściwe dla jednego produktu na komputerze A będą udostępniane innym na komputerze B, ale nie z programem Visual Studio na komputerze A lub b

## <a name="side-by-side-synchronized-settings"></a>Zsynchronizowane ustawienia Side-by-side

W programie Visual Studio 15 ustęp 3 i nowszych zostały zatrzymania udostępniania niektórych ustawień, takich jak układ okna narzędzia, różnych instalacjach programu Visual Studio 2017 side-by-side, zmieniając lokalizację `CurrentSettings.vssettings` w pliku `%userprofile%\Documents\Visual Studio 2017\Settings` do określonych instalacji folder, który jest podobny do `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings`.

**Uwaga**: Aby nowe określone ustawienia instalacji, należy wykonać nową instalację. W przypadku uaktualniania istniejącej instalacji programu Visual Studio 2017 do najnowszej aktualizacji zostanie użyta istniejąca lokalizacja udostępniona. Jeśli obecnie korzystają z instalacji programu Visual Studio 2017 side-by-side i zdecydować, uaktualniania i chcesz użyć do nowej lokalizacji pliku instalacyjnego konkretne ustawienia, wykonaj następujące kroki:

1. Po uaktualnieniu, należy użyć Kreatora ustawień Import\Export można wyeksportować wszystkich naszych istniejących ustawień do określonej lokalizacji poza `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx` folderu.
2. Otwórz **wiersz polecenia dla programu VS 2017 deweloperów** uaktualnionego instalacji programu Visual Studio i uruchom `devenv /resetuserdata` od niego.
3. Uruchom program Visual Studio i zaimportuj zapisane ustawienia z wyeksportowanego pliku ustawień.

## <a name="see-also"></a>Zobacz także

[Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
