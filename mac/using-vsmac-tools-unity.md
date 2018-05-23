---
title: Przy użyciu programu Visual Studio Mac Tools for Unity
description: W tym przewodniku opisano, jak używać programu Visual Studio dla komputerów Mac narzędzi dla rozszerzenia Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: ab605b3a8505ac189bc0f628b717c6863f9fd902
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Przy użyciu programu Visual Studio Mac Tools for Unity

W tej sekcji dowiesz się, jak używać programu Visual Studio dla komputerów Mac narzędzi do integracji i funkcje produktywności firmy Unity i sposobu korzystania z programu Visual Studio dla komputerów Mac debugera do tworzenia aplikacji platformy Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otwieranie skrypty środowiska Unity w programie Visual Studio dla komputerów Mac

Po Visual Studio for Mac [edytorem skryptu zewnętrznego dla Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otwarcie dowolnego skryptu z Edytor platformy Unity spowoduje automatyczne uruchomienie lub Otwórz przełącznika dla programu Visual Studio dla komputerów Mac przy użyciu wybranego skryptu.

Alternatywnie programu Visual Studio for Mac można otworzyć za pomocą skryptu otwarty w edytorze źródła, wybierając **otworzyć projektu C#** z **zasoby** menu w Unity.

![Otwórz projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji Unity

Programu Visual Studio for Mac Tools for Unity obejmuje skrót do uzyskiwania dostępu do dokumentacji interfejsu API platformy Unity. Aby uzyskać dostęp do dokumentacji interfejsu API środowiska Unity w programie Visual Studio dla komputerów Mac, umieść kursor nad interfejsu API Unity, aby dowiedzieć się o, a następnie naciśnij klawisz **⌘ polecenia + "**.

## <a name="intellisense-for-unity-messages"></a>IntelliSense dla komunikatów Unity
Aparat Unity wysyła komunikaty do skryptów MonoBehaviour, co umożliwia deweloperom do pisania kodu, który reaguje na komunikaty, takie jak OnMouseDown, OnTriggerEnter itp. Ponieważ nie są one wirtualnej metody w klasie podstawowej MonoBehaviour, niektóre IDEs, takich jak MonoDevelop brakuje funkcji uzupełniania kodu dla Unity wiadomości.

Jednak programu Visual Studio for Mac Tools for Unity rozszerza jego funkcje IntelliSense do wiadomości Unity. Ułatwia wdrożenie Unity wiadomości w skryptach MonoBehaviour i pomaga w learning Unity API. Aby użyć IntelliSense dla Unity komunikatów:

1.  Umieść kursor w nowym wierszu wewnątrz treści klasy, która jest pochodną MonoBehaviour.

2.  Rozpocznij wpisywanie nazwy Unity komunikatu, takich jak `OnTriggerEnter`.

3.  Raz litery "**czcionki**" wpisaniu, zostanie wyświetlona lista sugestie IntelliSense.

  ![Korzystanie z IntelliSense](media/using-vsmac-tools-unity-image2.png)

4.  Wybór na liście można zmienić na trzy sposoby:

    * Z **się** i **dół** klawiszy strzałek.

    * Po kliknięciu myszą na żądany element.

    * Kontynuując wpisz nazwę żądanego elementu.

5.  IntelliSense można wstawić wybranych wiadomości Unity, w tym wszelkie wymagane parametry:

    * Naciskając **kartę**.

    * Naciskając **zwracać**.

    * Klikając wybrany element.

  ![Wstaw Unity wiadomości z IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Dodawanie nowych Unity plików i folderów

Podczas można dodać nowe pliki do projektu środowiska Unity w edytorze Unity, Visual Studio for Mac umożliwia łatwe tworzenie nowego skryptów Unity, programów do cieniowania i foldery z poziomu programu Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Dodaj nowy skrypt MonoBehaviour C#

Aby dodać nowy skrypt MonoBehaviour C#, **kliknij prawym przyciskiem myszy folder na zasoby** lub jeden z jego podkatalogów w konsoli rozwiązania i wybierz **Dodaj > Nowy MonoBehaviour**.

![Dodaj nowy MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Dodaj nowy cieniowania Unity

Aby dodać nowy cieniowania Unity, **kliknij prawym przyciskiem myszy folder na zasoby** lub podkatalogu w konsoli rozwiązania i wybierz **Dodaj -> Nowy programu do cieniowania**.

### <a name="add-a-new-folder"></a>Dodaj nowy folder

Aby dodać nowy folder **kliknij prawym przyciskiem myszy folder na zasoby** lub podkatalogu w konsoli rozwiązania i wybierz **Dodaj > Nowy Folder**.

Te dodatki są uwzględniane w oknie Edytor platformy Unity projektu.

### <a name="to-rename-a-file-or-folder"></a>Aby zmienić nazwę pliku lub folderu
**Kliknij prawym przyciskiem myszy** element, aby zmienić nazwę w rozwiązaniu konsoli, a następnie wybierz **zmienić...** .

> [!NOTE]
> Jeśli masz nowy projekt platformy Unity z żadnych skryptów i folder zasobów nie jest wyświetlany w konsoli rozwiązania w programie Visual Studio dla komputerów Mac, należy dodać początkowej C# skrypt w edytorze Unity.

## <a name="unity-debugging"></a>Debugowanie Unity

Projekty platformy Unity może być debugowany przy użyciu programu Visual Studio dla komputerów Mac.

### <a name="start-debugging"></a>Rozpocznij debugowanie

Można rozpocząć debugowania:

1.  Połączenie programu Visual Studio z Unity przez kliknięcie **odtwarzanie** przycisku lub typ **polecenia + Return**, lub **F5**.

  ![Kliknij przycisk Odtwórz w programie Visual Studio](media/using-vsmac-tools-unity-image5.png)

2.  Przełączanie do środowiska Unity i kliknij przycisk **odtwarzanie** przycisku do uruchomienia gry w edytorze.

  ![Kliknij przycisk Odtwórz w Unity](media/using-vsmac-tools-unity-image6.png)

3.  Podczas gry działa edytor platformy Unity podczas połączenia z programu Visual Studio, wszystkie punkty przerwania napotkał będzie zatrzymać wykonywanie gry i wywołać wiersz kodu, w którym gry trafiony punkt przerwania w programie Visual Studio dla komputerów Mac.

### <a name="stop-debugging"></a>Zatrzymaj debugowanie

Aby zatrzymać debugowanie:

1.  Kliknij przycisk **zatrzymać** przycisk w Visual Studio for Mac lub naciśnij przycisk **Shift + Command + zwracać**.

  ![Kliknij przycisk Stop w Visual Studio](media/using-vsmac-tools-unity-image7.png)

Aby dowiedzieć się więcej na temat debugowania w programie Visual Studio dla komputerów Mac, zobacz [korzystanie z debugera](https://docs.microsoft.com/visualstudio/mac/debugging).
