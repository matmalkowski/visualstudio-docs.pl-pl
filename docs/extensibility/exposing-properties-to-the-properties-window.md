---
title: "Udostępnianie właściwości do okna właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7aed43ac4248c9bfd1e43d5e6c732a4fef3af529
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-properties-to-the-properties-window"></a>Udostępnianie właściwości w oknie właściwości
Ten przewodnik opisuje publicznego właściwości obiektu do **właściwości** okna. Te właściwości są uwzględniane w **właściwości** okna.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Udostępnianie właściwości w oknie właściwości  
 W tej sekcji, utworzyć okna narzędzia niestandardowego i wyświetlić właściwości publiczne obiektu okienku okna skojarzony w **właściwości** okna.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Do udostępnienia właściwości w oknie właściwości  
  
1.  Każde rozszerzenie programu Visual Studio rozpoczyna się od VSIX Projekt wdrożenia, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projektu o nazwie `MyObjectPropertiesExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Dodaj okna narzędzia przez dodanie szablon elementu okna narzędzia niestandardowa o nazwie `MyToolWindow`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **okno dialogowe Dodaj nowy element**, przejdź do **elementów Visual C# / rozszerzalności** i wybierz **okna narzędzia niestandardowe**. W **nazwa** u dołu okna dialogowego, Zmień nazwę pliku, aby `MyToolWindow.cs`. Aby uzyskać więcej informacji o sposobie tworzenia okna narzędzi niestandardowych, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Otwórz MyToolWindow.cs i dodaj następującą instrukcję using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Teraz dodaj następujące pola do `MyToolWindow` klasy.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Dodaj następujący kod do klasy MyToolWindow.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` Używa właściwości `GetService` uzyskanie `STrackSelection` usługi, która zapewnia <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu. `OnToolWindowCreated` Obsługi zdarzeń i `SelectList` — metoda razem utworzyć listę wybranych obiektów, która zawiera tylko narzędzia okna okienko samego obiektu. `UpdateSelection` Informuje metody **właściwości** okno, aby wyświetlić właściwości publiczne okienka okna narzędzi.  
  
6.  Skompiluj projekt i Rozpocznij debugowanie. Powinna zostać wyświetlona eksperymentalne wystąpienie programu Visual Studio.  
  
7.  Jeśli **właściwości** okno nie jest wyświetlane, otwórz go, naciskając klawisz F4.  
  
8.  Otwórz **MyToolWindow** okna. Można znaleźć w **widoku / inne okna**.  
  
     Zostanie otwarte okno i właściwości publiczne okienka są wyświetlane w **właściwości** okna.  
  
9. Zmień **podpis** właściwości w **właściwości** okna **Moje właściwości obiektu**.  
  
     Tytuł okna MyToolWindow zmienia się odpowiednio.  
  
## <a name="exposing-tool-window-properties"></a>Udostępnianie właściwości okna narzędzi  
 W tej sekcji możesz dodać okna narzędzia i uzyskać jego właściwości. Zmiany właściwości są uwzględniane w **właściwości** okna.  
  
#### <a name="to-expose-tool-window-properties"></a>Aby udostępnić narzędzia Właściwości okna  
  
1.  Otwórz MyToolWindow.cs i Dodaj publiczny właściwość typu boolean IsChecked do klasy MyToolWindow.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Ta właściwość pobiera stanu z wyboru WPF, utworzone zostanie później.  
  
2.  Otwórz MyToolWindowControl.xaml.cs i Zamień Konstruktor MyToolWindowControl poniższy kod.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Dzięki temu `MyToolWindowControl` dostęp do `MyToolWindow` okienka.  
  
3.  W MyToolWindow.cs, zmień `MyToolWindow` konstruktora w następujący sposób:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Zmień na widok projektu MyToolWindowControl.  
  
5.  Przycisk Usuń, a następnie dodaj pola wyboru z **przybornika** na lewym górnym rogu.  
  
6.  Dodaj zaznaczone i niezaznaczone zdarzeń. Zaznacz pole wyboru w widoku Projekt. W **właściwości** okna, kliknij przycisk programów obsługi zdarzeń (u góry po prawej **właściwości** okno). Znajdź **zaznaczono** i typ **checkbox_Checked** w polu tekstowym, następnie znajdź **niezaznaczone** i typ **checkbox_Unchecked** w polu tekstowym.  
  
7.  Dodawanie obsługi zdarzeń pola wyboru:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Skompiluj projekt i Rozpocznij debugowanie.  
  
9. Otwórz w eksperymentalnym wystąpieniu **MyToolWindow** okna.  
  
     Wyszukaj w oknie właściwości w **właściwości** okna. **IsChecked** pojawi się w dolnej części okna, w obszarze **właściwości mojego** kategorii.  
  
10. Zaznacz pole wyboru **MyToolWindow** okna. **IsChecked** w **właściwości** okno zmienia się na **True**. Wyczyść pole wyboru w **MyToolWindow** okna. **IsChecked** w **właściwości** okno zmienia się na **False**. Zmień wartość **IsChecked** w **właściwości** okna. Pole wyboru w **MyToolWindow** okno zmiany, aby pasowała do nowej wartości.  
  
    > [!NOTE]
    >  Jeśli użytkownik musi dysponować obiektu, który jest wyświetlany w **właściwości** okna, wywołaj `OnSelectChange` z `null` kontener wyboru pierwszy. Po disposing właściwość lub obiekt, można zmienić kontener wyboru, które zostały zaktualizowane <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> i <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> listy.  
  
## <a name="changing-selection-lists"></a>Zmiana listy wyboru  
 W tej sekcji można dodać listy wyboru dla klasy podstawowej właściwości i wybierz z listy wyboru, które można wyświetlić za pomocą interfejsu okna narzędzia.  
  
#### <a name="to-change-selection-lists"></a>Aby zmienić wybór listy  
  
1.  Otwórz MyToolWindow.cs i Dodaj Klasa publiczna o nazwie `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Dodaj właściwość SimpleObject do klasy MyToolWindow, a także dwie metody, aby przełączyć **właściwości** okno wyboru między okienka i `Simple` obiektu.  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  W MyToolWindowControl.cs Zastąp programy obsługi pól wyboru tych wierszy kodu:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Skompiluj projekt i Rozpocznij debugowanie.  
  
5.  Otwórz w eksperymentalnym wystąpieniu **MyToolWindow** okna.  
  
6.  Zaznacz pole wyboru w **MyToolWindow** okna. **Właściwości** Wyświetla okna `Simple` właściwości, obiektu **SomeText** i **tylko do odczytu**. Usuń zaznaczenie pola wyboru. Właściwości publiczne okna są wyświetlane w **właściwości** okna.  
  
    > [!NOTE]
    >  Nazwa wyświetlana **SomeText** jest **Mój tekst**.  
  
## <a name="best-practice"></a>Najlepsze praktyki  
 W tym przewodniku <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest implementowany kolekcji wybieranych obiektów i kolekcji wybranego obiektu są tej samej kolekcji. Wybrany obiekt pojawia się na liście właściwości przeglądarki. Bardziej szczegółowy wykonania interfejs ISelectionContainer Zobacz Reference.ToolWindow próbek.  
  
 Visual Studio narzędzia windows zachowywane między sesjami programu Visual Studio. Aby uzyskać więcej informacji na przechowywanie stanu okna narzędzia, zobacz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)