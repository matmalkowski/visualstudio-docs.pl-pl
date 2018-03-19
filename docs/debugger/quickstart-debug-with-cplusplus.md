---
title: "Debugowania z C++ za pomocą debugera programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fce20f8c17b52b109b469bd439905e0edd66c9d3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="debug-with-c-using-the-visual-studio-debugger"></a>Debugowania z C++ za pomocą debugera programu Visual Studio

Debuger programu Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w debugowaniu aplikacji. Ten temat zawiera szybko dowiedzieć się, niektóre podstawowe funkcje.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

2. W obszarze **Visual C++**, wybierz **Windows Desktop**, a następnie w środkowym okienku wybierz **aplikacji konsoli systemu Windows**.

    Jeśli nie widzisz **aplikacji konsoli systemu Windows** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **tworzenia klasycznych aplikacji w języku C++** obciążenia, a następnie wybierz **Modyfikuj**.

3. Wpisz nazwę, takich jak **MyDbgApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

4. W MyDbgApp.cpp Zastąp następujący kod

    ```c++
    int main()
    {
        return 0;
    }
    ```

    z tego kodu (nie usuwaj `#include "stdafx.h"`):

    ```c++
    #include <list>  
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

A *punktu przerwania* jest znacznika, która wskazuje, gdzie programu Visual Studio należy wstrzymać Twojej pracy kodu, aby móc przeglądać wartości zmiennych ani zachowanie pamięci lub czy nie jest pierwsze uruchom gałąź kodu. Jest najbardziej podstawowa funkcja debugowania.

1. Aby ustawić punkt przerwania, kliknij odstępu na lewo od `doWork` wywołania funkcji (lub zaznacz wiersz kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint.png "Ustaw punkt przerwania")

2. Teraz naciśnij **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

    ![Trafiony punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint.png "trafiony punkt przerwania")

    Wstrzymuje działanie debugera, którym można ustawić punktu przerwania. Żółta strzałka wskazuje instrukcji, których wykonanie debugera i aplikacji jest wstrzymana. Wiersz z `doWork` wywołanie funkcji nie ma jeszcze wykonane.

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które często kroków opisanych w, użyj [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. Warunkowych punktów przerwania zaoszczędzić czas, a także ułatwia debugowanie problemów, które są trudne do odtworzenia.

    Podczas próby debugowania błędy związane z pamięcią w języku C++, umożliwia także punktów przerwania do zbadania wartości adresów (poszukaj NULL) i referencyjne liczby. 

## <a name="navigate-code"></a>Przejdź do kodu

Istnieją różne polecenia nakazać debugera, aby kontynuować. Polecenie nawigacji przydatne kodu, które jest nowa w programie Visual Studio 2017 zostanie przedstawiony.

Podczas wstrzymana na punkt przerwania, umieść kursor nad instrukcji `c1.push_back(20)` do zielonego **Uruchom, aby kliknij** przycisk ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png "RunToClick") pojawia się, a następnie naciśnij klawisz **Uruchom, aby kliknij** przycisku.

![Uruchom, aby kliknij](../debugger/media/dbg-qs-run-to-click.png "Uruchom, aby kliknij")

Aplikacja kontynuuje wykonywanie, wywoływania `doWork`i zatrzymuje się na wiersz kodu, gdy kliknięto przycisk.

Typowe polecenia klawiatury używany do kroków kodu obejmują **F10** i **F11**. Aby uzyskać dodatkowe szczegółowe instrukcje, zobacz [przewodnik dla początkujących](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdź zmienne w etykietki danych

1. W bieżącym wierszu kodu (oznaczony przez wskaźnik wykonywania żółty), umieść kursor nad `c1` obiektu za pomocą myszy do Pokaż etykietki danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip.png "wyświetlenia etykietki danych")

    Etykietek danych pokazuje bieżącą wartość `c1` zmiennej i pozwala sprawdzić jego właściwości. Podczas debugowania, jeśli wartość, która nie jest widoczny, prawdopodobnie usterki w poprzednim lub wywoływania wierszach kodu. 

2. Rozwiń węzeł etykietek danych, aby zobaczyć bieżące wartości właściwości `c1` obiektu.

3. Jeśli chcesz przypiąć etykietek danych, dzięki czemu możesz zobaczyć wartość `c1` podczas wykonywania kodu, kliknij ikonę pinezki mała. (W dogodnej lokalizacji można przenieść przypiętych etykietek danych).

## <a name="edit-code-and-continue-debugging"></a>Edytuj kod i Kontynuuj debugowanie

Po zidentyfikowaniu zmiany, która ma zostać przetestowana w kodzie, gdy w trakcie sesji debugowania, możesz to zrobić, za.

1. Kliknij pozycję drugiego wystąpienia `c2.front()` i zmienić `c2.front()` do `c2.back()`.

2. Naciśnij klawisz **F10** (lub **Debuguj > Step Over**) kilka razy, aby poprawić debugera i wykonanie kodu edytowany.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue.gif "Edytuj i Kontynuuj")

    **F10** przesuwa instrukcja debugera jednym na raz, ale kroki za pośrednictwem funkcji zamiast Wkraczanie do nich (nadal wykonuje kod, który możesz pominąć).

Aby uzyskać więcej informacji na temat używania edit-and-continue i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku kiedy znasz już sposobu uruchamiania debugera, kroki do kodu i sprawdzić zmiennych. Możesz pobrać wysokiego poziomu przyjrzeć się debuger funkcji oraz łącza do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
