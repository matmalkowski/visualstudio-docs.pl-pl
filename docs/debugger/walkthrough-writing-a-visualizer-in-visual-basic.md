---
title: "Wskazówki: Pisanie wizualizatora w Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc15612fe7a59516483bb6b077e1b44b44f7fba8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Wskazówki: pisanie wizualizatora w Visual Basic
Ten przewodnik przedstawia sposób zapisania proste wizualizatora przy użyciu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Wizualizator, które będą tworzone w tym przewodniku Wyświetla zawartość ciągu przy użyciu okno komunikatu formularzy systemu Windows. Ten Wizualizator prostego ciągu jest prosty przykład pokazanie, sposób tworzenia wizualizatorów dla innych typów danych bardziej odpowiednie do projektów.  
  
> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, przejdź do **narzędzia** menu i wybierz polecenie **importowanie i eksportowanie** . Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Kod wizualizatora muszą znajdować się w bibliotece DLL, który będzie odczytywany przez debuger. Pierwszym krokiem jest do tworzenia projektu biblioteki klas dla biblioteki DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Tworzenie i przygotowanie projektu biblioteki klas  
  
#### <a name="to-create-a-class-library-project"></a>Aby utworzyć projektu biblioteki klas  
  
1.  Na **pliku** menu, wybierz **nowy** i kliknij przycisk **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **typu projektu**s, kliknij przycisk **Visual Basic**.  
  
3.  W **szablony** kliknij **biblioteki klas**.  
  
4.  W **nazwa** wpisz odpowiednią nazwę biblioteki klas, takich jak **MyFirstVisualizer**.  
  
5.  Kliknij przycisk **OK**.  
  
 Po utworzeniu biblioteki klas, należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL, tak, aby można było używać klas zdefiniowanych istnieje. Najpierw jednak nadać projektu zrozumiałą nazwę.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1.vb i dodać Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Class1.vb**i w menu skrótów kliknij **zmienić**.  
  
2.  Zmień nazwę z Class1.vb, wpisując tekst opisowy, takich jak DebuggerSide.vb.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automatycznie zmienia deklaracji klasy w DebuggerSide.vb odpowiadające nową nazwę pliku.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Moje wizualizatora pierwszy**i w menu skrótów kliknij **Dodaj odwołanie**.  
  
4.  W **Dodaj odwołanie** na okna dialogowego **.NET** , kliknij pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Kliknij przycisk **OK**.  
  
6.  W DebuggerSide.vb, dodaj następującą instrukcję do `Imports` instrukcji:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Dodaj kod po stronie debugera  
 Teraz można przystąpić do tworzenia kodu po stronie debugera. To jest kod, który jest uruchamiany w ramach debugera, aby wyświetlić informacje, które mają być wyświetlane. Najpierw trzeba zmienić deklaracja `DebuggerSide` obiekt, tak aby dziedziczy z klasy podstawowej `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z DialogDebuggerVisualizer  
  
1.  W DebuggerSide.vb przejdź do następującego kodu:  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  Edytuj kod, tak aby wygląda następująco:  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer`ma co metoda abstrakcyjna, `Show`, który należy zastąpić.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby przesłonić metodę DialogDebuggerVisualizer.Show  
  
-   W `public class DebuggerSide`, dodaj następującą metodę:  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 `Show` Metoda zawiera kod, który faktycznie tworzy visualizer — okno dialogowe, lub inny interfejs użytkownika i wyświetla informacje, który został przekazany do wizualizatora z debugera. Należy dodać kodu, który tworzy okno dialogowe i wyświetla informacje. W tym przewodniku zostaną w tym za pomocą okno komunikatu formularzy systemu Windows. Najpierw należy dodać odwołanie i `Imports` instrukcji dla <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Aby dodać System.Windows.Forms  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**i w menu skrótów kliknij **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** na okna dialogowego **.NET** , kliknij pozycję **System.Windows.Forms**.  
  
3.  Kliknij przycisk **OK**.  
  
4.  W DebuggerSide.cs, dodaj następującą instrukcję do `Imports` instrukcji:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Tworzenie sieci wizualizatora interfejsu użytkownika  
 Teraz należy dodać kodu, tworzyć i wyświetlać interfejsu użytkownika dla użytkownika wizualizatora. Ponieważ jest to Twoje pierwsze wizualizatora, będzie przechowywać prosty interfejs użytkownika i użyj pola wiadomości.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym  
  
1.  W `Show` metody, Dodaj następujący wiersz kodu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Ten przykład kodu nie ma obsługi błędów. Obsługa błędów w rzeczywistym wizualizatora lub dowolny inny rodzaj aplikacji, należy uwzględnić.  
  
2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien pomyślnie kompilacji. Przed kontynuowaniem należy poprawić błędy kompilacji.  
  
## <a name="add-the-necessary-attribute"></a>Dodaj atrybut niezbędne  
 To już koniec kod po stronie debugera. Istnieje jednak jeden krok,: atrybut, który informuje po stronie debugowanego obiektu, którego kolekcja klas obejmuje wizualizatora.  
  
#### <a name="to-add-the-debugee-side-code"></a>Aby dodać kod po stronie obiektu debugowanego  
  
1.  Dodaj następujący kod atrybutu do DebuggerSide.vb, po `Imports` instrukcje ale przed wysłaniem `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien pomyślnie kompilacji. Przed kontynuowaniem należy poprawić błędy kompilacji.  
  
## <a name="create-a-test-harness"></a>Utwórz kontroler testu  
 W tym momencie Twojego pierwszego wizualizatora jest zakończony. Jeśli kroki zostały wykonane prawidłowo, można utworzyć wizualizatora i zainstalować go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Przed zainstalowaniem wizualizatora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], jednak należy przetestować go, aby upewnić się, że działa prawidłowo. Teraz utworzysz kontroler testu do uruchamiania wizualizatora bez instalowania go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metody testowej, można wyświetlić wizualizatora  
  
1.  Dodaj następującą metodę do klasy `public DebuggerSide`:  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien pomyślnie kompilacji. Przed kontynuowaniem należy poprawić błędy kompilacji.  
  
 Następnie należy utworzyć projekt wykonywalny do wywołania programu visualizer biblioteki DLL. Dla uproszczenia należy użyć projekt aplikacji konsoli.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać do rozwiązania projekt aplikacji konsoli  
  
1.  Na **pliku** menu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego, **szablony** kliknij **aplikacji konsoli**.  
  
3.  W **nazwa** wpisz nazwę opisową dla aplikacji konsoli, takich jak **MyTestConsole**.  
  
4.  Kliknij przycisk **OK**.  
  
 Teraz należy dodać niezbędne odwołuje się więc MyTestConsole można wywołać MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole**i w menu skrótów kliknij **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** na okna dialogowego **.NET** , kliknij pozycję Microsoft.VisualStudio.DebuggerVisualizers.  
  
3.  Kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie kliknij przycisk **Dodaj odwołanie** ponownie.  
  
5.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **projektów** , a następnie wybierz MyFirstVisualizer.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Zakończ Twojego kontroler testu i testowania programu Visualizer  
 Zostanie teraz Dodaj kod, aby zakończyć kontroler testu.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.vb**i w menu skrótów kliknij **zmienić**.  
  
2.  Edytuj nazwę z Module1.vb na coś odpowiadającego, takich jak **TestConsole.vb**.  
  
     Zwróć uwagę, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmieni deklaracji klasy w TestConsole.vb odpowiadające nową nazwę pliku.  
  
3.  W TestConsole. VB, Dodaj następujący `Imports` instrukcji:  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  W metodzie `Main`, Dodaj następujący kod:  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 Teraz można przystąpić do testowania Twojego pierwszego wizualizatora.  
  
#### <a name="to-test-the-visualizer"></a>Aby przetestować Wizualizator  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole**i w menu skrótów kliknij **Ustaw jako projekt startowy**.  
  
2.  Na **debugowania** menu, kliknij przycisk **Start**.  
  
     Uruchamia aplikację konsoli. Wizualizator zostanie wyświetlony i ciąg "Hello, World."  
  
 Gratulacje. Właśnie utworzone i przetestowane Twojego pierwszego wizualizatora.  
  
 Aby korzystanie z wizualizatora w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zamiast tylko wywoływanie go z kontroler testu, należy go zainstalować. Aby uzyskać więcej informacji, zobacz [porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md)   
 [Utwórz niestandardowe Wizualizatory](../debugger/create-custom-visualizers-of-data.md)