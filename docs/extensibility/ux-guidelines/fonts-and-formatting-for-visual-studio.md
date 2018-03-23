---
title: Czcionki i formatowania dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/26/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 83c1d4e20dd372d3b76362b9f06ee894b045333c
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Czcionki i formatowania dla programu Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a> Czcionka środowiska
 Wszystkie czcionki w programie Visual Studio muszą być widoczne dla użytkowników do dostosowania. Przede wszystkim odbywa się za pośrednictwem **czcionki i kolory** strony **Narzędzia > Opcje** okna dialogowego. Są trzy główne kategorie ustawienia czcionki:  
  
-   **Czcionka środowiska** — podstawowy czcionkę dla IDE (zintegrowane środowisko programistyczne), wszystkich elementów interfejsu, w tym okien dialogowych, menu Narzędzia windows i windows dokumentu. Domyślnie czcionki środowiska jest powiązany czcionki systemowej, który jest wyświetlany jako 9 pt Segoe UI w bieżących wersjach systemu Windows. Przy użyciu jednego czcionki dla wszystkich elementów interfejsu zapewnia czcionki spójny wygląd IDE.  
  
-   **Edytor tekstu** — w obszarze elementów, że w kodzie i innych powierzchni edytory oparte na tekst można dostosować w edytorze tekstu **Narzędzia > Opcje**.  
  
-   **Określonych kolekcji** -powierzchni projektanta systemu windows, które oferują dostosowywanie ich elementy interfejsu użytkownika może narazić czcionki specyficzne dla ich projektu w ich własnych strony ustawień w **Narzędzia > Opcje**.  
  
### <a name="editor-font-customization-and-resizing"></a>Dostosowywanie edytora czcionki i zmiana rozmiaru  
 Użytkownicy często będą powiększyć lub powiększenie rozmiaru i/lub kolor tekstu w edytorze zgodnie z ich preferencji, niezależnie od interfejsu użytkownika ogólne. Ponieważ czcionki środowisko jest używane dla elementów, które mogą być wyświetlane w ramach lub jako część Projektant/edytora, jest pamiętać oczekiwane zachowanie, gdy jeden z tych klasyfikacjach czcionki zostanie zmieniona.  
  
 Podczas tworzenia elementów interfejsu użytkownika, które są wyświetlane w edytorze, ale są nie jest częścią *zawartości*, ważne jest, aby używać czcionkę środowiska i nie czcionki tekstu, tak aby elementy zmiany rozmiaru w sposób przewidywalne.  
  
1.  Kod tekstu w edytorze Zmień rozmiar ustawienia czcionki tekstu kodu i odpowiadać na poziom powiększenia edytora tekstu.  
  
2.  Wszystkie inne elementy interfejsu powinny powiązane ustawienia czcionki środowiska i Odpowiedz na wszelkie globalne zmiany w środowisku. To obejmuje (ale nie jest ograniczona do):  
  
    -   Tekst w menu kontekstowe  
  
    -   Tekst w edytorze ozdób, tekst menu żarówki, szybkie znajdowanie okienku edytora, takich jak i przejdź do okienka  
  
    -   Oznaczanie tekstu w oknach dialogowych, takich jak **Znajdź w plikach** lub **Refaktoryzuj**  
  
### <a name="accessing-the-environment-font"></a>Uzyskiwanie dostępu do środowiska czcionki  
 W kodzie macierzystym lub WinForms czcionki środowiska mogą uzyskiwać przez wywołanie metody `IUIHostLocale::GetDialogFont` po zapytań interfejsu z `SID_SUIHostLocale` usługi.  
  
 Dla systemu Windows Presentation Foundation (WPF), pochodzi z klasy okna dialogowego z poziomu powłoki `DialogWindow` klasy zamiast jego WPF `Window` klasy.  
  
 W języku XAML kod wygląda następująco:
  
```xaml
<ui:DialogWindow  
    x:Class"MyNameSpace.MyWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"  
    ShowInTaskbar="False"  
    WindowStartupLocation="CenterOwner"  
    Title="My Dialog">  
</ui:DialogWindow>  
```

kodzie:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```
  
 (Zastąp `Microsoft.VisualStudio.Shell.11.0` w bieżącej wersji biblioteki dll MPF.)  
  
 Aby wyświetlić okno dialogowe, wywołaj "`ShowModal()`" w klasie za pośrednictwem `ShowDialog()`. `ShowModal()` Ustawia stan modalny w powłoce, gwarantuje, że okno dialogowe jest wyśrodkowane okno nadrzędne i tak dalej.  
  
 Kod jest następujący:  
  
```csharp
MyWindow window = new MyWindow();  
window.ShowModal()  
```
  
 `ShowModal` Zwraca wartość logiczną? (wartość logiczna wartości null) z `DialogResult`, która może zostać użyta, jeśli to konieczne. Wartość zwracana jest wartość true, jeśli w oknie dialogowym został zamknięty z **OK**.  
  
 Jeśli konieczne jest wyświetlenie niektórych WPF interfejsu użytkownika, który nie jest okno dialogowe i znajduje się w jego własnej `HwndSource`, takie jak okna podręcznego lub okna podrzędnego WPF Win32/WinForms okna okna nadrzędnego, należy ustawić `FontFamily` i `FontSize` w elemencie głównym e WPF lementu. (Powłoka ustawia właściwości w oknie głównym, ale nie będą dziedziczone poza `HWND`). Powłoka zawiera zasoby, do których można powiązać właściwości, takie jak to:  
  
```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```
  
###  <a name="BKMK_Formatting"></a> Formatowanie odwołania (skalowanie/pogrubienie)  
 Części okien dialogowych wymagają określonej tekst, który ma być pogrubione lub rozmiar niż czcionki środowiska. Wcześniej, czcionki większy niż czcionki środowiska zostały zakodowane jako "`environment font +2`" lub podobny. Korzystania z wstawek kodu podanego obsługi wysokiej rozdzielczości monitorów i upewnij się, że tekst wyświetlany zawsze jest wyświetlany na odpowiedni rozmiar i wagi (na przykład lekki lub Semilight).  
  
> **Uwaga: Przed zastosowaniem formatowania, upewnij się, zgodnie z instrukcjami podanymi w [styl tekstu](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Aby skalować czcionki środowiska, ustawienie stylu blok tekstu lub etykieta wskazane. Każdy z tych fragmentów kodu, prawidłowo używana, spowoduje wygenerowanie poprawne czcionki, w tym odpowiednie zmiany rozmiaru i wagi.  
  
 Gdzie "`vsui`" jest odwołanie do przestrzeni nazw `Microsoft.VisualStudio.Shell`:  

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```
  
#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + jasny  
 **Pojawia się jako:** 34 pt Segoe UI jasny  
 **Na użytek:** (rzadki przypadek) unikatowy marki interfejsu użytkownika, tak samo, jak w stronę początkową

 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```
  
#### <a name="310-environment-font--light"></a>Czcionka środowiska 310% + jasny  
 **Pojawia się jako:** 28 pt Segoe UI jasny   
 **Na użytek:** tytuły okna dialogowego dużych podpisu, głównego pozycji w raportach  
  
 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```
  
#### <a name="200-environment-font--semilight"></a>200% środowiska czcionki + Semilight  
 **Pojawia się jako:** 18 pkt Segoe UI Semilight    
 **Na użytek:** nagłówki podrzędne, tytułu w małych i średnich okien dialogowych  
  
 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety: 
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```
  
#### <a name="155-environment-font"></a>155% środowiska czcionki  
 **Pojawia się jako:** 14 punktów Segoe UI    
 **Na użytek:** nagłówki sekcji w dokumencie oraz interfejsu użytkownika lub raportów  
  
 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```
  
#### <a name="133-environment-font"></a>133% środowiska czcionki  
 **Pojawia się jako:** 12 punktów Segoe UI    
 **Na użytek:** nagłówki mniejsze podrzędne w oknach dialogowych podpisu i zarządzania dokumentami oraz interfejsu użytkownika  
  
 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```
  
#### <a name="122-environment-font"></a>122% środowiska czcionki  
 **Pojawia się jako:** 11 pkt Segoe UI    
 **Na użytek:** sekcji nagłówków w oknach dialogowych podpisu, top węzłów w widoku drzewa, tabulator pionowy nawigacji  
  
 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```
  
#### <a name="environment-font--bold"></a>Czcionka środowiska + bold  
 **Pojawia się jako:** pogrubiony 9 pt Segoe UI    
 **Na użytek:** etykiet oraz nagłówki w oknach dialogowych podpisu, raporty i dokumentu oraz interfejsu użytkownika  
  
 **Kod procedury:** gdzie `textBlock` jest wcześniej zdefiniowanego blok tekstu i `label` jest uprzednio zdefiniowanej etykiety:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```
  
 **XAML:** ustawienie stylu blok tekstu lub etykiety, jak pokazano:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```
  
### <a name="localizable-styles"></a>Style Lokalizowalny  
 W niektórych przypadkach wiadomość dla lokalizatorów należy zmodyfikować style dla innych języków, takich jak usuwanie pogrubienie w tekście wschodnioazjatyckim języków. Aby umożliwić lokalizacji style, te style musi być w pliku resx. Najlepszy sposób, aby osiągnąć ten cel i edytować style w projektancie formularzy programu Visual Studio jest jawnie ustawiona style czcionek w czasie projektowania. Tworzy obiekt pełne czcionki, i mogą być przerwanie dziedziczenia czcionki nadrzędnego, tylko właściwość FontStyle jest używana do ustawienia czcionki.  
  
 Rozwiązanie polega na połączeniu formularz okna dialogowego `FontChanged` zdarzeń. W `FontChanged` zdarzeń, opisano wszystkie formanty i sprawdź, czy ich czcionki jest ustawiony. Jeśli jest ustawiona, zmień go na nową czcionkę na podstawie formularza czcionki i poprzednich styl czcionki formantu. Na przykład w kodzie jest:  
  
```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
          SetFontStyles();  
}  
  
/// <summary>  
/// SetFontStyles - This function will iterate all controls on a page  
/// and recreate their font with the desired fontstyle.  
/// It should be called in the OnFontChanged handler (and also in the constructor  
/// in case the IUIService is not available so OnFontChange doesn't fire).  
/// This way, when the VS shell font is given to us the controls that have  
/// a different style for the font (bolded for example) will recreate their font  
/// and use the VS shell font but with a style variation (bolded ...).  
/// </summary>   
protected void SetFontStyles()  
{  
     SetFontStyles(this, this, this.Font);  
}  
  
protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)  
{  
     foreach(Control c in parent.Controls)  
     {  
          if (c.Controls != null && c.Controls.Count > 0) {  
               SetFontStyles(topControl, c, referenceFont);  
          }  
          if (c.Font != topControl.Font) {  
               c.Font = new Font(referenceFont, c.Font.Style);  
          }  
     }  
}  
```
  
 Przy użyciu tego kodu gwarantuje po zaktualizowaniu czcionki formularza czcionki formantów uaktualnią również. Tej metody należy także wywołać z konstruktora formularza, ponieważ w oknie dialogowym mogą nie można pobrać wystąpienia `IUIService` i `FontChanged` nigdy nie będzie wyzwalać zdarzeń. Przechwytywanie `FontChanged` umożliwi wyświetlanie dodatkowych okien dialogowych dynamicznie odebrania nowych czcionek, nawet jeśli jest już otwarte okno dialogowe.  
  
### <a name="testing-the-environment-font"></a>Testowanie czcionki środowiska  
 Aby upewnić się, że Twój interfejs użytkownika jest przy użyciu czcionki środowiska i uwzględnia ustawienia rozmiaru, otwórz **Narzędzia > Opcje > środowiska > czcionki i kolory** i wybierz pozycję "Środowisko czcionki" w obszarze "Pokaż ustawienia dla:" menu rozwijanego.  
  
 ![Ustawienia czcionek i kolorów w narzędziach &gt; okno dialogowe Opcje](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />Ustawienia czcionek i kolorów w narzędziach &gt; okno dialogowe Opcje
  
 Ustaw czcionkę bardzo inny niż domyślny. Aby umożliwić oczywiste, który nie powoduje aktualizacji interfejsu użytkownika, wybierz czcionki z szeryfów (na przykład "podzbiory") i ustaw bardzo dużym rozmiarze. Następnie testu interfejsu użytkownika, upewnij się, że jej szanuje środowiska. Oto przykład za pomocą okna dialogowego licencji:  
  
 ![Przykład tekstu interfejsu użytkownika, który nie przestrzega czcionki środowiska](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />Przykład tekstu interfejsu użytkownika, który nie przestrzega czcionki środowiska
  
 W takim przypadku "Informacje o użytkowniku" i "Informacje o produkcie" nie są przestrzeganie czcionki. W niektórych przypadkach może to być wybrany jawną projektu, ale może być usterki, jeśli jawne czcionki nie jest określony jako część specyfikacji redline.  
  
 Aby zresetować czcionki, kliknij przycisk "Użyj ustawień domyślnych" w obszarze **Narzędzia > Opcje > środowiska > czcionki i kolory**.  
  
##  <a name="BKMK_TextStyle"></a> Styl tekstu  
 Styl tekstu odnosi się do rozmiaru czcionki, waga i wielkość liter. Aby uzyskać wskazówki dotyczące implementacji, zobacz [czcionki środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Wielkości liter tekstu  
  
#### <a name="all-caps"></a>Wszystkie wersaliki  
 Nie należy używać wersaliki tytułów lub etykiet w programie Visual Studio.  
  
#### <a name="all-lowercase"></a>Wszystkie małe  
 Nie należy używać małych liter tytułów lub etykiet w programie Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Przypadek zdanie i tytuł  
 Tekst w programie Visual Studio należy używać w przypadku tytuł lub zdaniu, w zależności od sytuacji.  
  
|Użyj nazwy własne dla:|Użyj zdaniu dla:|  
|-------------------------|----------------------------|  
|Okno dialogowe tytułów|Etykiety|  
|Pola grupy|Zaznaczanie pól|  
|Elementy menu|Przyciski opcji|  
|Elementy menu kontekstowego|Elementy pola listy|  
|Przyciski|Paski stanu|  
|Etykiety tabeli||  
|Nagłówki kolumn||  
|Etykietki narzędzi||  
  
##### <a name="title-case"></a>Pisownia tytułów  
 Wielkość liter jest styl kapitalizacji pierwsze litery większość lub wszystkie wyrazy w frazę. W programie Visual Studio wielkość liter jest używany dla wielu elementów, w tym:  
  
-   **Tooltips.** Przykład: "podgląd wybranych elementów"  
  
-   **Nagłówki kolumn.** Przykład: "System odpowiedź"  
  
-   **Elementy menu.** Przykład: "Zapisz wszystkie"  
  
 Korzystając z wielkość liter, są wytyczne dotyczące czasu na wielką słów i kiedy pozostaw je małe litery:  
  
|Wielkie litery|Komentarze i przykłady|  
|---------------|---------------------------|  
|Wszystkie rzeczowniki||  
|Wszystkie zlecenia|W tym "Jest" i inne formy "Aby być"|  
|Wszystkich parametrów|W tym "Od" i "Po"|  
|Wszystkie określeniem|W tym "To" i "Czy"|  
|Wszystkie Zaimki|W tym dzierżawczych "Jego" także niezmieniona"," zmniejszenie zrozumieć "on" i zlecenie "jest"|  
|Imię i nazwisko wyrazy, niezależnie od części mowy||  
|Przyimki, które są częścią frazę zlecenie|"Zamykanie wszystkich systemu Windows" lub "Zamykanie systemu"|  
|Wszystkie litery akronim|HTML, XML, URL, IDE, RGB|  
|Drugi programu word w wyraz złożony, jeśli jest rzeczownik lub przymiotnik własnych lub jeśli wyrażenie ma ta sama waga|Odsyłaczy, oprogramowanie Microsoft wstępne odczytu i zapisu, środowiska wykonawczego|  
  
|Małe litery|Przykłady|  
|---------------|--------------|  
|Drugi wyraz w wyraz złożony, jeśli jest inny część mowy lub participle, modyfikując pierwsze słowo|Porada odbioru|  
|Artykuły, chyba że jeden z nich jest pierwszy wyraz w tytule|,,|  
|Współrzędna spójników|i, ale, ani, lub|  
|Przyimki wyrazów cztery lub mniej liter poza frazę zlecenie|do na, jak w przypadku, out, w górnej części|  
|"Do" w przypadku używania w nieskończona frazy|"How to formatowania dysku twardego"|  
  
##### <a name="sentence-case"></a>Zdaniu  
 Zdaniu jest metoda standardowej wielkości liter do zapisu w kapitalizacji jest tylko pierwszy wyraz zdania, wraz z dowolnej nazwy własne i zrozumieć "I". Ogólnie rzecz biorąc zdaniu łatwiej odbiorców do odczytu, szczególnie gdy zawartość będzie można przetłumaczyć przez maszynę z całego świata. Użyj zdaniu dla:  
  
1.  **Komunikaty paska stanu.** Są to prosty, krótki które zapewniają tylko informacje o stanie. Przykład: "ładowanie projektu pliku"  
  
2.  **Wszystkie inne elementy interfejsu użytkownika**, łącznie z etykiet, pola wyboru, przyciski radiowe i elementy pola listy. Przykład: "Wybierz wszystkie elementy na liście"  
  
### <a name="text-formatting"></a>Formatowanie tekstu  
 Domyślny tekst formatowania w programie Visual Studio 2013 jest kontrolowany przez [czcionki środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Ta usługa zapewnia czcionki spójny wygląd IDE (zintegrowane środowisko programistyczne) i należy go użyć, aby zagwarantować spójne środowisko dla użytkowników.  
  
 Domyślny rozmiar używanego przez usługę Visual Studio czcionki pochodzi z systemu Windows i będzie wyświetlany jako 9 pt.  
  
 Formatowanie do czcionki środowiska można zastosować. W tym temacie opisano, jak i gdzie aby stosować style. Implementacja informacji, zapoznaj się [czcionki środowiska](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Pogrubiony tekst  
 Pogrubiony tekst jest rzadko używana w programie Visual Studio i powinna być zarezerwowana dla:  
  
-   etykiety zapytania w kreatorach  
  
-   wyznaczenie aktywny projekt w Eksploratorze rozwiązań  
  
-   przesłonięcia wartości w oknie właściwości narzędzia  
  
-   określone zdarzenia na liście rozwijanej edytora języka Visual Basic  
  
-   wygenerowana przez serwer zawartości w konspekt dokumentu dla stron sieci web  
  
-   nagłówki sekcji w oknie dialogowym złożonych lub Projektant interfejsu użytkownika  
  
#### <a name="italics"></a>Italics  
 Program Visual Studio nie korzysta z kursywą lub pogrubiony tekst kursywą.  
  
#### <a name="color"></a>Kolor  
  
-   Niebieski jest zarezerwowany dla hiperłącza (nawigacji oraz wydawanie poleceń) i nie mogą być używane dla orientacji.  
  
-   Większe nagłówki (czcionki środowisku x 155% lub większą) mogą być malowane dla tych celów:  
  
    -   Aby zapewnić visual odwołania do sygnatury interfejsu użytkownika programu Visual Studio  
  
    -   Aby zwrócić uwagę na określonym obszarze  
  
    -   Oferowanie zwolnienia z standardowe środowisko szarości/Czarne ciemny kolor tekstu  
  
-   Kolor w nagłówki powinny wykorzystywać funkcję istniejącego programu Visual Studio brand kolory, przede wszystkim głównym purpurowy #FF68217A.  
  
-   Używając kolorów w nagłówki, muszą być zgodne z [Windows kolor wytyczne](https://msdn.microsoft.com/en-us/library/dn742482.aspx), w tym stosunek kontrast i inne zagadnienia dotyczące ułatwień dostępu.  
  
### <a name="font-size"></a>Rozmiar czcionki  
 Visual Studio UI projektowania funkcjami jaśniejszy wygląd więcej spacją. Jeśli to możliwe, chrome i paska tytułu zostały zredukowane lub usunięte. Podczas gęstość informacji jest wymagane w programie Visual Studio, typografii jest nadal ważny, ze szczególnym uwzględnieniem więcej Otwórz odstępy i różnic rozmiary czcionek i wagi.  
  
 W poniższych tabelach zawiera szczegóły dotyczące projektowania i przykłady visual czcionki wyświetlanej w programie Visual Studio. Różne wersje czcionki wyświetlanej ma rozmiar i wagi, takie jak Semilight lub światła w ich wyglądu.  
  
 Wstawki kodu implementacji dla wszystkich czcionek wyświetlania można znaleźć w [formatowania odwołania (skalowanie/pogrubienie)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Czcionka środowiska 375% + jasny  
  
|||  
|-|-|  
|**Sposób użycia:** rzadko. UNIQUE tylko marki interfejsu użytkownika.<br /><br /> **Wykonaj:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika innych niż podpis interfejsu użytkownika, takie jak strona początkowa<br />— Pogrubienie, kursywa lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** 34 pt Segoe UI jasny<br /><br /> **Przykład Visual:**<br /><br /> *Obecnie nieużywane. Mogą być używane w strony początkowej.*|  
  
#### <a name="310-environment-font--light"></a>Czcionka środowiska 310% + jasny  
  
|||  
|-|-|  
|**Sposób użycia:**<br /><br /> — Większa nagłówka w oknach dialogowych podpisu<br />— Nagłówek raportu głównego<br /><br /> **Wykonaj:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj lekkie<br /><br /> **Nie:**<br /><br /> -Użyj interfejsu użytkownika innych niż podpis interfejsu użytkownika, takie jak strona początkowa<br />— Pogrubienie, kursywa lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** 28 pt Segoe UI jasny<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład czcionki środowiska 310% &#43; światła nagłówek](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>200% środowiska czcionki + Semilight  
  
|||  
|-|-|  
|**Sposób użycia:**<br /><br /> -Nagłówki podrzędne<br />-Tytuły w małych i średnich okien dialogowych<br /><br /> **Wykonaj:**<br /><br /> -Użyj zdaniu<br />-Zawsze używaj Semilight wagi<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** 18 pkt Segoe UI Semillight<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład 200% środowiska czcionki &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>155% środowiska czcionki  
  
|||  
|-|-|  
|**Sposób użycia:**<br /><br /> -Section nagłówków w dokumencie oraz interfejsu użytkownika<br />— Raporty<br /><br /> **:** Zdanie przypadek użycia<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj w formantów standardowych programu Visual Studio<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** 14 punktów Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład nagłówka czcionki środowiska 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>133% środowiska czcionki  
  
|||  
|-|-|  
|**Sposób użycia:**<br /><br /> -Nagłówki mniejsze podrzędne w oknach dialogowych podpisu<br />-Nagłówki mniejsze podrzędne w dokumencie oraz interfejsu użytkownika<br /><br /> **:** Zdanie przypadek użycia<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj w formantów standardowych programu Visual Studio<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** 12 punktów Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład nagłówka czcionki środowiska 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>122% środowiska czcionki  
  
|||  
|-|-|  
|**Sposób użycia:**<br /><br /> -Section nagłówków w oknach dialogowych podpisu<br />-Top węzłów w widoku drzewa<br />— Nawigacji kart pionowe<br /><br /> **:** Zdanie przypadek użycia<br /><br /> **Nie:**<br /><br /> — Pogrubienie, kursywa lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj w formantów standardowych programu Visual Studio<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** 11 pkt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład nagłówka czcionki środowiska 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>Czcionka środowiska + bold  
  
|||  
|-|-|  
|**Sposób użycia:**<br /><br /> -Etykiet oraz nagłówki w oknach dialogowych podpisu<br />-Etykiet oraz nagłówki w raportach<br />-Etykiety i podnagłówkami w dokumencie oraz interfejsu użytkownika<br /><br /> **Wykonaj:**<br /><br /> -Użyj zdaniu<br />-Użyj bold wagi<br /><br /> **Nie:**<br /><br /> -Kursywą lub pogrubienie, kursywa<br />-Użyj tekstu treści<br />-Użyj w formantów standardowych programu Visual Studio<br />-Użyj narzędzia systemu Windows|**Pojawia się jako:** pogrubiony 9 pt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład środowiska czcionki &#43; pogrubiony nagłówek](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|  
  
#### <a name="environment-font"></a>Środowisko czcionki  
  
|||  
|-|-|  
|**Sposób użycia:** inny tekst<br /><br /> **:** Zdanie przypadek użycia<br /><br /> **Nie:** kursywa lub pogrubienie, kursywa|**Pojawia się jako:** 9 pt Segoe UI<br /><br /> **Przykład Visual:**<br /><br /> ![Przykład środowiska czcionki](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|  
  
### <a name="padding-and-spacing"></a>Wypełnienie i odstępy  
 Nagłówki wymagają ich nadanie im odpowiedni nacisk wolnego miejsca. Ta przestrzeń różni się w zależności od rozmiaru punktu i co jest bliski pozycji, takich jak linia pozioma lub wiersz tekstu w środowisku czcionki.  
  
-   Dopełnienie nadaje się doskonale dla pozycji samodzielnie powinna być 90% kapitału znak odstępu wysokość. Na przykład nagłówek Segoe UI jasny 28 pt ma zakończenia wysokości 26 pt i uzupełnienie powinien być około 23 pt lub około 31 pikseli.  
  
-   Minimalny odstęp wokół nagłówek powinna być 50% kapitału wielkość czcionki. Może być używany mniej miejsca, gdy nagłówek towarzyszy reguły lub innego elementu ściśle dopasowane.  
  
-   Pogrubiony tekst czcionki środowiska powinien być zgodny domyślna wysokość odstępy i wypełnieniem.  
  
## <a name="see-also"></a>Zobacz też  
 [MSDN: Czcionek (system Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [Witrynie MSDN: Tekst interfejsu użytkownika (system Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)