---
title: "Debugowanie przy użyciu kodu zarządzanego za pomocą debugera programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: aa992c0cdcf5c50208aacc8e16d954f4ee35da13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-with-managed-code-using-the-visual-studio-debugger"></a>Debugowanie przy użyciu kodu zarządzanego za pomocą debugera programu Visual Studio

Debuger programu Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w debugowaniu aplikacji. Ten temat zawiera szybko dowiedzieć się, niektóre podstawowe funkcje.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

2. W obszarze **Visual C#** lub **Visual Basic**, wybierz **.NET Core**, a następnie w środkowym okienku wybierz **aplikacji konsoli (.NET Core)**.

     Jeśli nie widzisz **aplikacji konsoli (.NET Core)** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **tworzenia klasycznych aplikacji .NET** i **.NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

3. Wpisz nazwę, takich jak **MyDbgApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

4. W pliku Program.cs lub Module1.vb Zastąp następujący kod

    ```c#
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    o tym kodzie:

    ```c#
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > W języku Visual Basic, upewnij się, ma ustawioną wartość obiektu uruchamiania `Sub Main` (**właściwości > aplikacji > obiekt uruchomieniowy**).

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

A *punktu przerwania* jest znacznika, która wskazuje, gdzie programu Visual Studio należy wstrzymać Twojej pracy kodu, aby móc przeglądać wartości zmiennych ani zachowanie pamięci lub czy nie jest pierwsze uruchom gałąź kodu. Jest najbardziej podstawowa funkcja debugowania.

1. Aby ustawić punkt przerwania, kliknij odstępu na lewo od `doWork` wywołania funkcji (lub zaznacz wiersz kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Ustaw punkt przerwania")

2. Teraz naciśnij **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

    ![Trafiony punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "trafiony punkt przerwania")

    Wstrzymuje działanie debugera, którym można ustawić punktu przerwania. Żółta strzałka wskazuje instrukcji, których wykonanie debugera i aplikacji jest wstrzymana. Wiersz z `doWork` wywołanie funkcji nie ma jeszcze wykonane.

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które często kroków opisanych w, użyj [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. Zaoszczędzić czas, a także ułatwia debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Przejdź do kodu

Istnieją różne polecenia nakazać debugera, aby kontynuować. Polecenie nawigacji przydatne kodu, które jest nowa w programie Visual Studio 2017 w tekście.

- Podczas wstrzymana na punkt przerwania, umieść kursor nad instrukcji `c1.AddLast(20)` do zielonego **Uruchom, aby kliknij** przycisk ![Uruchom kliknięcie](../debugger/media/dbg-tour-run-to-click.png "RunToClick") pojawia się, a następnie naciśnij klawisz **Uruchom, aby kliknij** przycisku.

    ![Uruchom, aby kliknij](../debugger/media/dbg-qs-run-to-click-csharp.png "Uruchom, aby kliknij")

    Aplikacja kontynuuje wykonywanie, wywoływania `doWork`i zatrzymuje się na wiersz kodu, gdy kliknięto przycisk.

    Typowe polecenia klawiatury używany do kroków kodu obejmują **F10** i **F11**. Aby uzyskać dodatkowe szczegółowe instrukcje, zobacz [przewodnik dla początkujących](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdź zmienne w etykietki danych

1. W bieżącym wierszu kodu (oznaczony przez wskaźnik wykonywania żółty), umieść kursor nad `c1` obiektu za pomocą myszy do Pokaż etykietki danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip-csharp.png "wyświetlenia etykietki danych")

    Etykietek danych pokazuje bieżącą wartość `c1` zmiennej i pozwala sprawdzić jego właściwości. Podczas debugowania, jeśli wartość, która nie jest widoczny, prawdopodobnie usterki w poprzednim lub wywoływania wierszach kodu. 

2. Rozwiń węzeł etykietek danych, aby zobaczyć bieżące wartości właściwości `c1` obiektu.

3. Jeśli chcesz przypiąć etykietek danych, dzięki czemu możesz zobaczyć wartość `c1` podczas wykonywania kodu, kliknij ikonę pinezki mała. (W dogodnej lokalizacji można przenieść przypiętych etykietek danych).

## <a name="edit-code-and-continue-debugging"></a>Edytuj kod i Kontynuuj debugowanie

Po zidentyfikowaniu zmiany, która ma zostać przetestowana w kodzie, gdy w trakcie sesji debugowania, możesz to zrobić, za.

1. Kliknij pozycję drugiego wystąpienia `c2.First.Value` i zmienić `c2.First.Value` do `c2.Last.Value`.

2. Naciśnij klawisz **F10** (lub **Debuguj > Step Over**) kilka razy, aby poprawić debugera i wykonanie kodu edytowany.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edytuj i Kontynuuj")

    **F10** przesuwa instrukcja debugera jednym na raz, ale kroki za pośrednictwem funkcji zamiast Wkraczanie do nich (nadal wykonuje kod, który możesz pominąć).

Aby uzyskać więcej informacji na temat używania edit-and-continue i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

- Aby dowiedzieć się więcej na temat debugera, zobacz [uruchomienia debugera i przejdź do kodu](../debugger/getting-started-with-the-debugger.md).
- Aby dowiedzieć się więcej na temat punktów przerwania, zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)
