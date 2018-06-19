---
title: 'Wskazówki: Zapisywanie ustawień użytkownika na stronie Start | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ea4d4a07ed9f61f20ca2b3f79b99d3a2ebfa0b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146094"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Wskazówki: Zapisywanie ustawień użytkownika na stronę początkową
Można ją utrwalić ustawienia użytkownika dla strony początkowej sieci. Wykonując tego przewodnika, można utworzyć formantu, który zapisuje ustawienie rejestru, gdy użytkownik kliknie przycisk, a następnie pobiera ustawienie zawsze ładuje strony początkowej. Ponieważ strona początkowa szablon projektu zawiera kontrolki użytkownika można dostosować, a domyślne strony początkowej XAML wymaga tego formantu, nie trzeba się zmodyfikować strony początkowej.  
  
 Magazyn ustawień, który zostanie uruchomiony w ramach tego przewodnika jest wystąpieniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfejsu, która odczytuje i zapisuje w następującej lokalizacji rejestru, gdy jest wywoływana: HKCU\Software\Microsoft\VisualStudio\14.0\\  *CollectionName*  
  
 Gdy jest on uruchamiany w eksperymentalne wystąpienie programu Visual Studio, Magazyn ustawień odczytuje i zapisuje HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName.*  
  
 Aby uzyskać więcej informacji na temat w celu utrzymania ustawień, zobacz [opcje i ustawienia użytkownika rozszerzanie](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
> [!NOTE]
>  Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  Szablon projektu strony początkowej można pobrać za pomocą **Menedżera rozszerzenia**.  
  
## <a name="setting-up-the-project"></a>Konfigurowanie projektu  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Aby skonfigurować projekt dla tego przewodnika  
  
1.  Utwórz projekt strony początkowej, zgodnie z opisem w [Tworzenie niestandardowej strony początkowej](creating-a-custom-start-page.md). Nazwij projekt **SaveMySettings**.  
  
2.  W **Eksploratora rozwiązań**, Dodaj następujące odwołania do zestawu do projektu StartPageControl:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Otwórz MyControl.xaml.  
  
4.  W okienku XAML w najwyższego poziomu <xref:System.Windows.Controls.UserControl> definicji elementu, Dodaj następujące deklaracja zdarzenia po deklaracjach przestrzeni nazw.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  W okienku projektowania kliknij obszaru głównego formantu, a następnie naciśnij klawisz DELETE.  
  
     Spowoduje to usunięcie <xref:System.Windows.Controls.Border> element i wszystkie elementy, a tylko najwyższego poziomu pozostawia <xref:System.Windows.Controls.Grid> elementu.  
  
6.  Z **przybornika**, przeciągnij <xref:System.Windows.Controls.StackPanel> formant do siatki.  
  
7.  Teraz przeciągnij <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>oraz przycisk służący do <xref:System.Windows.Controls.StackPanel>.  
  
8.  Dodaj **x: Name** atrybutu dla <xref:System.Windows.Controls.TextBox>, a `Click` zdarzenia dla <xref:System.Windows.Controls.Button>, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementowanie kontrolki użytkownika  
  
#### <a name="to-implement-the-user-control"></a>Aby wdrażanie kontroli użytkownika  
  
1.  W okienku XAML, kliknij prawym przyciskiem myszy `Click` atrybutu <xref:System.Windows.Controls.Button> elementu, a następnie kliknij przycisk **przechodzą do obsługi zdarzeń**.  
  
     To otwiera MyControl.xaml.cs i tworzy obsługi stub `Button_Click` zdarzeń.  
  
2.  Dodaj następujące `using` instrukcje na początku pliku.  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Dodaj prywatnej `SettingsStore` właściwości, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     Ta właściwość najpierw pobiera odwołanie do <xref:EnvDTE80.DTE2> interfejsu, zawierającą modelu obiektu automatyzacji z <xref:System.Windows.FrameworkElement.DataContext%2A> kontrolki użytkownika, a następnie używa DTE można pobrać wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfejsu. Następnie używa tego wystąpienia, aby przywrócić bieżące ustawienia użytkownika.  
  
4.  Wypełnij `Button_Click` zdarzeń w następujący sposób.  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     To zapisuje zawartość pola tekstowego do pola "MySetting" w kolekcji "MySettings" w rejestrze. Jeśli kolekcja nie istnieje, jest tworzony.  
  
5.  Dodaj następujące obsługę `OnLoaded` zdarzeń kontrolki użytkownika.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Bieżąca wartość "MySetting" to ustawia tekst pola tekstowego.  
  
6.  Tworzenie formantu użytkownika.  
  
7.  W **Eksploratora rozwiązań**, otwórz source.extension.vsixmanifest.  
  
8.  W edytorze manifestu zestawu **nazwa produktu** do **Zapisz moje ustawienia strony początkowej**.  
  
     Ustawia nazwę strony początkowej, ponieważ ma ono wyświetlane w **dostosowanie strony początkowej** na liście **opcje** okno dialogowe.  
  
9. Tworzenie StartPage.xaml.  
  
## <a name="testing-the-control"></a>Testowanie formantu  
  
#### <a name="to-test-the-user-control"></a>Aby przetestować kontrolki użytkownika  
  
1.  Naciśnij F5.  
  
     Otwiera eksperymentalne wystąpienie programu Visual Studio.  
  
2.  W eksperymentalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **opcje**.  
  
3.  W **środowiska** węzła, kliknij przycisk **uruchamiania**, a następnie w **dostosowanie strony początkowej** listy, wybierz **[zainstalowane rozszerzenia] Zapisz moje ustawienia strony początkowej** .  
  
     Kliknij przycisk **OK**.  
  
4.  Zamknij stronę początkową, jeśli jest on otwarty, a następnie na **widoku** menu, kliknij przycisk **— strona początkowa**.  
  
5.  Na stronie początkowej kliknij **MójFormant** kartę.  
  
6.  W polu tekstowym wpisz **Cat**, a następnie kliknij przycisk **Zapisz moje ustawienia**.  
  
7.  Zamknij stronę początkową, a następnie otwórz go ponownie.  
  
     Wyraz "Kot" powinna być wyświetlana w polu tekstowym.  
  
8.  Zamień wyraz "Kot" wyraz "Dog". Nie należy klikać przycisku.  
  
9. Zamknij stronę początkową, a następnie otwórz go ponownie.  
  
     Wyraz "Kot" powinna być wyświetlana w polu tekstowym, mimo, że ustawienie nie został zapisany. Zdarza się to Visual Studio zachowuje okna narzędzi w pamięci, nawet jeśli ich są zamknięte, do czasu zamknięcia programu Visual Studio, sama.  
  
10. Zamknij eksperymentalne wystąpienie programu Visual Studio.  
  
11. Naciśnij klawisz F5, aby ponownie otworzyć eksperymentalne wystąpienie.  
  
12. Wyraz "Kot" powinna być wyświetlana w polu tekstowym.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz zmodyfikować ten formant użytkownika, aby zapisać i pobierać dowolną liczbę niestandardowych ustawień przy użyciu różnych wartości z obsługi zdarzeń do pobierania i ustawiania `SettingsStore` właściwości. Tak długo, jak można użyć innego `propertyName` parametr dla każdego wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, wartości nie zastąpi siebie w rejestrze.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)