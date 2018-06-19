---
title: Tworzenie formantu przybornika WPF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b8bfbde2459998f13b8b19b17cfecba172538aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107806"
---
# <a name="creating-a-wpf-toolbox-control"></a>Tworzenie formantu przybornika WPF
Szablon formantu przybornika WPF (Windows Presentation Framework) umożliwia tworzenie formantów WPF, które są automatycznie dodawane do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak użyć szablonu, aby utworzyć **przybornika** kontroli, którą można dystrybuować do innych użytkowników.  
  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Tworzenie formantu przybornika WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Tworzenie rozszerzenia za pomocą formantu przybornika WPF  
  
1.  Tworzenie projektu VSIX o nazwie `MyToolboxControl`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Po otwarciu projektu dodać **kontroli przybornika WPF** szablon elementu o nazwie `MyToolboxControl`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **kontroli przybornika WPF**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby `MyToolboxControl.cs`.  
  
     Rozwiązanie zawiera teraz kontrolkę użytkownika `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> dodaje formant **przybornika**, a **Microsoft.VisualStudio.ToolboxControl** pozycji zasobu w manifeście VSIX  wdrożenia.  
  
#### <a name="to-create-the-control-ui"></a>Można utworzyć formantu interfejsu użytkownika  
  
1.  Otwórz MyToolboxControl.xaml w projektancie.  
  
     Pokazuje projektanta <xref:System.Windows.Controls.Grid> formant, który zawiera <xref:System.Windows.Controls.Button> formantu.  
  
2.  Rozmieść układ siatki. Po wybraniu <xref:System.Windows.Controls.Grid> kontrolować paski sterowania niebieski są wyświetlane na górnej i lewej krawędzi siatki. Poprzez kliknięcie można dodać do siatki wierszy i kolumn.  
  
3.  Dodaj formanty podrzędne do siatki. Formant podrzędny można umieścić, przeciągając je z **przybornika** do sekcji siatki, albo ustawiając jego `Grid.Row` i `Grid.Column` atrybutów w kodzie XAML. W poniższym przykładzie dodano dwie etykiety w górnym wierszu siatki i element button w drugim wierszu.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Zmiana nazwy formantu  
 Domyślnie formantu pojawią się w **przybornika** jako **MyToolboxControl** w grupę o nazwie **MyToolboxControl.MyToolboxControl**. Można zmienić ich nazwy w pliku MyToolboxControl.xaml.cs.  
  
1.  Otwórz MyToolboxControl.xaml.cs w widoku kodu.  
  
2.  Znajdź klasy MyToolboxControl i zmień jego nazwę na TestControl. (Jest to najszybszy sposób, w tym celu można zmienić nazwy klasy, następnie wybierz **zmienić** z menu kontekstowego i wykonaj kroki. (Aby uzyskać więcej informacji na temat **zmienić** polecenia, zobacz [zmienić Refaktoryzacja (C#)](../ide/reference/rename.md).)
  
3.  Przejdź do `ProvideToolboxControl` atrybutu i zmień wartość pierwszy parametr **testu**. Jest to nazwa grupy, która będzie zawierać formant w **przybornika**.  
  
     Wynikowy kod powinien wyglądać następująco:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Tworzenie, testowanie i wdrażanie  
 Podczas debugowania projektu, należy odnaleźć formantu zainstalowane w **przybornika** z eksperymentalne wystąpienie programu Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Tworzenie i testowanie formantu  
  
1.  Ponownie skompilować projekt i Rozpocznij debugowanie.  
  
2.  W tym nowym wystąpieniu programu Visual Studio Utwórz projekt aplikacji WPF. Upewnij się, że projektant XAML jest otwarty.  
  
3.  Znajdź formantu w **przybornika** i przeciągnij go na powierzchnię projektu.  
  
4.  Uruchom profilowanie aplikacji WPF.  
  
5.  Sprawdź, czy formant jest widoczny.  
  
#### <a name="to-deploy-the-control"></a>Aby wdrożyć formantu  
  
1.  Po utworzeniu projektu przetestowany plik .vsix można znaleźć w folderze \bin\debug\ projektu.  
  
2.  Można zainstalować go na komputerze lokalnym przez dwukrotne kliknięcie pliku .vsix i wykonując procedurę instalacji. Aby odinstalować formantu, przejdź do **narzędzia / rozszerzenia i aktualizacje** i wyszukaj rozszerzenie sterowania, a następnie kliknij przycisk **Odinstaluj**.  
  
3.  Przekaż plik .vsix z siecią lub do witryny sieci Web.  
  
     Jeśli można przekazać pliku do [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryny sieci Web, można użyć innych użytkowników **narzędzia / rozszerzenia i aktualizacje** w programie Visual Studio można znaleźć formantu w trybie online i zainstalować go.