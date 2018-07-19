---
ms.topic: include
ms.openlocfilehash: 37079cfaa1204cd8ce7a77e1e2f5aa91ea844ea5
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809421"
---
1. Uruchom program Visual Studio i wybierz **Plik > Nowy > Projekt**.

1. W **nowy projekt** okno dialogowe, wyszukaj "Python", wybierz szablon "Z poziomu kodu Python istniejące", należy nadać projektowi nazwę i lokalizację, a następnie wybierz **OK**.

1. W oknie kreatora należy ustawić ścieżkę do istniejącego kodu, ustawić filtr dla typów plików i określić wszelkie ścieżki wyszukiwania, które projektu wymaga, a następnie wybierz **dalej**. Jeśli nie wiesz, jakie wyszukiwania ścieżki, pozostaw to pole puste.

    ![Nowy projekt z istniejącego kodu, krok 1](../media/projects-from-existing-1.png)

1. W następnym oknie dialogowym Wybierz plik startowy dla projektu i wybierz **dalej**. (Jeśli to konieczne, wybierz środowisko; w przeciwnym razie Zaakceptuj ustawienia domyślne.) Należy pamiętać, że okno dialogowe zawiera tylko pliki w folderze głównym; Jeśli żądany plik znajduje się w podfolderze, pozostaw pusty plik startowy i ustaw go później w Eksploratorze rozwiązań (opisanych poniżej).

    ![Nowy projekt z istniejącego kodu, krok 2](../media/projects-from-existing-2.png)

1. Wybierz lokalizację, w której chcesz zapisać plik projektu (czyli `.pyproj` pliku na dysku). Jeśli to konieczne, możesz również obejmować automatyczne wykrywanie środowisk wirtualnych i dostosować projekt dla innej witryny sieci web platform. Jeśli masz pewności co do tych opcji, należy pozostawić je ustawiane na wartości domyślne.

    ![Nowy projekt z istniejącego kodu, krok 3](../media/projects-from-existing-3.png)

1. Wybierz **Zakończ** i Visual Studio tworzy projekt i otworzy go w Eksploratorze rozwiązań. Jeśli chcesz przenieść `.pyproj` pliku w innym miejscu, zaznacz ją w Eksploratorze rozwiązań i wybierz **Plik > Zapisz jako**. Ta akcja aktualizacji odwołania do pliku w projekcie, ale nie przenosi wszystkie pliki kodu.

1. Aby ustawić innego pliku startowego, zlokalizuj plik w Eksploratorze rozwiązań, kliknij prawym przyciskiem myszy i wybierz pozycję **Ustaw jako plik startowy**.