---
title: Tworzenie okien formantu Przybornika formularzy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4229d9045dfe64fcb320eca7cf004de56e7f8f0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Tworzenie formantu Przybornika formularzy systemu Windows
Szablon elementu formantu Przybornika formularzy systemu Windows, który znajduje się w Visual Studio Tools rozszerzalności (VS SDK) umożliwia tworzenie formant, który jest automatycznie dodawany do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak użyć szablonu, aby utworzyć formant prostego licznika, którą można dystrybuować do innych użytkowników.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Tworzenie formantu Przybornika formularzy systemu Windows  
 Szablon formantu Przybornika formularzy systemu Windows tworzy kontrolkę użytkownika niezdefiniowane i udostępnia wszystkie funkcje, które jest wymagane do dodania formant **przybornika**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Tworzenie rozszerzenia z formantu Przybornika formularzy systemu Windows  
  
1.  Tworzenie projektu VSIX o nazwie `MyWinFormsControl`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Po otwarciu projektu dodać **formantu Przybornika formularzy systemu Windows** szablon elementu o nazwie `Counter`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **formantu Przybornika formularzy systemu Windows**  
  
3.  Spowoduje to dodanie kontrolkę użytkownika `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> aby umieścić kontrolkę w **przybornika**, a **Microsoft.VisualStudio.ToolboxControl** pozycji zasobu w manifeście VSIX dla wdrożenia.  
  
### <a name="building-a-user-interface-for-the-control"></a>Tworzenie formantu interfejsu użytkownika  
 `Counter` Formant wymaga dwóch formantów podrzędnych: <xref:System.Windows.Forms.Label> Aby wyświetlić bieżącą liczbę i <xref:System.Windows.Forms.Button> do resetowania licznika na 0. Inne formanty podrzędne są wymagane, ponieważ obiekty wywołujące powoduje zwiększenie licznika programowo.  
  
##### <a name="to-build-the-user-interface"></a>Tworzenie interfejsu użytkownika  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie Counter.cs, aby otworzyć go w projektancie.  
  
2.  Usuń "Kliknij tutaj!" **Przycisk** zawarty domyślnie po dodaniu szablon elementu formantu Przybornika formularzy systemu Windows.  
  
3.  Z **przybornika**, przeciągnij `Label` sterowania, a następnie `Button` kontroli poniżej na powierzchnię projektu.  
  
4.  Zmień rozmiar ogólną kontrolkę użytkownika do 150, do 50, kontrolować 50 pikseli, a następnie zmień rozmiar przycisku 20 pikseli.  
  
5.  W **właściwości** okna, ustaw następujące wartości kontrolek na powierzchnię projektu.  
  
    |Formant|Właściwość|Wartość|  
    |-------------|--------------|-----------|  
    |`Label1`|**Tekst**|""|  
    |`Button1`|**Nazwa**|btnReset|  
    |`Button1`|**Tekst**|Resetowanie|  
  
### <a name="coding-the-user-control"></a>Kodowanie kontrolki użytkownika  
 `Counter` Sterowania powoduje to udostępnienie metody, aby zwiększyć licznik zdarzenia wywoływane, gdy licznik jest zwiększany, `Reset` przycisk i trzech właściwości do przechowywania bieżąca liczba, tekst wyświetlany i wyświetlanie lub ukrywanie `Reset`przycisku. `ProvideToolboxControl` Atrybut określa, gdzie w **przybornika** `Counter` pojawi się formant.  
  
##### <a name="to-code-the-user-control"></a>Kod kontrolki użytkownika  
  
1.  Kliknij dwukrotnie formularza, aby otworzyć jego obciążenia obsługi zdarzeń w oknie kodu.  
  
2.  Powyżej metoda obsługi zdarzeń Utwórz całkowitą do przechowywania wartości licznika i ciągu do przechowywania tekstu, jak pokazano w poniższym przykładzie w klasy formantu.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Utwórz następujące deklaracje właściwości publicznej.  
  
    ```csharp  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     Elementy wywołujące mogą uzyskiwać dostęp do tych właściwości get i set wyświetlany tekst licznika, jak i do wyświetlenia lub ukrycia `Reset` przycisku. Obiekty wywołujące można uzyskać bieżącą wartość tylko do odczytu `Value` właściwości, ale nie można ustawić wartości bezpośrednio.  
  
4.  Umieść następujący kod `Load` zdarzeń dla formantu.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Ustawienie **etykiety** tekst w <xref:System.Windows.Forms.UserControl.Load> zdarzeń umożliwia właściwości obiektu docelowego załadować przed zastosowaniem ich wartości. Ustawienie **etykiety** tekstu w Konstruktorze spowodowałoby pustą **etykiety**.  
  
5.  Utwórz następującą metodę publiczny, aby zwiększyć licznik.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Dodaj deklarację dla `Incremented` zdarzenia do klasy formantu.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Obiekty wywołujące można dodać obsługi do tego zdarzenia do reagowania na zmiany w wartości licznika.  
  
7.  Powrót do widoku projektu, a następnie kliknij dwukrotnie ikonę `Reset` przycisk, aby wygenerować `btnReset_Click` obsługi zdarzeń i wypełnić ją w, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Bezpośrednio nad definicji klasy w `ProvideToolboxControl` atrybutu deklaracji, zmień wartość pierwszego parametru z `"MyWinFormsControl.Counter"` do `"General"`. To ustawia nazwę grupy elementów, który będzie obsługiwał formantu w **przybornika**.  
  
     W poniższym przykładzie przedstawiono `ProvideToolboxControl` atrybut i definicji klasy skorygowane.  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Testowanie formantu  
 Aby przetestować **przybornika** sterować, najpierw przetestować w środowisku programistycznym i przetestować go w skompilowanej aplikacji.  
  
##### <a name="to-test-the-control"></a>Aby sprawdzić formant  
  
1.  Naciśnij F5.  
  
     Tworzy projekt i otwiera drugie eksperymentalne wystąpienie programu Visual Studio, która ma zainstalowanego formantu.  
  
2.  Eksperymentalne wystąpienie programu Visual Studio, tworzenie **aplikacji Windows Forms** projektu.  
  
3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie ikonę pliku Form1.cs, aby otworzyć go w projektancie, jeśli nie jest już otwarty.  
  
4.  W **przybornika**, `Counter` formantu powinna być wyświetlana w **ogólne** sekcji.  
  
5.  Przeciągnij `Counter` sterowania do formularza, a następnie wybierz go. `Value`, `Message`, I `ShowReset` właściwości, które będą wyświetlane w **właściwości** okna, wraz z właściwościami, które są dziedziczone z <xref:System.Windows.Forms.UserControl>.  
  
6.  Ustaw `Message` właściwości `Count:`.  
  
7.  Przeciągnij <xref:System.Windows.Forms.Button> sterowania do formularza, a następnie ustaw właściwości nazwy i tekst przycisku `Test`.  
  
8.  Kliknij dwukrotnie przycisk, aby otworzyć pliku Form1.cs w widoku Kod i Utwórz obsługi kliknięcia.  
  
9. W obsłudze kliknij przycisk Wywołaj `counter1.Increment()`.  
  
10. W funkcji konstruktora, po wywołaniu `InitializeComponent`, typ `counter1``.``Incremented +=` i naciśnij dwa razy klawisz TAB.  
  
     Visual Studio generuje obsługi poziomie formularza `counter1.Incremented` zdarzeń.  
  
11. Wyróżnij `Throw` instrukcji do obsługi zdarzeń typu `mbox`, a następnie naciśnij klawisz TAB, dwa razy, aby wygenerować pola wiadomości z mbox fragment kodu.  
  
12. W następnym wierszu, Dodaj następujący `if` / `else` bloku, aby ustawić widoczność `Reset` przycisku.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Naciśnij F5.  
  
     Po otwarciu formularza. `Counter` Kontrola wyświetla następujący tekst.  
  
     **Liczba: 0**  
  
14. Kliknij przycisk **testu**.  
  
     Zwiększa licznik i Visual Studio Wyświetla okno komunikatu.  
  
15. Zamknij okno komunikatu.  
  
     **Zresetować** przycisk zniknie.  
  
16. Kliknij przycisk **testu** do momentu osiągnięcia licznik **5** komunikat zamknięcia pola zawsze.  
  
     **Zresetować** przycisk zostanie ponownie wyświetlony.  
  
17. Kliknij przycisk **zresetować**.  
  
     Resetuje licznik **0**.  
  
## <a name="next-steps"></a>Następne kroki  
 Podczas budowania **przybornika** kontroli, Visual Studio tworzy plik o nazwie *ProjectName*.vsix w folderze \bin\debug\ projektu. Przekazując plik .vsix z siecią lub do witryny sieci Web, można wdrożyć formantu. Po otwarciu pliku .vsix formantu jest zainstalowana i dodać do programu Visual Studio **przybornika** na komputerze użytkownika. Alternatywnie można przekazać plik .vsix [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryna sieci Web, tak aby użytkownicy mogli ją znaleźć przechodząc w **narzędzia / rozszerzenia i aktualizacje** okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Tworzenie formantu przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)