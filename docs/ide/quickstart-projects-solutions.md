---
title: Wprowadzenie do projektów i rozwiązań w programie Visual Studio
ms.date: 12/11/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b85f9ea5e9e570203d6d1f4148f714b0da1f861
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283435"
---
# <a name="quickstart-projects-and-solutions"></a>Szybki Start: Projekty i rozwiązania

W tym szybkiego startu 10 minut firma Microsoft będzie Poznaj, co to oznacza, że tworzenie rozwiązania i projektu w programie Visual Studio. Przyjrzymy właściwości projektu, a niektóre z plików, które może zawierać. Utworzymy również odwołanie do projektu drugiego.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

> [!TIP]
> Firma Microsoft będzie można konstruowania rozwiązania i projektu od podstaw w tego przewodnika Szybki Start, jako edukacyjnych wykonywania zrozumienie pojęcia projektu. W ogólne, używając programu Visual Studio najprawdopodobniej użyjesz wielu szablony projektu Visual Studio oferuje podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do opracowywania aplikacji w programie Visual Studio. Można także po prostu otwórz folder, który zawiera kod i uruchomić kodowanie, kompilowanie i debugowanie. Na przykład jeśli klonowanie repozytorium GitHub, go może nie zawierać projektów programu Visual Studio i rozwiązań. Aby uzyskać więcej informacji, zobacz [Opracuj kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Rozwiązania

Rozwiązanie to kontenery używane przez program Visual Studio do organizowania jedną lub więcej powiązanych projektów. Po otwarciu rozwiązania w programie Visual Studio automatycznie pobierze wszystkie projekty, które zawiera.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Zaczniemy naszych Eksploracja przez utworzenie puste rozwiązanie. Po uzyskaniu wiedzieć, Visual Studio, prawdopodobnie nie zaczniesz tworzyć puste rozwiązania zbyt często. Podczas tworzenia nowego projektu w programie Visual Studio, automatycznie tworzy rozwiązanie do przechowywania projektu, jeśli jeszcze nie istnieje rozwiązanie open.

1. Uruchom program Visual Studio.

   Zostanie otwarty program Visual Studio i prawdopodobnie zobaczysz **— strona początkowa** zajmują większość nieruchomości okna.

1. Na pasku menu wybierz **pliku** > **nowy** > **projektu**.

   **Nowy projekt** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **inne typy projektów**, a następnie wybierz **rozwiązań programu Visual Studio**. W środkowym okienku wybierz **puste rozwiązanie**. Nazwa rozwiązania "QuickSolution", a następnie wybierz pozycję **OK**.

   ![Pusty szablon rozwiązania](media/quickstart-projects-new-solution.png)

   **— Strona początkowa** zostanie zamknięty i rozwiązanie zostanie wyświetlony w **Eksploratora rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie użyjesz **Eksploratora rozwiązań** często, aby przeglądać zawartość projektów.

### <a name="add-a-project"></a>Dodaj projekt

Teraz możemy dodać nasze pierwszego projektu do rozwiązania. Firma Microsoft będzie rozpoczynać pusty projekt i Dodaj elementy, które należy do projektu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekstu **rozwiązania "QuickSolution"** w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy projekt**.

   **Dodawanie nowego projektu** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **Visual C#** i wybierz polecenie **Windows Desktop**. Następnie w środkowym okienku wybierz **pusty projekt (.NET Framework)**. Nazwa projektu "QuickDate", a następnie wybierz pozycję **OK** przycisku.

   Projekt o nazwie "QuickDate" pojawia się poniżej rozwiązania w **Eksploratora rozwiązań**. Obecnie zawiera jednego pliku o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz **Visual C#** w lewym okienku okna dialogowego, musisz zainstalować **tworzenia klasycznych aplikacji .NET** obciążenia. Prosty sposób, w tym celu jest wybranie **Otwórz Instalator programu Visual Studio** łącze w lewym dolnym rogu okna dialogowego. Po **Instalator programu Visual Studio** uruchomieniu wybierz **tworzenia klasycznych aplikacji .NET** obciążenia, a następnie **Modyfikuj** przycisku.

   ![Otwórz łącze Instalator programu Visual Studio](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Dodaj element do projektu

Mamy pusty projekt&mdash;Dodajmy pliku kodu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekstu **QuickDate** w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy element**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. Rozwiń węzeł **Visual C# elementów**, a następnie wybierz **kod**. W środkowym okienku wybierz **klasy**. Nazwa klasy "Kalendarz", a następnie wybierz **Dodaj** przycisku.

   Plik o nazwie *Calendar.cs* zostanie dodany do projektu. *.Cs* na końcu jest rozszerzenie pliku, które znajduje się do plików kodu C#. Plik pojawi się w hierarchii projektu visual w **Eksploratora rozwiązań**, a jego zawartość jest otwarty w edytorze.

1. Zastąp zawartość *Calendar.cs* pliku następującym kodem.

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Nie trzeba wiedzieć, jaki jest kod, ale jeśli chcesz, możesz uruchomić program i zobacz Wyświetla bieżącą datę w oknie konsoli.

## <a name="add-a-second-project"></a>Dodaj drugi projektu

Bardzo często rozwiązania wzajemnie się zawierały więcej niż jednego projektu i często odwołania te projekty. Niektóre projekty w rozwiązaniu może być biblioteki klas, niektóre aplikacje pliku wykonywalnego, i może być niektórych projektów testów jednostkowych lub witryny sieci web.

Dodajmy jednostkowy projekt testowy do naszego rozwiązania. Teraz Zaczniemy z szablonem projektu, więc nie trzeba było dodać dodatkowy kod plik do projektu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekstu **rozwiązania "QuickSolution"** w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy projekt**.

   **Dodawanie nowego projektu** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **Visual Basic** i wybierz polecenie **testu** kategorii. W środkowym okienku wybierz **jednostkowy projekt testowy (.NET Framework)**. Nazwa projektu "QuickTest", a następnie wybierz **OK** przycisku.

   Drugi projekt zostanie dodany do **Eksploratora rozwiązań**, a plik o nazwie *UnitTest1.vb* zostanie otwarty w edytorze. *.VB* jest rozszerzenie pliku, które znajduje się do plików kodu programu Visual Basic.

   ![Eksplorator rozwiązań z dwóch projektów](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

Chcemy używać nowego jednostkowy projekt testowy do testowania w naszym metody **QuickDate** projektu, więc musimy dodać odwołanie do tego projektu. Spowoduje to utworzenie zależności kompilacji między dwa projekty, co oznacza **QuickDate** zostanie skompilowany przed **QuickTest** po utworzeniu rozwiązania.

1. Wybierz **odwołania** w węźle **QuickTest** projektu, a z menu kliknij prawym przyciskiem myszy lub kontekstu, wybierz pozycję **Dodaj odwołanie**.

   ![Dodaj odwołanie do menu](media/quickstart-projects-add-reference.png)

   **Menedżera odwołań** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **projekty** i wybierz polecenie **rozwiązania**. W środkowym okienku, zaznacz pole wyboru **QuickDate**, a następnie wybierz pozycję **OK** przycisku.

   Odwołanie do **QuickDate** projekt zostanie dodany.

## <a name="add-test-code"></a>Dodaj kod testu

1. Teraz dodamy kod testu do pliku kodu języka Visual Basic. Zastąp zawartość *UnitTest1.vb* następującym kodem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Zostanie wyświetlony czerwony symbol "dowolnym kształcie" w części kodu. Firma Microsoft będzie naprawić ten błąd, tworząc projekt testowy [przyjaznego zestawu](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) do **QuickDate** projektu.

1. W **QuickDate** otwarciu projektu *Calendar.cs* plik, jeśli nie jest jeszcze otwarty i dodaj następującą instrukcję using i <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby rozwiązać problem w projekcie testowym.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Plik kod powinien wyglądać następująco.

   ![Kod języka CSharp](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku kodu C#, który zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> nazwę zestawu odwołuje się do atrybutu **QuickTest** projektu. Nazwa zestawu może nie być taka sama jak nazwa projektu. Aby znaleźć nazwy zestawu projektu, otwórz właściwości projektu.

1. W **Eksploratora rozwiązań**, wybierz pozycję **QuickTest** projektu. Wybierz z menu kliknij prawym przyciskiem myszy lub kontekstu **właściwości**, lub od razu naciśnij **Alt**+**Enter**.

   Otwieranie stron właściwości projektu na **aplikacji** kartę. Zwróć uwagę, że nazwa zestawu **QuickTest** projekt jest w rzeczywistości "QuickTest". Jeśli chcesz zmienić, jest to, gdzie należy ją zmienić. Następnie podczas kompilowania projektu testowego, wynikowy plik wykonywalny może zmienić nazwy z *QuickTest.exe* można wybrać.

   ![Właściwości projektu](media/quickstart-projects-properties.png)

1. Poznać inne karty strony właściwości projektu, takie jak **skompilować** i **ustawienia**. Te karty mogą być inne w zależności od typu projektu.

## <a name="next-steps"></a>Następne kroki

Jeśli chcesz sprawdzić, czy działa z testu jednostkowego, wybierz **Test** > **Uruchom** > **wszystkie testy** na pasku menu. Wywołuje okno **Eksploratora testów** zostanie otwarta, a powinna być wyświetlana **TestGetCurrentDate** przebiegi testów.

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Następnie należy poznać inne elementy szybkiego startu dla programu Visual Studio lub Dowiedz się więcej o sposobie [tworzenie projektów i rozwiązań](../ide/creating-solutions-and-projects.md).

## <a name="see-also"></a>Zobacz także

- [Szybki Start: Pierwsze spojrzenie na środowiska IDE programu Visual Studio](../ide/quickstart-ide-orientation.md)
- [Szybki Start: Personalizowanie środowiska IDE programu Visual Studio i edytora](../ide/quickstart-personalize-the-ide.md)
- [Szybki Start: Kodowania w edytorze](../ide/quickstart-editor.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE — omówienie](../ide/visual-studio-ide.md)