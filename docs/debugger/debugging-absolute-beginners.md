---
title: Debugowanie kodu dla początkujących bezwzględne
description: Jeśli debugujesz po raz pierwszy, Dowiedz się kilka zasady uruchomienie aplikacji w trybie debugowania w programie Visual Studio
ms.custom: ''
ms.date: 06/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2b9bcfecb8bae70852aebf7503641a8c2a3f6cf
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057356"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Debugowanie dla początkujących bezwzględne

Bez błędów możemy zapisać jako programistami kod zawsze nie co oczekiwaliśmy wykonania. Czasami robi całkowicie inny! W takim przypadku następne zadanie to aby dowiedzieć się, dlaczego i firma Microsoft może wydawać się tylko zachować uruchomieniem w naszego kodu na godziny, ale jest znacznie łatwiejsze i bardziej wydajne za pomocą narzędzia debugowania lub debugera.

Niestety, debugera nie coś, co magicznie może ujawnić wszystkie problemy lub "usterek" w naszym kodzie. *Debugowanie* oznacza, że aby uruchomić kod krok po kroku w narzędziu do debugowania, takich jak Visual Studio można znaleźć punktu, w którym wprowadzono błąd programowania. Następnie rozumiesz, jakie poprawki, które należy podjąć w kodzie, a narzędzia debugowania umożliwiają często tymczasowo zmienić tak, aby kontynuować program.

Efektywne za pomocą debugera jest również umiejętności, która jest czasochłonne i rozwiązań, aby dowiedzieć się, ale jest ostatecznie podstawowych zadań dla Każdy deweloper oprogramowania. W tym artykule następnie możemy wprowadzić podstawowe zasady debugowania i podaj porad ułatwiających rozpoczęcie pracy.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Wyjaśnienie problem pytając samodzielnie odpowiednie pytania

Ułatwia on wyjaśnienie uruchomionego na, przed podjęciem próby go rozwiązać problem. Oczekuje się, że możesz już wystąpił problem w kodzie, w przeciwnym razie nie można w tym miejscu chcesz dowiedzieć się, jak można debugować go! Tak przed rozpoczęciem debugowania, upewnij się, że wyłaniają przeznaczony do rozwiązania problemu:

* Oczekiwań swój kod, aby zrobić?

* Co się stało zamiast niego?

    Jeśli podczas uruchamiania aplikacji wystąpił błąd (wyjątku), które może być zdaje! Wyjątkiem jest nieoczekiwane zdarzenie napotkał podczas uruchamiania kodu, zazwyczaj błąd określonego rodzaju. Narzędzia debugowania może potrwać do dokładnego miejscu w kodzie, na którym wystąpił wyjątek i mogą pomóc w Zbadaj możliwe poprawki.

    Jeśli czegoś innego się stało, co to jest symptomem problem? Czy już podejrzewasz, którym wystąpił ten problem w kodzie? Na przykład jeśli kod wyświetla część tekstu, ale tekst jest niepoprawny, wiesz, że dane są uszkodzone albo określonego rodzaju błędów ma kod, który ustawić tekst wyświetlany. Przez krokowe wykonywanie kodu w debugerze, można sprawdzić wszystkie zmiany do odnajdywania dokładnie sposób i są przypisane nieprawidłowe wartości zmiennych.

## <a name="examine-your-assumptions"></a>Sprawdź założeń

Wziąć pod uwagę przed badania usterki lub wystąpił błąd, założeń, które można spodziewać się pewnych wynik wprowadzone. Ukryty lub nieznany założenia można uzyskać kategoriach identyfikowanie problemu, nawet wtedy, gdy chcesz dokładnie przyczyną problemu w debugerze. Masz długą listę możliwych założenia! Poniżej przedstawiono kilka pytań, aby zadać sobie zażąda założeń.

* Używasz prawo interfejsu API (oznacza to, prawego obiektu, funkcji, metody lub właściwości)? Interfejs API, którego używasz może nie działać wydaje się, że istnieje. (Po należy zbadać wywołania interfejsu API w debugerze, naprawienie go może wymagać podróży dokumentacji w celu identyfikowania poprawne interfejsu API.)

* Jest używany interfejs API poprawnie? Może być używane po prawej interfejsu API, ale nie został użyty w sposób prawo.

* Kod zawiera żadnych błędów? Niektórych błędów, takich jak prosty błąd pisowni nazwy zmiennej, może być trudne zobaczyć, szczególnie w przypadku pracy z językami, które nie wymagają zmienne, które mają być zadeklarowana przed ich używania.

* Czy wprowadzić zmiany w kodzie i przyjęto założenie, że jest związana z problem, który jest wyświetlane?

* Czy spodziewasz się obiektu lub zmienna zawiera określoną wartość (lub typ wartości) różni się od naturę naprawdę?

* Czy wiesz, celem kod? Jest często bardziej trudne do debugowania kogoś innego elementu kodu. Jeśli nie jest kod, jest to możliwe, należy poświęcić czas nauki dokładnie jakie kod jest przed debugowaniem jej efektywnie.

    > [!TIP]
    > Podczas pisania kodu, zacznij od czegoś małego i rozpoczynać się od kodu, który działa! (Dobrym przykładowy kod jest pomocne tutaj). Czasami jest łatwiej rozwiązać, zaczynając od małego fragmentu kodu, który demonstruje z podstawowym zadaniem, które próbujesz osiągnąć duży lub zbyt skomplikowany zestaw kodu. Następnie można zmodyfikować lub Dodaj kod przyrostowo, testowanie w każdym punkcie błędów.

Przez kwestionowaniu założeń, może skrócić czas potrzebny do znalezienia problem w kodzie. Może również skrócić czas potrzebny do rozwiązania konkretnego problemu.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Krokowo kodu w tryb można znaleźć, gdzie wystąpił problem podczas debugowania

Po uruchomieniu zwykle aplikacji, zostanie wyświetlony błędów i niepoprawne wyniki dopiero po uruchomieniu kodu. Program może również zakończyć nieoczekiwanie bez informujący, dlaczego.

Uruchamianie aplikacji w debugerze, nazywany również *tryb debugowania*, oznacza to, że debuger aktywnie monitoruje wszystko, co dzieje się jako program zostanie uruchomiony. Umożliwia on również wstrzymać aplikacja w dowolnym momencie, aby zbadać jego stan i następnie krokowo kodu wiersz po wierszu, aby obejrzeć co szczegółów jako zdarza się.

W programie Visual Studio, możesz wprowadzić tryb debugowania za pomocą **F5** (lub **debugowania** > **Rozpocznij debugowanie** polecenia menu lub **Rozpocznij debugowanie**  przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie")) na pasku narzędzi debugowania. Jeśli wystąpią wyjątki, pomocnika wyjątków programu Visual Studio umożliwia przejście do punktu gdzie wyjątek wystąpił i udostępnia inne przydatne informacje.

Jeśli nie otrzymasz wyjątek, to prawdopodobnie dobrze miejsce wyszukiwania problem w kodzie. To których są używane *punktów przerwania* z debugera w celu utworzenia możliwość bardziej dokładnie zbadać swój kod. Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio należy wstrzymać kodu uruchomionej Aby móc przeglądać wartości zmiennych, lub zachowanie pamięci lub sekwencji, w której jest uruchamiana kodu.

W programie Visual Studio można szybko ustawić punkt przerwania, klikając na lewym marginesie obok wiersza kodu. Lub umieść kursor na wiersza i naciśnij klawisz **F9**.

Aby funkcja tych pojęć, chcesz przejść przez niektóre przykładowy kod, który ma już kilka błędów. Używamy C#, ale funkcje debugowania dotyczą Visual Basic, C++, JavaScript, Python i innych języków.

### <a name="create-a-sample-app-with-some-bugs"></a>Tworzenie przykładowej aplikacji (z niektórych błędów)

Następnie utworzymy aplikację, która ma kilka błędów.

1. Musi mieć zainstalowanego programu Visual Studio i albo. **NET development pulpitu** obciążenia lub. **Podstawowe NET cross platform programowanie** obciążenia zainstalowane, w zależności od typu aplikacji, które chcesz utworzyć.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale jeszcze programu Visual Studio, kliknij przycisk **narzędzia** > **Pobierz narzędzia i funkcje**. Uruchamia Instalator programu Visual Studio. Wybierz. **NET development pulpitu** (lub. **Podstawowe NET cross platform programowanie**) obciążenia, a następnie wybierz **Modyfikuj**.

1. Otwórz program Visual Studio, a następnie wybierz pozycję **pliku** > **nowy** > **projektu**.

1. Wybierz szablon dla kodu aplikacji.

    Dla programu .NET Framework w **nowy projekt** okno dialogowe Wybierz **Visual C#**, **Windows Desktop** z sekcji zainstalowane szablony, a następnie w środkowym okienku wybierz  **Konsoli aplikacji (.NET Framework)**.

    Dla platformy .NET Core w **nowy projekt** oknie dialogowym wybierz **Visual C#**, **.NET Core** z sekcji zainstalowane szablony, a następnie w środkowym okienku wybierz  **Konsoli aplikacji (.NET Core)**.

    Jeśli nie widzisz tych szablonów, należy zainstalować odpowiednie obciążenie (zobacz powyżej).

1. W **nazwa** wpisz **ConsoleApp FirstApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt konsoli, która jest wyświetlana w Eksploratorze rozwiązań w okienku po prawej stronie.

1. W *Program.cs*, Zastąp domyślny kod następującym kodem:

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Naszym celem tego kodu jest wyświetlanie nazw galaxy, odległość galaxy i typ galaxy wszystkich na liście. Do debugowania, ważne jest zrozumienie celem kod. Oto format jeden wiersz z listy, która ma do pokazania w danych wyjściowych:

    *Nazwa Galaxy*, *odległość*, *typu galaxy*.

### <a name="run-the-app"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **F5** lub **Rozpocznij debugowanie** przycisk ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") narzędzi debugowania znajdujące się powyżej edytora kodu.

    Uruchamia aplikację i nie ma żadnych wyjątków pokazano nam przez debuger. Dane wyjściowe, które są widoczne w oknie konsoli jest jednak inna niż oczekiwana. Oto oczekiwane dane wyjściowe:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ale możemy zamiast tego zobacz:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Wyszukiwanie w danych wyjściowych i naszego kodu, wiemy, że `GType` jest nazwą klasy, która przechowuje typ galaxy. Próbujemy Pokaż typu rzeczywistego galaxy (na przykład "spirali"), nie nazwę klasy!

### <a name="debug-the-app"></a>Debugowanie aplikacji

1. Gdy aplikacja nadal działa, należy ustawić punkt przerwania, klikając pozycję na lewym marginesie `Console.WriteLine` wywołania metody w tym wierszu kodu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
        {
            Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Po ustawieniu punktu przerwania na lewym marginesie pojawi się czerwonej kropki.

    Ponieważ widzimy problem w danych wyjściowych, firma Microsoft rozpocznie się debugowanie analizując poprzedni kod, który ustawia dane wyjściowe w debugerze.

1. Kliknij przycisk **Uruchom ponownie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku w pasku narzędzi debugowania (**Ctrl** + **przesunięcia**   +  **F5**).

    Wstrzymuje aplikacji na punkt przerwania, które można ustawić. Żółty hightlighting wskazuje, gdzie jest wstrzymana debugera (żółty wiersz kodu nie wykonane).

1. Umieść kursor nad `GalaxyType` rozwinąć zmiennej po prawej stronie, a następnie w lewo ikona klucza `theGalaxy.GalaxyType`. Zostanie wyświetlony `GalaxyType` zawiera właściwość `MyGType`, i ma ustawioną wartość właściwości `Spiral`.

    ![Sprawdź zmienną](../debugger/media/beginners-inspect-variable.png)

    "Spirali" jest wartością poprawne, oczekiwany drukowanie do konsoli! Dlatego jest dobry początek, że masz dostęp tej wartości w tym kodu podczas uruchamiania aplikacji. W tym scenariuszu użyto niepoprawne interfejsu API. Jeśli firma Microsoft może rozwiązać ten problem podczas uruchamiania w debugerze kodu zostanie wyświetlone.

1. W tym samym kodzie, podczas debugowania nadal, umieść kursor na końcu `theGalaxy.GalaxyType` i zmień go na `theGalaxy.GalaxyType.MyGType`. Mimo że można to zrobić, edytora kodu pokazuje, o błędzie z informacją, że nie można skompilować tego kodu.

    ![Błąd składni](../debugger/media/beginners-edit.png)

1. Kliknij przycisk **Edytuj** w **Edytuj i Kontynuuj** okno komunikatu. Zostanie wyświetlony komunikat o błędzie teraz w **listy błędów** okna. Ten błąd oznacza, że `'object'` nie zawiera definicji dla `MyGType`.

    ![Błąd składni](../debugger/media/beginners-no-definition.png)

    Nawet wtedy, gdy firma Microsoft galaxy każdego obiektu typu `GType` (która zawiera `MGType` właściwości), debuger nie może rozpoznać `theGalaxy` obiektu jako obiektu typu `GType`. Co się dzieje? Chcesz znaleźć za pomocą kodu, który ustawia typ galaxy. Po wykonaniu tej czynności zobaczysz, że `GType` klasy ostatecznie ma właściwość `MyGType`, ale coś nie ma prawo. Komunikat o błędzie dotyczący `object` okaże się clue; interpreter języka typ wydaje się być obiektem typu `object` zamiast typu obiektu `GType`.

1. Wyszukiwanie za pomocą kodu powiązany z ustawianiem typu galaxy, możesz znaleźć `GalaxyType` właściwość `Galaxy` jest określona jako `object` zamiast `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Zmień poprzedni kod to:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Kliknij przycisk **Uruchom ponownie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku w pasku narzędzi debugowania (**Ctrl** + **przesunięcia**   +  **F5**) ponownie skompilować kod i uruchomić ponownie.

    Teraz, gdy debuger zatrzyma się w `Console.WriteLine`, można Aktywuj `theGalaxy.GalaxyType.MyGType`i zobaczyć poprawnie ustawionej wartości.

1. Usuń punkt przerwania, klikając okrągłego punktu przerwania na lewym marginesie (lub kliknij prawym przyciskiem myszy i wybierz polecenie **punktu przerwania** > **usunąć punkt przerwania**), a następnie naciśnij klawisz **F5** aby kontynuować.

    Aplikacja jest uruchamiana i wyświetla dane wyjściowe. Wygląda na to bardzo dobre teraz, ale można zauważyć rzecz; Oczekiwano galaxy małych chmury Magellanic wyświetlani jako nieregularne galaxy w danych wyjściowych konsoli, ale żaden typ galaxy będzie wyświetlana w ogóle.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Ustaw punkt przerwania w tym wierszu kodu.

    ```csharp
    public GType(char type)
    ```

    Ten kod jest, którego ustawiono typ galaxy, dlatego chcemy się zająć bliższe spojrzenie na go.

1. Kliknij przycisk **Uruchom ponownie** ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisku w pasku narzędzi debugowania (**Ctrl** + **przesunięcia**   +  **F5**) do ponownego uruchomienia.

    Wstrzymuje debuger w wierszu kodu, w którym można ustawić punktu przerwania.  

1. Umieść kursor nad `type` zmiennej. Zobacz wartość `S` (po kodzie znaków). Planuje się wartość `I`, ponieważ wiadomo, który jest typem galaxy nieregularne.

1. Naciśnij klawisz **F5** i umieść kursor nad `type` zmiennej ponownie. Powtórz ten krok, aż zostanie wyświetlony wartość `I` w `type` zmiennej.

    ![Sprawdź zmienną](../debugger/media/beginners-inspecting-data.png)

1. Teraz, naciśnij klawisz **F11** (**debugowania** > **Step Into** lub **Step Into** przycisku w pasku narzędzi Debug).

    **F11** przesuwa debugera (i wykonuje kod) jedną instrukcję naraz. **F10** (**Step Over**) jest podobne polecenie, a oba są bardzo przydatne podczas nauki korzystania debugera.

1. Naciśnij klawisz **F11** aż do zatrzymania na wierszu kodu w `switch` instrukcja dla wartości "I". W tym miejscu zobaczysz wyczyść wynikające z Literówka problem. Oczekiwano kodu, aby przejść do której ustawia `MyGType` jako nieregularne galaxy typu, lecz debuger całkowicie pomija ten kod i zatrzyma się w `default` sekcji `switch` instrukcji.

    ![Znajdź Literówka](../debugger/media/beginners-typo.png)

    Spojrzenie na kod, zobacz Literówka w `case 'l'` instrukcji. Powinien być `case 'I'`.

1. Kliknij w kodzie `case 'l'`i zastąpić go ciągiem "case"I".

1. Usuń punkt przerwania, a następnie kliknij przycisk **ponowne uruchomienie** przycisk, aby ponownie uruchomić aplikację.

    Teraz rozwiązane usterki, aby zobaczyć dane wyjściowe spodziewasz się!

    Naciśnij dowolny klawisz, aby zakończyć aplikację.

## <a name="summary"></a>Podsumowanie

Gdy pojawi się problem, należy użyć debugera i [krok polecenia](../debugger/navigating-through-code-with-the-debugger.md) takich jak **F10** i **F11** można znaleźć na region kodu z tym problemem.

> [!NOTE]
> Jeśli jest trudne do zidentyfikowania region kodu, gdzie występuje ten problem, ustaw punkt przerwania w kodzie, który jest uruchamiany przed wystąpieniem problemu, a następnie użyj polecenia krok, aż pojawi się problem manifestu. Można również użyć [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) logowania komunikaty **dane wyjściowe** okna. Dzięki patrzeć komunikaty zarejestrowane (i wiadomości, które nie zostały jeszcze zarejestrowane po raz pierwszy!), często można odizolować region kodu z tym problemem. Może być konieczne Powtórz ten proces kilka razy, aby zawęzić jej.

Po znalezieniu region kodu z tym problemem, należy użyć debugera do badania. Aby znaleźć przyczynę problemu, sprawdź kod problemu podczas uruchamiania aplikacji w debugerze:

* [Sprawdź zmienne](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) i sprawdź, czy zawierają one typ wartości, które powinny zawierać. Jeśli okaże się zła wartość dowiedzieć się, gdy została ustawiona nieprawidłowa wartość (Aby dowiedzieć się, gdy wartość została ustawiona, konieczne może być albo ponownie uruchom debuger, obejrzyj [stosu wywołań](../debugger/how-to-use-the-call-stack-window.md), lub obie).

* Sprawdź, czy aplikacja jest wykonywanie kodu, który będzie. (Na przykład w przykładowej aplikacji, Oczekiwano kodu dla instrukcji switch Ustaw typ galaxy nieregularne, ale aplikacja pominięte kodu z powodu Literówka.)

> [!TIP]
> Używasz debugera w celu znalezienia usterek. Narzędzia debugowania można znaleźć usterki *dla Ciebie* tylko wtedy, gdy wiadomo celem kodu. Jeśli express Tobie, deweloperze, że celem, narzędzie może tylko informacje celem kodu. Zapisywanie [testów jednostkowych](../test/improve-code-quality.md) się, jak to zrobić.

## <a name="next-steps"></a>Następne kroki

W tym artykule kiedy znasz już kilka ogólne koncepcje debugowania. Następnie możesz uruchomić poznanie debugowanie przy użyciu programu Visual Studio.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
