---
title: 'Porady: Korzystanie z kreatora z szablonami projektu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8eef98d11f98e3db8216c69dcfacf478c676a837
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2018
---
# <a name="how-to-use-wizards-with-project-templates"></a>Porady: korzystanie z kreatora z szablonami projektu
Program Visual Studio udostępnia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu, implementując umożliwia uruchamianie kodu niestandardowego, gdy użytkownik tworzy projekt z szablonu.  
  
 Dostosowywanie szablonu projektu może służyć do wyświetlenia niestandardowego interfejsu użytkownika, która gromadzi dane wejściowe, aby dostosować szablon, należy dodać dodatkowe pliki do szablonu użytkownika lub innego działania dozwolone w projekcie.  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Metod interfejsu są nazywane w różnym czasie, gdy projekt jest tworzony, uruchamianie, gdy użytkownik kliknie **OK** na **nowy projekt** okno dialogowe. Do opisania punktu, w którym jest ona wywoływana nosi nazwę każdej metody interfejsu. Na przykład Visual Studio wymaga <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> natychmiast po uruchomieniu utworzyć projekt, dzięki czemu dobrym miejscem do pisanie kodu niestandardowego, aby zbierać dane wejściowe użytkownika.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Tworzenie projektu szablonu projektu z projektu VSIX  
 Możesz uruchomić utworzenie niestandardowego szablonu z projektu szablonu projektu., który wchodzi w skład programu Visual Studio SDK. W tej procedurze używamy projektu szablonu projektu C#, ale jest również projektu szablonu projektu Visual Basic. Następnie należy dodać projektu VSIX do rozwiązania, które zawiera projekt szablonu projektu.  
  
1.  Tworzenie projektu szablonu projektu C# (w programie Visual Studio **Plik > Nowy > Projekt > Visual C# > rozszerzalności > szablon projektu C#**). Nadaj mu nazwę **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Użytkownik może monit o zainstalowanie programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Dodawanie nowego projektu VSIX (**Plik > Nowy > Projekt > Visual C# > rozszerzalności > projektu VSIX**) w tego samego rozwiązania co projekt szablonu (w **Eksploratora rozwiązań**, wybierz pozycję rozwiązanie, kliknij prawym przyciskiem myszy, a następnie wybierz węzeł **Dodaj > Nowy projekt**). Nadaj mu nazwę **MyProjectWizard.**  
  
3.  Ustaw projekt VSIX jako projekt startowy. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.  
  
4.  Dodaj szablon projektu jako zasób projektu VSIX. W **Eksploratora rozwiązań**, w obszarze węzła projektu VSIX, Znajdź **source.extension.vsixmanifest** pliku. Kliknij go dwukrotnie, aby otworzyć go w edytorze manifestu.  
  
5.  W edytorze manifestu wybierz **zasoby** karcie po lewej stronie okna.  
  
6.  W **zasoby** wybierz opcję **nowy**. W **Dodaj nowy element zawartości** okna w polu Typ wybierz **Microsoft.VisualStudio.ProjectTemplate**. W **źródła** pól, zaznacz **projekt w bieżącym rozwiązaniu**. W **projektu** pól, zaznacz **MyProjectTemplate**. Następnie kliknij przycisk **OK**.  
  
7.  Skompiluj rozwiązanie i Rozpocznij debugowanie. Zostanie wyświetlone drugie wystąpienie programu Visual Studio. (Może to potrwać kilka minut).  
  
8.  W drugim wystąpienie programu Visual Studio spróbuj utworzyć nowy projekt z nowego szablonu. (**Plik > Nowy > Projekt > Visual C# > szablonu MyProject**). Nowy projekt powinien zostać wyświetlony z klasy o nazwie **Class1**. Został utworzony szablon niestandardowy projektu! Zatrzymać debugowanie.  
  
## <a name="creating-a-custom-template-wizard"></a>Tworzenie kreatora szablonu niestandardowego  
 W tym temacie przedstawiono sposób tworzenia niestandardowego kreatora otwartym formularzu systemu Windows, przed utworzeniem projektu. Formularz umożliwia użytkownikom dodanie wartość parametru niestandardowych, który jest dodawany do kodu źródłowego podczas tworzenia projektu.  
  
1.  Konfigurowanie projektu VSIX, aby umożliwić go w celu utworzenia zestawu.  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX. Poniżej Eksploratora rozwiązań powinien zostać wyświetlony **właściwości** okna. W przeciwnym razie wybierz **Widok > okno właściwości**, lub naciśnij klawisz **F4**. W oknie właściwości wybierz następujące pola do `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Dodaj zestaw jako zasób do projektu VSIX. Otwórz plik Source.Extension.vsixmanifest,a i wybierz **zasoby** kartę. W **Dodaj nowy element zawartości** oknie dla **typu** wybierz **Microsoft.VisualStudio.Assembly**, dla **źródła** wybierz **A Projekt w bieżącym rozwiązaniu**oraz **projektu** wybierz **MyProjectWizard**.  
  
4.  Dodaj następujące odwołania do projektu VSIX. (W **Eksploratora rozwiązań**, w pliku VSIX projektu wybierz węzeł **odwołania**, kliknij prawym przyciskiem myszy, a następnie wybierz **Dodaj odwołanie**.) W **Dodaj odwołanie** okna dialogowego, w **Framework** karcie, Znajdź **formularze System.Windows** zestawu i zaznacz je. Teraz wybierz **rozszerzenia** Znajdź kartę **EnvDTE** zestawu i zaznacz je. Jest także **Microsoft.VisualStudio.TemplateWizardInterface** zestawu i zaznacz je. Kliknij przycisk **OK**.  
  
5.  Dodaje klasę do wykonania Kreatora do projektu VSIX. (W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu VSIX, a następnie wybierz **Dodaj**, następnie **nowy element**, następnie **klasy**.) Nazwa klasy **WizardImplementation**.  
  
6.  Zastąp kod w **WizardImplementationClass.cs** pliku następującym kodem:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
        {  
            private UserInputForm inputForm;  
            private string customMessage;  
  
            // This method is called before opening any item that   
            // has the OpenInEditor attribute.  
            public void BeforeOpeningFile(ProjectItem projectItem)  
            {  
            }  
  
            public void ProjectFinishedGenerating(Project project)  
            {  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public void ProjectItemFinishedGenerating(ProjectItem   
                projectItem)  
            {  
            }  
  
            // This method is called after the project is created.  
            public void RunFinished()  
            {  
            }  
  
            public void RunStarted(object automationObject,  
                Dictionary<string, string> replacementsDictionary,  
                WizardRunKind runKind, object[] customParams)  
            {  
                try  
                {  
                    // Display a form to the user. The form collects   
                    // input for the custom message.  
                    inputForm = new UserInputForm();  
                    inputForm.ShowDialog();  
  
                    customMessage = UserInputForm.CustomMessage;  
  
                    // Add custom parameters.  
                    replacementsDictionary.Add("$custommessage$",   
                        customMessage);  
                }  
                catch (Exception ex)  
                {  
                    MessageBox.Show(ex.ToString());  
                }  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public bool ShouldAddProjectItem(string filePath)  
            {  
                return true;  
            }          
        }  
    }  
    ```  
  
     **UserInputForm** do którego odwołuje się ten kod będzie później zaimplementowana.  
  
     `WizardImplementation` Klasa zawiera implementacje metod dla każdego członka <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. W tym przykładzie, tylko <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metoda wykonuje zadanie. Wszystkie inne metody, nic nie rób albo zwracać `true`.  
  
     <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda przyjmuje cztery parametry:  
  
    -   <xref:System.Object> Parametru, które mogą być rzutowane na katalog główny <xref:EnvDTE._DTE> obiekt umożliwiają dostosowanie projektu.  
  
    -   A <xref:System.Collections.Generic.Dictionary%602> parametr, który zawiera kolekcję wszystkich wstępnie zdefiniowanych parametrów w szablonie. Aby uzyskać więcej informacji dotyczących parametrów szablonu, zobacz [parametrów szablonu](../ide/template-parameters.md).  
  
    -   A <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parametr, który zawiera informacje o rodzaju szablon jest używany.  
  
    -   <xref:System.Object> Tablicy, która zawiera zestaw parametrów przekazane do kreatora przez program Visual Studio.  
  
     W tym przykładzie dodaje wartości parametru z formularza danych wejściowych użytkownika do <xref:System.Collections.Generic.Dictionary%602> parametru. Każde wystąpienie `$custommessage$` parametru w projekcie zostaną zastąpione tekst wprowadzony przez użytkownika. Następujące zestawy należy dodać do projektu: **systemu** i **System.Drawing**.
  
7.  Teraz utworzyć **UserInputForm**. W **WizardImplementation.cs** pliku, Dodaj następujący kod na końcu **WizardImplementation** klasy.  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
                this.Close();
            }  
        }  
    ```  
  
     Formularza danych wejściowych użytkownika zapewnia prosty formularz wprowadzania parametru niestandardowego. Formularz zawiera pole tekstowe o nazwie `textBox1` i przycisk o nazwie `button1`. Po kliknięciu przycisku tekst w polu tekstowym jest przechowywany w `customMessage` parametru.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>Nawiązać Kreatora szablonu niestandardowego  
 Kreator niestandardowy szablon niestandardowy projekt, musisz podpisać zestawu kreatora i dodaj kilka wierszy do szablonu projektu niestandardowy o tym, gdzie można znaleźć implementacji kreatora podczas tworzenia nowego projektu.  
  
1.  Podpisz zestaw. W **Eksploratora rozwiązań**, wybierz projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **właściwości projektu**.  
  
2.  W **właściwości projektu** wybierz **podpisywanie** kartę w **podpisywanie** karcie wyboru **Podpisz zestaw**. W **wybierz plik klucza o silnej nazwie** pól, zaznacz  **\<nowy >**. W **tworzenie silnej nazwy klucza** okna w **nazwę pliku klucza** wpisz **key.snk**. Usuń zaznaczenie pola wyboru **ochrony pliku klucza przy użyciu hasła** pola.  
  
3.  W **Eksploratora rozwiązań**, wybierz projekt VSIX i Znajdź **właściwości** okna.  
  
4.  Ustaw **katalog wyjściowy danych wyjściowych kompilacji kopiowania** do **true**. Dzięki temu zestawu, który ma zostać skopiowany do katalogu wyjściowego podczas rozwiązania. Nadal znajduje się w pliku .vsix. Należy sprawdzić zestaw się jego klucza podpisywania.  
  
5.  Ponownie skompiluj rozwiązanie.  
  
6.  Teraz można znaleźć pliku key.snk w katalogu projektu MyProjectWizard (**\<lokalizacji na dysku > \MyProjectTemplate\MyProjectWizard\key.snk**). Skopiuj plik key.snk.  
  
7.  Przejdź do katalogu wyjściowego i Znajdź zestawu (**\<lokalizacji na dysku > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Wklej plik key.snk tutaj. (Nie jest to bezwzględnie konieczne, ale spowoduje to, że następujące kroki łatwiejsze).  
  
8.  Otwórz okno polecenia i przejdź do katalogu, w którym został utworzony zestaw.  
  
9. Znajdź **sn.exe** narzędzia podpisywania. Na przykład na 64-bitowym systemie Windows 10, typowe ścieżka byłaby następujące czynności:  
  
     **C:\Program plików (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 narzędzia**  
  
     Jeśli nie można odnaleźć narzędzia, spróbuj uruchomić **gdzie /R.  SN.exe** w oknie wiersza polecenia. Zanotuj ścieżkę.  
  
10. Wyodrębnić klucza publicznego z pliku key.snk. W oknie polecenia wpisz  
  
     **\<Lokalizacja sn.exe > \sn.exe -p key.snk outfile.key.**  
  
     Nie zapomnij przestrzenny ścieżka sn.exe w cudzysłowie, jeśli istnieją spacje w nazwach katalogów!  
  
11. Pobierz token klucza publicznego z PlikWyjściowy:  
  
     **\<Lokalizacja sn.exe > \sn.exe outfile.key -t.**  
  
     Ponownie nie zapomnij cudzysłowów. Wiersz w danych wyjściowych, jak powinny być widoczne  
  
     **Token klucza publicznego jest<token>**  
  
     Zanotuj tę wartość.  
  
12. Dodaj odwołanie do kreatora niestandardowego do pliku .vstemplate szablonu projektu. W Eksploratorze rozwiązań Znajdź plik o nazwie MyProjectTemplate.vstemplate i otwórz go. Po zakończeniu \<TemplateContent > Dodaj sekcję poniżej:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Gdzie **MyProjectWizard** jest nazwą zestawu, a **tokenu** jest tokenem skopiowany w poprzednim kroku.  
  
13. Zapisz wszystkie pliki w projekcie i skompiluj ponownie.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Dodawanie do szablonu niestandardowego parametru  
 W tym przykładzie używany jako szablon projektu wyświetli komunikat określone w formie wejściowych użytkownika Kreatora niestandardowego.  
  
1.  W Eksploratorze rozwiązań, przejdź do **MyProjectTemplate** projektu i Otwórz **Class1.cs**.  
  
2.  W `Main` metoda aplikacji, Dodaj następujący wiersz kodu.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Parametr `$custommessage$` jest zastępowany tekst wprowadzony w formularza danych wejściowych użytkownika, gdy projekt jest tworzony na podstawie szablonu.  
  
 Oto plik pełny kod, zanim została wyeksportowana do szablonu.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>Za pomocą Kreatora niestandardowego  
 Teraz możesz utworzyć projekt z szablonu i za pomocą Kreatora niestandardowego.  
  
1.  Ponownie skompiluj rozwiązanie i Rozpocznij debugowanie. Powinna pojawić się drugie wystąpienie programu Visual Studio.  
  
2.  Utwórz nowy projekt MyProjectTemplate. (**Plik > Nowy > Projekt > Visual C# > MyProjectTemplate**)  
  
3.  W **nowy projekt** okno dialogowe Znajdź szablon, wpisz nazwę i kliknij przycisk **OK**.  
  
     Zostanie otwarty Kreator formularza danych wejściowych użytkownika.  
  
4.  Wpisz wartość dla parametru niestandardowego, a następnie kliknij przycisk.  
  
     Zamyka formularza danych wejściowych użytkownika kreatora i projektu jest tworzona na podstawie szablonu.  
  
5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik kodu źródłowego i kliknij przycisk **kod widoku**.  
  
     Zwróć uwagę, że `$custommessage$` zostało zastąpione tekst wprowadzony w formularza danych wejściowych użytkownika kreatora.  
  
## <a name="see-also"></a>Zobacz też  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[WizardExtension, element (szablony Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[Pakiety NuGet w szablony programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
