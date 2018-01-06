---
title: "Wskazówki: Pisanie wizualizatora w C# | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6e161b3c914d0a87a720f1217b52a571b85f5ff9
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2018
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Wskazówki: Pisanie wizualizatora w C# #
W tym przewodniku pokazano, jak napisać prosty wizualizatora przy użyciu języka C#. Wizualizator, które będą tworzone w tym przewodniku Wyświetla zawartość ciągu przy użyciu okno komunikatu formularzy systemu Windows. Ten Wizualizator prosty ciąg nie jest szczególnie przydatna w sobie, ale zawiera podstawowe kroki, które należy wykonać, aby utworzyć wizualizatorów bardziej użyteczna w przypadku innych typów danych.  
  
> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, przejdź do **narzędzia** menu i wybierz polecenie **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Kod wizualizatora muszą znajdować się w bibliotece DLL, który będzie odczytywany przez debuger. W związku z tym pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.  

## <a name="create-a-visualizer-manually"></a>Ręczne tworzenie wizualizatora

Wykonaj zadania poniżej, aby utworzyć wizualizatora.
  
#### <a name="to-create-a-class-library-project"></a>Aby utworzyć projektu biblioteki klas  
  
1.  Na **pliku** menu, wybierz **nowy > Projekt**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **Visual C#**, wybierz pozycję **.NET Standard**.  
  
3.  W środkowym okienku wybierz **biblioteki klas**.  
  
4.  W **nazwa** wpisz odpowiednią nazwę biblioteki klas, takich jak MyFirstVisualizer.  
  
5.  Kliknij przycisk **OK**.  
  
 Po utworzeniu biblioteki klas, należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL tak, aby można było używać klas zdefiniowanych istnieje. Aby dodać odwołanie, jednak należy zmienić nazwę niektórych klas, aby miały łatwy do rozpoznania nazwy.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1.cs i dodać Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Class1.cs i wybierz **zmienić** menu skrótów.  
  
2.  Zmień nazwę z Class1.cs, wpisując tekst opisowy, takich jak DebuggerSide.cs.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automatycznie zmienia deklaracji klasy w DebuggerSide.cs odpowiadające nową nazwę pliku.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie** menu skrótów.  
  
4.  W **Dodaj odwołanie** na okna dialogowego **.NET** , wybierz pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Kliknij przycisk **OK**.  
  
6.  W DebuggerSide.cs, dodaj następującą instrukcję do `using` instrukcji:  
  
    ```csharp  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 Teraz można przystąpić do tworzenia kodu po stronie debugera. To jest kod, który jest uruchamiany w ramach debugera, aby wyświetlić informacje, które mają być wyświetlane. Najpierw trzeba zmienić deklaracja `DebuggerSide` obiekt, który dziedziczy z klasy podstawowej `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z DialogDebuggerVisualizer  
  
1.  W DebuggerSide.cs przejdź do następującego kodu:  
  
    ```csharp  
    public class DebuggerSide  
    ```  
  
2.  Zmień kod, aby:  
  
    ```csharp  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer`ma co metoda abstrakcyjna (`Show`), który należy zastąpić.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby przesłonić metodę DialogDebuggerVisualizer.Show  
  
-   W `public class DebuggerSide`, Dodaj następujący **metody:**  
  
    ```csharp  
    protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 `Show` Metoda zawiera kod, który faktycznie tworzy visualizer — okno dialogowe lub inny interfejs użytkownika i wyświetla informacje, który został przekazany do wizualizatora z debugera. Należy dodać kodu, który tworzy okno dialogowe i wyświetla informacje. W tym przewodniku zostaną w tym za pomocą okno komunikatu formularzy systemu Windows. Najpierw należy dodać odwołanie i `using` instrukcji dla elementu System.Windows.Forms.  
  
#### <a name="to-add-systemwindowsforms"></a>Aby dodać System.Windows.Forms  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie** menu skrótów.  
  
2.  W **Dodaj odwołanie** na okna dialogowego **.NET** , wybierz pozycję System.Windows.Forms.DLL.  
  
3.  Kliknij przycisk **OK**.  
  
4.  W DebuggerSide.cs, dodaj następującą instrukcję do `using` instrukcji:  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
 Teraz należy dodać kodu, tworzyć i wyświetlać interfejsu użytkownika dla użytkownika wizualizatora. Ponieważ jest to Twoje pierwsze wizualizatora, firma Microsoft będzie przechowywać prosty interfejs użytkownika i użyj okno komunikatu.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym  
  
1.  W `Show` metody, Dodaj następujący wiersz kodu:  
  
    ```csharp  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Ten przykład kodu nie ma obsługi błędów. Obsługa błędów w rzeczywistym wizualizatora lub dowolny inny rodzaj aplikacji, należy uwzględnić.  
  
2.  Na **kompilacji** menu, wybierz **kompilacji MyFirstVisualizer**. Projekt powinien pomyślnie kompilacji. Przed kontynuowaniem należy poprawić błędy kompilacji.  
  
 To już koniec kod po stronie debugera. Istnieje jeden krok, jednak; Ten atrybut informuje po stronie debugowanego obiektu, którego kolekcja klas obejmuje wizualizatora.  
  
#### <a name="to-add-the-debuggee-side-code"></a>Aby dodać kod po stronie debugowanego obiektu  
  
1.  Dodaj następujący kod atrybutu do DebuggerSide.cs, po `using` instrukcje ale przed wysłaniem `namespace MyFirstVisualizer`:  
  
    ```csharp  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target = typeof(System.String),  
    Description = "My First Visualizer")]  
    ```  
  
2.  Na **kompilacji** menu, wybierz **kompilacji MyFirstVisualizer**. Projekt powinien pomyślnie kompilacji. Przed kontynuowaniem należy poprawić błędy kompilacji.  
  
 W tym momencie Twojego pierwszego wizualizatora jest zakończony. Jeśli kroki zostały wykonane prawidłowo, można utworzyć wizualizatora i zainstalować go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Przed zainstalowaniem wizualizatora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], jednak należy przetestować go, aby upewnić się, że działa prawidłowo. Teraz utworzysz kontroler testu do uruchamiania wizualizatora bez instalowania go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metody testowej, można wyświetlić wizualizatora  
  
1.  Dodaj następującą metodę do klasy `public DebuggerSide`:  
  
    ```csharp  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Na **kompilacji** menu, wybierz **kompilacji MyFirstVisualizer**. Projekt powinien pomyślnie kompilacji. Przed kontynuowaniem należy poprawić błędy kompilacji.  
  
 Następnie należy utworzyć projekt wykonywalny do wywołania programu visualizer biblioteki DLL. Dla uproszczenia użyjemy projekt aplikacji konsoli.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać do rozwiązania projekt aplikacji konsoli  
  
1.  Na **pliku** menu, wybierz **Dodaj** , a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego, **szablony** wybierz **aplikacji konsoli**.  
  
3.  W **nazwa** wpisz nazwę opisową dla aplikacji konsoli, takich jak `MyTestConsole`.  
  
4.  Kliknij przycisk **OK**.  
  
 Teraz należy dodać niezbędne odwołuje się więc MyTestConsole można wywołać MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole** i wybierz polecenie **Dodaj odwołanie** menu skrótów.  
  
2.  W **Dodaj odwołanie** okno dialogowe **.NET** , wybierz pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3.  Kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **MyTestConsole** i wybierz polecenie **Dodaj odwołanie** ponownie.  
  
5.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **projekty** a następnie kliknij pozycję MyFirstVisualizer.  
  
6.  Kliknij przycisk **OK**.  
  
 Zostanie teraz Dodaj kod, aby zakończyć kontroler testu.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Program.cs i wybierz **zmienić** menu skrótów.  
  
2.  Umożliwia edytowanie nazwy z pliku Program.cs, wpisując tekst opisowy, na przykład TestConsole.cs.  
  
     **Uwaga** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmieni deklaracji klasy w TestConsole.cs odpowiadające nową nazwę pliku.  
  
3.  W TestConsole.cs, Dodaj następujący kod do `using` instrukcji:  
  
    ```csharp  
    using MyFirstVisualizer;  
    ```  
  
4.  W metodzie `Main`, Dodaj następujący kod:  
  
    ```csharp  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 Teraz można przystąpić do testowania Twojego pierwszego wizualizatora.  
  
#### <a name="to-test-the-visualizer"></a>Aby przetestować Wizualizator  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole** i wybierz polecenie **Ustaw jako projekt startowy** menu skrótów.  
  
2.  Na **debugowania** menu, wybierz **Start**.  
  
     Uruchamia aplikację konsoli i wizualizatora zostanie wyświetlony i ciąg "Hello, World".  
  
 Gratulacje. Właśnie utworzone i przetestowane Twojego pierwszego wizualizatora.  
  
 Aby korzystanie z wizualizatora w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zamiast tylko wywoływanie go z kontroler testu, należy go zainstalować. Aby uzyskać więcej informacji, zobacz [porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Tworzenie przy użyciu szablonu elementu wizualizatora wizualizatora  
 Do tej pory tego przewodnika wykazało należy jak ręcznie utworzyć wizualizatora. Zostało to wykonane jako wykonywania learning. Teraz, gdy wiesz, jak działa proste wizualizatora, jest łatwiejszy sposób, aby go utworzyć: przy użyciu szablonu elementu wizualizatora.  
  
 Najpierw należy utworzyć nowego projektu biblioteki klas.  
  
#### <a name="to-create-a-new-class-library"></a>Aby utworzyć nową bibliotekę klas  
  
1.  Na **pliku** menu, wybierz **nowy > Projekt**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **Visual C#**, wybierz pozycję **.NET Standard**.  
  
3.  W środkowym okienku wybierz **biblioteki klas**.   
  
4.  W **nazwa** wpisz odpowiednią nazwę biblioteki klas, takich jak MySecondVisualizer.  
  
5.  Kliknij przycisk **OK**.  
  
 Teraz można dodać elementu wizualizatora do niej:  
  
#### <a name="to-add-a-visualizer-item"></a>Aby dodać element wizualizatora  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy MySecondVisualizer.  
  
2.  W menu skrótów wybierz **Dodaj** , a następnie kliknij przycisk **nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego, w obszarze **Visual C# elementów**, wybierz pozycję **Wizualizator debugowania**.  
  
4.  W **nazwa** wpisz odpowiednią nazwę, takich jak SecondVisualizer.cs.  
  
5.  Kliknij przycisk **Dodaj**.  
  
 To wszystko jest do niego. Sprawdź plik SecondVisualizer.cs i wyświetlić kod, który szablon został dodany automatycznie. Przejdź dalej i Poeksperymentuj z kodem. Teraz, gdy znasz już podstawy jesteś na dobrej drodze do tworzenia bardziej złożone i przydatne wizualizatorów własny.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md)   
 [Utwórz niestandardowe Wizualizatory](../debugger/create-custom-visualizers-of-data.md)
