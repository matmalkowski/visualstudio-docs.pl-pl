---
title: Debugowanie ASP.NET
description: Debugowanie aplikacji ASP.NET przy użyciu debuger programu Visual Studio
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 5f731e5d40205776682e706aa4e32d988a76f0f0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Szybki Start: Debugowanie ASP.NET przy użyciu debuger programu Visual Studio

Debuger programu Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w debugowaniu aplikacji. Ten temat zawiera szybko dowiedzieć się, niektóre podstawowe funkcje.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#**, wybierz **Web**, a następnie w środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET Core**.

1. Wpisz nazwę, takich jak **MyDbgApp** i kliknij przycisk **OK**.

1. W oknie dialogowym wybierz **aplikacji sieci Web** w środkowym okienku, a następnie kliknij przycisk **OK**.

     Jeśli nie widzisz **aplikacji sieci Web** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **ASP.NET** i **.NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

    ![Wybierz aplikację sieci Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Program Visual Studio tworzy projekt.

1. W Eksploratorze rozwiązań Otwórz About.cshtml.cs (w obszarze Pages/About.cshtml) i Zastąp następujący kod

    ```c#
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    o tym kodzie:

    ```c#
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

A *punktu przerwania* jest znacznika, która wskazuje, gdzie programu Visual Studio należy wstrzymać Twojej pracy kodu, aby móc przeglądać wartości zmiennych ani zachowanie pamięci lub czy nie jest pierwsze uruchom gałąź kodu. Jest najbardziej podstawowa funkcja debugowania.

1. Aby ustawić punkt przerwania, kliknij odstępu na lewo od `doWork` — funkcja (lub zaznacz wiersz kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Punkt przerwania jest ustawiony do lewego nawiasu otwierającego (`{`).

1. Teraz naciśnij **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

1. Podczas ładowania strony sieci web, kliknij przycisk **o** łącze w górnej części strony sieci web.

    Wstrzymuje działanie debugera, którym można ustawić punktu przerwania. Żółta strzałka wskazuje instrukcji, których wykonanie debugera i aplikacji jest wstrzymana. Wiersz z nawiasu otwierającego (`{`) po `doWork` deklaracji funkcji nie ma jeszcze wykonane.

    ![Trafiony punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które często kroków opisanych w, użyj [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. Zaoszczędzić czas, a także ułatwia debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Przejdź do kodu

Istnieją różne polecenia nakazać debugera, aby kontynuować. Polecenie nawigacji przydatne kodu, które jest nowa w programie Visual Studio 2017 zostanie przedstawiony.

Podczas wstrzymana na punkt przerwania, umieść kursor nad instrukcji `return c2` do zielonego **Uruchom, aby kliknij** przycisk ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png) pojawia się, a następnie naciśnij klawisz **Uruchom, aby kliknij** przycisk.

![Uruchom kliknij](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikacja kontynuuje wykonywanie i zatrzyma się w wierszu kodu, gdy kliknięto przycisk.

Typowe polecenia klawiatury używany do kroków kodu obejmują **F10** i **F11**. Aby uzyskać dodatkowe szczegółowe instrukcje, zobacz [przewodnik dla początkujących](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdź zmienne w etykietki danych

1. W bieżącym wierszu kodu (oznaczony przez wskaźnik wykonywania żółty), umieść kursor nad `c2` obiektu za pomocą myszy do Pokaż etykietki danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Etykietek danych pokazuje bieżącą wartość `c2` zmiennej i pozwala sprawdzić jego właściwości. Podczas debugowania, jeśli wartość, która nie jest widoczny, prawdopodobnie usterki w poprzednim lub wywoływania wierszach kodu. 

2. Rozwiń węzeł etykietek danych, aby zobaczyć bieżące wartości właściwości `c2` obiektu.

3. Jeśli chcesz przypiąć etykietek danych, dzięki czemu możesz zobaczyć wartość `c2` podczas wykonywania kodu, kliknij ikonę pinezki mała. (W dogodnej lokalizacji można przenieść przypiętych etykietek danych).

## <a name="edit-code-and-continue-debugging"></a>Edytuj kod i Kontynuuj debugowanie

Po zidentyfikowaniu zmiany, która ma zostać przetestowana w kodzie, gdy w trakcie sesji debugowania, możesz to zrobić, za.

1. W `OnGet` metody, kliknij pozycję drugiego wystąpienia `result.First.Value` i zmienić `result.First.Value` do `result.Last.Value`.

1. Naciśnij klawisz **F10** (lub **Debuguj > Step Over**) kilka razy, aby poprawić debugera i wykonanie kodu edytowany.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Edytuj i Kontynuuj")

    **F10** przesuwa instrukcja debugera jednym na raz, ale kroki za pośrednictwem funkcji zamiast Wkraczanie do nich (nadal wykonuje kod, który możesz pominąć).

Aby uzyskać więcej informacji na temat używania edit-and-continue i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku kiedy znasz już sposobu uruchamiania debugera, kroki do kodu i sprawdzić zmiennych. Możesz pobrać wysokiego poziomu przyjrzeć się debuger funkcji oraz łącza do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
