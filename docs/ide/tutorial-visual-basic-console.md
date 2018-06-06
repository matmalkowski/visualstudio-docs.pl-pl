---
title: Wprowadzenie do języka Visual Basic w programie Visual Studio
ms.custom: ''
ms.date: 12/08/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 228ebc2fd2137b78b44347fa2e03d7ba949a23c7
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764936"
---
# <a name="get-started-with-visual-basic-in-visual-studio"></a>Wprowadzenie do języka Visual Basic w programie Visual Studio

W tym samouczku Visual Basic (VB) można będzie użyć programu Visual Studio do tworzenia i uruchamiania kilka aplikacji w innej konsoli i eksplorować niektóre funkcje [programu Visual Studio zintegrowane środowisko programistyczne (IDE)](visual-studio-ide.md) podczas możesz to zrobić.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

W tym miejscu jest szybkie często zadawane pytania na przedstawiono niektóre podstawowe pojęcia.

### <a name="what-is-visual-basic"></a>Co to jest Visual Basic?

Visual Basic jest bezpieczny język programowania, który ma bardzo łatwe dowiedzieć się więcej. Jest on uzyskiwany z BASIC, co oznacza "Dla początkujących uniwersalny symboliczne Kod instrukcji".

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Visual Studio to zestaw zintegrowanych programowanie wydajności narzędzi dla deweloperów. Go traktować jako program, który służy do tworzenia programy i aplikacje.

### <a name="what-is-a-console-app"></a>Co to jest aplikacja konsoli?

Aplikacja konsoli dane wejściowe i alias wyświetla dane wyjściowe w oknie wiersza polecenia konsoli.

### <a name="what-is-net-core"></a>Co to jest oprogramowanie .NET Core?

Oprogramowanie .NET core to ewolucyjny następny krok programu .NET Framework. Gdzie programu .NET Framework zezwalały na udostępnianie kodu w językach programowania .NET Core dodaje umożliwiają udostępnianie kodu na platformach. Nawet lepiej jest typu open source. (.NET Framework i .NET Core obejmuje bibliotek wbudowane funkcje, jak również środowisko uruchomieniowe języka wspólnego (CLR), która działa jako maszynę wirtualną do uruchamiania kodu).

## <a name="start-developing"></a>Rozpocząć tworzenie

Czy chcesz rozpocząć tworzenie? Chodźmy!

### <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji Visual Basic. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim nawet dodano niczego!

1. Otwórz program Visual Studio 2017 r.

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu**.

3. W **nowy projekt** okno dialogowe w lewym okienku rozwiń **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz **aplikacji konsoli (.NET Core)**. Nadaj nazwę plikowi *HelloWorld*.  

   ![Konsoli szablonu projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Dodaj grupy roboczej (opcjonalnie)

Jeśli nie widzisz **aplikacji konsoli (.NET Core)** szablon projektu, możesz pobrać go przez dodanie **aplikacji dla wielu platform .NET Core** obciążenia. Możesz dodać to obciążenie w jednym z dwóch sposobów, w zależności od zainstalowanych aktualizacji programu Visual Studio 2017 na tym komputerze.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Użyj okna dialogowego Nowy projekt

1. Kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe.

  ![Kliknij łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Uruchamia Instalator programu Visual Studio. Wybierz **aplikacji dla wielu platform .NET Core** obciążenia, a następnie wybierz pozycję **Modyfikuj**.

   ![Obciążenie wiele platform .NET core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anuluj poza **nowy projekt** okna dialogowego polu, a następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

2. Uruchamia Instalator programu Visual Studio. Wybierz **aplikacji dla wielu platform .NET Core** obciążenia, a następnie wybierz pozycję **Modyfikuj**.

## <a name="create-a-what-is-your-name-application"></a>Tworzenie aplikacji "Co to jest nazwa użytkownika"

Utwórz aplikację, która wyświetla monit o podanie nazwy użytkownika, a następnie wyświetli wraz z datą i godziną. Oto jak:

1. Jeśli go nie jest jeszcze otwarty, następnie otwórz Twojej *WhatIsYourName* projektu.

2. Wprowadź poniższy kod Visual Basic natychmiast po nawiasie otwierającym, który następuje `Sub Main(args As String())` wierszu i przed `End Sub` wiersza:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, i <xref:System.Console.ReadKey%2A> instrukcje.

 ![W oknie kod przedstawiający kodu co to jest nazwa użytkownika](../ide/media/vb-codewindow-what-name.png)

3. Po otwarciu okna konsoli, wprowadź nazwę. Okna konsoli powinien wyglądać podobnie do następującego zrzutu ekranu:

   ![Konsoli okna pokazującego co to jest nazwa użytkownika, Data i godzina, a następnie naciśnij dowolny klawisz, aby kontynuować wiadomości](../ide/media/vb-console-what-name.png)

5. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="create-a-calculate-this-application"></a>Utwórz aplikację "Obliczyć to"

1. Otwórz program Visual Studio 2017 r, a następnie na pasku menu u góry wybierz **pliku** > **nowy** > **projektu**.

2. W **nowy projekt** okno dialogowe w lewym okienku rozwiń **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz **aplikacji konsoli (.NET Core)**. Nadaj nazwę plikowi *CalculateThis*.  

3. Wprowadź następujący kod między `Module Program` wiersza i `End Module` wiersza:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

  W oknie Kod powinien wyglądać Poniższy zrzut ekranu:

   ![W oknie kod przedstawiający Calculate ten kod](../ide/media/vb-codewindow-calculate-this.png)

4. Kliknij przycisk **CalculateThis** do uruchomienia programu. Okna konsoli powinien wyglądać podobnie do następującego zrzutu ekranu:       

    ![Okno konsoli przedstawiający CaluculateThis aplikacji, która zawiera monity w akcje, które należy podjąć.](../ide/media/vb-console-calculate-this.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Aby zapoznać się jeszcze bardziej Visual Basic i Visual Studio IDE, zobacz następujące strony.

* [Przewodnik po Visual Basic](/dotnet/visual-basic/index)
* [Nowości w języku Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense dla plików kodu programu Visual Basic](visual-basic-specific-intellisense.md)
* [Dokumentacja języka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Podstawy języka Visual Basic dla początkujących bezwzględną](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507) kursu wideo
