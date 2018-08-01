---
title: 'Porady: otwieranie wielu rozwiązań'
description: Dowiedz się, jak otworzyć więcej niż jednego rozwiązania w programie Visual Studio dla komputerów Mac i jak otworzyć więcej niż jedno wystąpienie aplikacji.
author: asb3993
ms.author: amburns
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 85d300c5131dad2d6f4480fceb4770e2e8a126a5
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39391585"
---
# <a name="opening-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otwieranie wielu rozwiązań lub wystąpienia programu Visual Studio dla komputerów Mac

Domyślnie wszystkie aplikacje na komputerze Mac, w tym Visual Studio dla komputerów Mac, są _jednego wystąpienia_ aplikacji. Oznacza to, że jeśli aplikacji, którą chcesz używać jest już otwarty (zilustrowane "dot" pod ikoną w obszarze dock), klikając ikonę ponownie otworzy uruchomionego wystąpienia, a nie nowy.  Jeśli potrzebujesz dodatkowych wystąpień aplikacji, możesz też monitować systemu, aby go otworzyć, zgodnie z opisem w [następnej sekcji](#open-a-second-instance-of-visual-studio-for-mac).

Ponadto po otwarciu rozwiązania, zachowanie domyślne jest Otwórz rozwiązanie w nowy obszar roboczy i Zamknij bieżący obszar roboczy (jeśli jest to konieczne). To zachowanie domyślne można przesłonić, przechowując bieżącego obszaru roboczego otwarte, zgodnie z opisem w [Otwórz drugie rozwiązanie](#open-a-second-solution-inside-a-single-instance) sekcji.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Otwórz drugie wystąpienie programu Visual Studio dla komputerów Mac

Aby otworzyć drugiego wystąpienia IDE, otwórz **terminalu** aplikacji i wprowadź następujący wiersz:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otwórz drugie rozwiązanie wewnątrz pojedynczego wystąpienia

Aby otworzyć drugiego rozwiązań razem swoje pierwsze rozwiązanie, użyj następujących kroków:

1. Swoje pierwsze rozwiązanie już jest otwarty, wybierz **Plik > Otwórz**.
2. Przeglądaj system plików można znaleźć istniejącego rozwiązania.
3. Wybierz **.sln** pliku i naciśnij klawisz **opcje** przycisku:
    
    ![Lokalizacja przycisku opcji](media/open-multiple-solutions-image3.png)
4. Usuń zaznaczenie **Zamknij bieżący obszar roboczy** pola:

    ![Zrzut ekranu przedstawiający bieżącego obszaru roboczego](media/open-multiple-solutions-image1.png)

1. Naciśnij przycisk Otwórz, aby otworzyć rozwiązanie drugi w konsoli rozwiązania.

**Można również**, jeśli zostało ostatnio otwarte rozwiązanie, można użyć następujących czynności:

1. Przejdź do pliku > element menu ostatnio używane rozwiązania:

    ![Zrzut ekranu przedstawiający menu ostatnio używane rozwiązania](media/open-multiple-solutions-image2.png)

1. Naciśnij i przytrzymaj **Ctrl** klucza, a następnie wybierz rozwiązanie. Ta kombinacja otwiera drugie rozwiązanie, w konsoli rozwiązania.
