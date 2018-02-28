---
title: "Szybki Start: Tworzenie pierwszej aplikacji konsoli w programie Visual Studio za pomocą Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 2573e1a2344b858b721fb234d6b228b421a36550
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Szybki Start: Tworzenie pierwszej aplikacji konsoli w programie Visual Studio za pomocą Visual Basic
W tej 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację języka Visual Basic, która działa w konsoli programu.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-project"></a>Tworzenie projektu
Najpierw utworzysz projekt aplikacji Visual Basic. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim nawet dodano niczego!

1. Otwórz program Visual Studio 2017 r.

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu...** .

3. W **nowy projekt** okno dialogowe w lewym okienku rozwiń **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz **aplikacji konsoli (.NET Core)**. Następnie nazwą projektu *HelloWorld*.

   ![Konsoli szablonu projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz **aplikacji konsoli (.NET Core)** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe.

   ![Kliknij łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uruchamia Instalator programu Visual Studio. Wybierz **aplikacji dla wielu platform .NET Core** obciążenia, a następnie wybierz pozycję **Modyfikuj**.

     ![Obciążenie wiele platform .NET core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Tworzenie aplikacji
Po wybraniu szablonu projektu języka Visual Basic oraz nazwę projektu, Visual Studio tworzy prostą aplikację "Hello World". Wywołuje <xref:System.Console.WriteLine%2A> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli.

![Wyświetl domyślny kod Hello World z szablonu](../ide/media/vb-console-helloworld-template.png)

Jeśli klikniesz przycisk **HelloWorld** przycisk w IDE, możesz uruchomić program w trybie debugowania.

  ![Kliknij przycisk Hello World, aby uruchomić program w trybie debugowania](../ide/media/vb-console-hello-world-button.png)

Można to zrobić, w oknie konsoli jest widoczna na tylko chwilę przed jego zamknięciem. Zdarza się to `Main` metoda kończy się po wykonaniu jej jednej instrukcji, w związku z czym kończenia aplikacji.

### <a name="add-some-code"></a>Dodawanie kodu
Dodajmy trochę kodu, aby zatrzymać aplikację, a następnie poprosić dla danych wejściowych użytkownika.

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Zatrzymuje program, dopóki naciśnięciu klawisza.

2. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

   Program to kompiluje się na język pośredni (IL), który jest konwertowany na kod binarny za pomocą kompilatora just-in-time (JIT).

## <a name="run-the-application"></a>Uruchamianie aplikacji
1. Kliknij przycisk **HelloWorld** przycisk na pasku narzędzi.

   ![Kliknij przycisk Hello World do uruchomienia programu z paska narzędzi](../ide/media/vb-console-hello-world-button.png)

2. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

   ![Wyświetlana Hello World w oknie konsoli i naciśnij dowolny klawisz, aby kontynuować](../ide/media/vb-console-hello-world-press-any-key.png)

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Mamy nadzieję, że znasz nieco dotyczące języka Visual Basic i Visual Studio IDE. Jeśli chcesz delve głębiej, kontynuuj samouczek w **samouczki** sekcji spisu treści.

## <a name="see-also"></a>Zobacz także
* [Szybki Start: Tworzenie Windows "tekst Hello World" formularzy aplikacji w języku Visual Basic w programie Visual Studio](quickstart-visual-basic-winforms.md)
* [Samouczek: Wprowadzenie do języka Visual Basic w programie Visual Studio](tutorial-visual-basic-console.md)
* [IntelliSense dla plików kodu programu Visual Basic](visual-basic-specific-intellisense.md)
