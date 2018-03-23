---
title: Kolory i style dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/31/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af9522d5773fd74eabcd3b7fce84b7bd56e0cd2a
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="colors-and-styling-for-visual-studio"></a>Kolory i style dla programu Visual Studio
## <a name="using-color-in-visual-studio"></a>Przy użyciu kolorów w programie Visual Studio
W programie Visual Studio kolor jest używany głównie narzędzie komunikacji, nie tylko jako decoration. Użyj koloru minimalny zestaw i go zarezerwować dla sytuacji, w której chcesz:

-   Komunikować się znaczenie lub przynależności (na przykład Modyfikatory platformy lub language)

-   Zwróć uwagę, (na przykład wskazującego zmianę stanu)

-   Poprawa czytelności i podaj punkty orientacyjne nawigowanie po Interfejsie użytkownika

-   Zwiększ potrzebę

Istnieje kilka opcji przypisywania kolorów do elementów interfejsu użytkownika w programie Visual Studio. Czasami może być trudne figure out, która opcja jest powinien używać lub jak z niego korzystać poprawnie. W tym temacie ułatwią:

1.  Zrozumienie różnych usług i systemy używane do definiowania kolorów w Visual Studio.

2.  Wybierz opcję odpowiednią dla danego elementu.

3.  Poprawnie opcja wybrana.

> **Uwaga:** nigdy nie umieszczaj hex, RGB lub kolorów systemu do elementów interfejsu użytkownika. Przy użyciu usługi umożliwia elastyczność w dostrajaniu hue. Ponadto bez usługi, nie będzie mógł skorzystać z możliwości przełączania motywu [usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Elementy interfejsu metody przypisywania kolorów dla programu Visual Studio
Wybierz metodę najlepiej nadaje się do elementów interfejsu użytkownika.

| Interfejsu użytkownika | Metoda | Co to są one? |
| --- | --- | --- |
| Zostały osadzone lub autonomiczny okien dialogowych. | **Kolorów systemu** | System nazw, które system operacyjny zdefiniować kolor i wygląd elementów interfejsu użytkownika, takie jak typowych formantów okna dialogowego. |
| Masz niestandardowego interfejsu użytkownika, które mają być zgodne z ogólną środowiska VS i masz elementów interfejsu użytkownika, które pasują do kategorii i znaczenie semantyczne, udostępnionego tokenów. | **Typowe udostępnionego kolorów** | Istniejące nazwy tokenu kolor wstępnie zdefiniowanego dla określonych elementów interfejsu użytkownika |
| Masz poszczególnych funkcji lub grupy funkcji i nie ma żadnych udostępnionego kolor podobnych elementów. | **Kolory niestandardowe** | Nazwy tokenu kolorów, które są specyficzne dla obszaru i nie mają być współużytkowana z innymi interfejsu użytkownika |
| Chcesz zezwolić użytkownikom końcowym dostosowywanie interfejsu użytkownika lub zawartości (na przykład edytory tekstów lub specjalne projektanta systemu windows). | **Dostosowywanie przez użytkownika końcowego**<br /><br />**(Narzędzia &gt; okna dialogowego Opcje)** | Ustawienia zdefiniowane na stronie "Czcionki i kolory" **narzędzia &gt; opcje** okna dialogowego lub specjalne specyficzne dla jednej funkcji interfejsu użytkownika strony. |

### <a name="visual-studio-themes"></a>Visual Studio motywów
Trzy motywy kolorów różnych funkcji programu Visual Studio: światła ciemny i niebieski. Ta funkcja wykrywa także trybie dużego kontrastu, który jest przeznaczony dla ułatwień dostępu kompozycja kolorów systemu.

Użytkownicy wyświetlony monit o wybranie motywu podczas ich pierwszym użyciu programu Visual Studio i można przełączać kompozycje później, przechodząc do **narzędzia &gt; opcje &gt; środowiska &gt; ogólne** i wybierając polecenie Nowy motyw z menu rozwijane "Kolor motywu".

Użytkowników można również przełączyć do jednego z kilku kompozycji duży kontrast całego systemu za pomocą Panelu sterowania. Jeśli użytkownik wybierze kompozycję Duży kontrast, następnie selektor motywu kolorów w Visual Studio już ma wpływ na kolory w programie Visual Studio, mimo że wszelkie zmiany motywu są zapisywane dla, gdy użytkownik opuszcza tryb dużego kontrastu. Aby uzyskać więcej informacji o trybie dużego kontrastu, zobacz [Wybieranie duży kontrast kolorów](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Usługa VSColor
Visual Studio udostępnia usługę kolorów środowiska, znane jako usługa VSColor, dzięki czemu można powiązać wartości kolorów elementy interfejsu użytkownika do nazwanego wpisu zawierający wartości kolorów dla każdego motywu programu Visual Studio. Daje to pewność, że kolory automatycznie zmieni się odpowiednio bieżący użytkownik wybrał motyw lub system trybie dużego kontrastu. Korzystanie z usługi oznacza, że implementacja wszystkie zmiany dotyczące motywu kolorów jest obsługiwany w jednym miejscu, a jeśli używasz wspólnych kolorów udostępniony przez usługę interfejsu użytkownika automatycznie zostaną one zastosowane nowej kompozycji w przyszłych wersjach programu Visual Studio.

### <a name="implementation"></a>Implementacja
Kod źródłowy programu Visual Studio zawiera kilka plików definicji pakietu, które zawierają listy tokenów nazw i wartości kolorów odpowiednich dla każdego motywu. Usługa kolor odczytuje VSColors zdefiniowane w tych plikach definicji pakietu. Kolory jest przywoływany w kodzie XAML, lub w kodzie i następnie ładowane przy użyciu jednej `IVsUIShell5.GetThemedColor` metody lub mapowania DynamicResource.

### <a name="system-colors"></a>Kolorów systemu
Formanty standardowe odwołanie kolory systemowe zostaną domyślnie. Jeśli chcesz, aby Twój interfejs użytkownika do Użyj kolorów systemu, takie jak podczas tworzenia okna dialogowego autonomiczny lub osadzonych, nie trzeba wykonywać żadnych czynności.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Typowe udostępnionego kolorów w usłudze VSColor
Elementów interfejsu powinien odzwierciedlać ogólną środowiska Visual Studio. Na podstawie wspólnej udostępnionego kolorów, które są odpowiednie dla składnika interfejsu użytkownika, który projektowania, upewnij się że interfejsu jest zgodny z innych interfejsów Visual Studio i kolory uaktualnią automatycznie po motywów zostały dodane lub zaktualizowane.

Przed użyciem wspólnych udostępnionego kolorów, upewnij się, że rozumiesz, jak ich używać poprawnie. Nieprawidłowe użycie wspólnych kolorów udostępnionego może spowodować niespójne, irytujące lub niejasny środowisko dla użytkowników.

### <a name="user-customizable-colors"></a>Użytkownika można dostosować kolory
Zobacz: [udostępnianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Czasami można zezwolić użytkownikom końcowym dostosowywanie interfejsu użytkownika, takie jak podczas tworzenia edytora kodu lub powierzchnię projektu. Elementy interfejsu użytkownika znajdują się w **czcionki i kolory** sekcji **narzędzia &gt; opcje** okna dialogowego, w którym użytkownicy mogą wybrać, aby zmienić kolor pierwszego planu i tła.

![Narzędzia &gt; okno dialogowe Opcje](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />Narzędzia &gt; okno dialogowe Opcje

##  <a name="BKMK_TheVSColorService"></a> Usługa VSColor
Visual Studio udostępnia usługę kolorów środowiska, nazywany również usługi VSColor lub kolor powłoki. Ta usługa służy do wartości kolorów elementy interfejsu użytkownika należy powiązać zestaw zawierający kolorów dla każdego motywu kolorów nazwa wartość. Usługa VSColor należy użyć dla wszystkich elementów interfejsu użytkownika, dzięki czemu kolory automatycznie zmieniać, aby odzwierciedlić bieżącego motywu wybrane przez użytkownika i tak, aby interfejsu użytkownika powiązany z usługami kolorów środowiska zostanie zintegrowana z nowej kompozycji w przyszłości wersji programu Visual Studio.

### <a name="how-the-service-works"></a>Jak działa usługa
Środowisko usługi kolor odczytuje VSColors zdefiniowane w .pkgdef składnik interfejsu użytkownika. VSColors te są następnie odwoływać w kodzie XAML lub kodu i są ładowane przy użyciu jednej `IVsUIShell5.GetThemedColor` lub `DynamicResource` mapowania.

![Architektura usługi kolorów środowiska](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Architektura usługi kolorów środowiska

### <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi
Istnieje kilka różnych metod dostępu korzystają z usługi VSColor, w zależności od tego, jakiego rodzaju kolor tokeny należy i Kod jakiego rodzaju masz.

#### <a name="predefined-environment-colors"></a>Wstępnie zdefiniowane środowiska kolorów

##### <a name="from-native-code"></a>Z kodu natywnego
Powłoka udostępnia usługę, która zapewnia dostęp do `COLORREF` kolorów. Interfejs/usługi jest:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

W pliku VSShell80.idl, wyliczenia `__VSSYSCOLOREX` ma stałe kolor powłoki. Aby go użyć, przekazywane jako wartość indeksu jednej wartości z `enum __VSSYSCOLOREX` udokumentowane w witrynie MSDN lub indeks regularne number, który system Windows API, `GetSysColor`, akceptuje. Spowoduje to powrót pobiera wartości RGB kolorów, które mają być używane w drugi parametr.

Przechowywanie pióro lub pędzla o nowy kolor, należy `AdviseBroadcastMessages` (wylogowuje Visual Studio shell) i nasłuchiwania `WM_SYSCOLORCHANGE` i `WM_THEMECHANGED` wiadomości.


Aby uzyskać dostęp do usługi kolorów w kodzie natywnym, należy podjąć podobny to wywołanie:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> **Uwaga:** `COLORREF` wartości zwracanych przez `GetVSSysColorEx()` zawierają tylko R, G, składniki B kolor motywu. Jeśli wpis motywu używa przejrzystości, wartość kanału alfa zostanie usunięty przed zwróceniem. W związku z tym Jeśli kolor środowiska zainteresowań musi można używać w miejscu, gdzie kanał przezroczystość jest ważne, należy użyć `IVsUIShell5.GetThemedColor` zamiast `IVsUIShell2::GetVSSysColorEx`, zgodnie z opisem w dalszej części tego tematu.

##### <a name="from-managed-code"></a>Z kodu zarządzanego
Uzyskiwanie dostępu do usługi VSColor za pomocą kodu natywnego jest bardzo prosta. Podczas pracy za pomocą kodu zarządzanego, jednak określania sposobu korzystania z usługi może być trudnych. Z tym pamiętać Oto fragment kodu C# prezentacja ten proces:

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Jeśli pracujesz w języku Visual Basic, należy użyć:

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Z poziomu interfejsu użytkownika WPF
Można powiązać kolorów wartości wyeksportowane do aplikacji z programu Visual Studio `ResourceDictionary`. Poniżej przedstawiono przykładowy używa zasobów z tabeli kolorów, a także powiązanie z danymi czcionki środowiska w języku XAML.

```
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Pomocnik klasy i metody dla zarządzanego kodu
Dla kodu zarządzanego, biblioteki zarządzane Framework pakietu powłoki (`Microsoft.VisualStudio.Shell.12.0.dll`) zawiera kilka klas pomocniczych umożliwia korzystanie z zastosowanymi motywami kolorów.

Metody pomocnicze w `Microsoft.VisualStudio.Shell.VsColors` obejmują klasy w MPF `GetThemedGDIColor()` i `GetThemedWPFColor()`. Tych metod pomocniczych zwraca wartość koloru motywu wpisu jako `System.Drawing.Color` lub `System.Windows.Media.Color`do używania w WinForms lub interfejsu użytkownika aplikacji WPF.

```
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

Klasy mogą służyć do uzyskania identyfikatorów VSCOLOR dla danego klucza zasobu kolorów WPF, albo na odwrót.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Metody `VsColors` klasy zapytania zwracanej wartości koloru zawsze ich wywołania usługi VSColor. Można uzyskać wartości koloru jako `System.Drawing.Color`, zamiast z lepszą wydajność ma zamiast tego użyj metody `Microsoft.VisualStudio.PlatformUI.VSThemeColor` klasy, która przechowuje uzyskane z usługi VSColor wartości kolorów. Klasa zdarzeń komunikatów rozgłaszanych powłoki subskrybuje wewnętrznie i odrzuca wartość w pamięci podręcznej, gdy wystąpi zdarzenie zmiany motywu. Ponadto zapewnia klasy. Zdarzenie NET przyjaznego subskrybować zmiany motywu. Użyj `ThemeChanged` zdarzenie, aby dodać nowy program obsługi i używać `GetThemedColor()` metodę, aby uzyskać kolor wartości `ThemeResourceKeys` zainteresowań. Przykładowy kod może wyglądać następująco:

```
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

##  <a name="BKMK_ChoosingHighContrastColors"></a> Wybieranie kolorów Duży kontrast

### <a name="overview"></a>Omówienie
System Windows używa kilku motywów systemowe dużego kontrastu zwiększyć kolor tekstu, tła i obrazów, tworzenie elementów są wyświetlane na ekranie znacznie. Ze względu na dostępność jest ważne, czy elementy interfejsu programu Visual Studio poprawnej odpowiedzi, gdy użytkownicy będą przełączać się do motyw z wysokim kontrastem.

Tylko garstka kolorów systemu może służyć do dużego kontrastu motywów. Przy wyborze nazwy kolorów systemu, należy pamiętać o następujących wskazówek:

1.  **Wybierz kolorów systemu, które mają takie samo znaczenie semantyczne** jako element, do którego są kolorowania. Na przykład wybierzesz dużego kontrastu kolor tekstu w oknie, należy użyć, WindowText i nie ControlText.

2.  **Wybierz pary narzędzia/tła** ze sobą ani nie będziesz mieć pewność, że wybrany kolor będzie działać w wszystkie kompozycje duży kontrast.

3.  **Określenie części interfejsu użytkownika, które są najważniejsze i upewnij się, że wyróżnienia obszarów zawartości.** Wiele szczegółów niewielkie różnice w kolor odcienia, który będzie zwykle rozróżnić, zostaną utracone, więc Użyj kolorów obramowania silne jest typowe określenie obszarów zawartości, ponieważ nie nie wariantów kolorów dla różnych obszarów zawartości.

### <a name="system-color-set"></a>Zestaw kolorów systemu
Tabeli na [blogu zespołu programu WPF: odwołanie SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) wskazuje pełny zestaw nazwy kolorów systemu i odpowiednie odcienie wyświetlane w każdym motywu.

Podczas stosowania to ograniczony zestaw kolorów do interfejsu użytkownika, *oczekuje się, utracisz niewielkie szczegółowe informacje, które były obecne w kompozycji "normal"*. Poniżej przedstawiono przykład interfejsu użytkownika z niewielkie szarego kolorów, które są używane do odróżnienia obszarów w obrębie okna narzędzia. Łączyć się z tym samym oknie wyświetlany w trybie dużego kontrastu, można wyświetlić wszystkie tła są tego samego hue, a granice z tych obszarów oznaczono obramowanie wyłącznie:

![Przykład sposobu niewielkie szczegóły zostaną utracone w przypadku dużego kontrastu](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Przykład sposobu niewielkie szczegóły zostaną utracone w duży kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Wybór koloru tekstu w edytorze
Pokolorowane tekst jest używany w edytorze lub na powierzchni projektowej wskazująca znaczenie, takie jak pozwalające ułatwiający identyfikację grup podobnych elementów. W kompozycję Duży kontrast jednak nie masz możliwość rozróżnienia między więcej niż trzy kolory tekstu. WindowText, GrayText i HotTrackText są dostępne na powierzchni WindowBackground kolory tylko. Ponieważ nie można użyć więcej niż trzy kolory, wybierz uważnie najważniejsze różnice, które mają być wyświetlane w trybie dużego kontrastu.

Barwy dla każdej nazwy tokenu dozwolone na powierzchni Edytor znajdujące się w każdym kompozycję Duży kontrast:

![Wysoki kontrast Edytor porównanie](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Wysoki kontrast Edytor porównania

Przykłady powierzchni motywu niebieski edytora:

![Edytor w motywu niebieski](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Edytor w motywu niebieski

![Edytor w kompozycję Duży kontrast nr 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Edytor w kompozycję Duży kontrast nr 1

### <a name="usage-patterns"></a>Wzorce użycia
Wiele wspólnych elementów interfejsu użytkownika już duży kontrast kolorów zdefiniowanych. Możesz odwoływać się tych wzorców użycia przy wybieraniu nazwy kolorów własnego systemu tak, aby były zgodne ze składnikami podobnych elementów interfejsu użytkownika.

| Kolor systemu | Użycie |
| --- | --- |
| ActiveCaption | -Active-IDE i symbole przycisk okna rafted aktywowany, a następnie naciśnij klawisz<br />-Tło paska tytułu IDE i rafted systemu windows<br />-Domyślne tło paska stanu |
| ActiveCaptionText | -Active-IDE i rafted systemu windows na pierwszym planie paska tytułu (tekst i symboli)<br />— W tle i obramowania przycisków aktywne okno na aktywowanie i naciśnij klawisz |
| Formant | -Pole kombi, listy rozwijanej i wyszukiwania kontrolować domyślne i wyłączone tło, włącznie z przycisku rozwijanego<br />— Tło przycisku dokowania docelowego<br />— Tło paska polecenie<br />— Tło okna Narzędzie |
| ControlDark | -Tło IDE<br />-Separatory pasek menu i poleceń<br />— Obramowania paska polecenie<br />-Menu shadows<br />-Narzędzie separator i obramowanie domyślne i aktywuje kartę okna<br />-Również dokumentu tło przycisku przepełnienia<br />-Obramowania symbolu docelowego dock |
| ControlDarkDark |— Okno karty bez fokusu, wybranego dokumentu |
| ControlLight |— Obramowanie karty automatyczne ukrywanie<br />-Obramowanie listy, a pole listy rozwijanej kombi<br />-Dock docelowego tła i obramowania |
| ControlLightLight | -Wybranych, konkretną tymczasowego obramowania |
| ControlText | -Kombi pole i rozwijania listy symbolu<br />— Tekst kartę okna niezaznaczony narzędzie |
| GrayText |-Pole kombi i listy rozwijanej wyłączone obramowania symbolu listy rozwijanej, tekst i tekst elementu menu<br />— Tekst menu wyłączone<br />— Tekst nagłówka "Opcje wyszukiwania" kontroli wyszukiwanie<br />— Separator sekcji kontroli wyszukiwanie |
| Wyróżnij | -Wszystkie aktywowanego i naciśniętego tła i obramowania, z wyjątkiem kombi przycisku rozwijanego tła i zarządzania dokumentami oraz przepełnienie przycisk obramowanie<br />-Tło wybranego elementu |
| HighlightText | -Wszystkie aktywowanie i naciśniętego cieniowanie (tekst i symboli)<br />-Narzędzie ukierunkowanych okna i zarządzania dokumentami kartę okna kontrolki pierwszego planu<br />— Obramowanie pasek tytułu okna narzędzia ukierunkowanych<br />-Ukierunkowanych, wybrane kartę tymczasowego pierwszego planu<br />-Również dokumentu obramowania przycisku przepełnienie aktywowany, a następnie naciśnij klawisz<br />— Obramowanie ikony|
| HotTrack | -Przewijania, tło przycisku przewijania i obramowanie naciśnij przycisk paska<br />-Paska przewijania symbolu strzałkę na naciśnij klawisz |
| InactiveCaption | -Nieaktywne IDE i symbole przycisk rafted okna przy aktywowaniu<br />-Tło paska tytułu IDE i rafted systemu windows<br />— Tło formantu wyszukiwania wyłączone |
| InactiveCaptionText | -Nieaktywne IDE i narzędzia paska tytułu rafted systemu windows (tekst i symboli)<br />-Tła przycisków nieaktywnym oknie i obramowania przy aktywowaniu<br />— Tło przycisku okna narzędzia bez fokusu, obramowania<br />— Pierwszego planu formantu wyszukiwania wyłączone |
| Menu | Listy rozwijanej tła menu<br />-Checked, jak i wyłączonych znacznik wyboru tła |
| MenuText | -Listy rozwijanej menu obramowania<br />-Znaczników zaznaczenia<br />— Symbole menu<br />Listy rozwijanej tekst menu<br />— Obramowanie ikony |
| Pasek przewijania | -Przewiń pasek i Strzałka w tle, wszystkie stany — pasek przewijania |
| Okno | — Automatyczne ukrywanie kartę tła<br />— Menu pasek oraz poleceń półki tła<br />— Tło kartę okno dokumentu bez fokusu lub niezaznaczone i obramowanie dokumentu, otwartych i tymczasowego karty<br />— Tło paska tytułu okna narzędzia bez fokusu<br />— Tło karcie okna tool, zarówno zaznaczony i niezaznaczony |
| WindowFrame | -Obramowanie IDE |
| WindowText | — Automatyczne ukrywanie kartę pierwszoplanowe<br />-Wybranego narzędzia okna kartę pierwszoplanowe<br />— Karta okna dokumentu bez fokusu i pierwszego planu kartę tymczasowego bez fokusu lub niezaznaczone<br />-Drzewa widok domyślny kolor pierwszego planu i aktywowanych za pośrednictwem niezaznaczone symbolu<br />— Okno narzędzia zaznaczona obramowanie karty<br />-Paska przewijania tło przycisku przewijania, obramowania i symbolu |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> Udostępnianie kolorów dla użytkowników końcowych

### <a name="overview"></a>Omówienie
Czasami można zezwolić użytkownikom końcowym dostosowywanie interfejsu użytkownika, takie jak podczas tworzenia edytora kodu lub powierzchnię projektu. Jest najczęściej w tym celu za pomocą **narzędzia &gt; opcje** okna dialogowego. Chyba że znajduje się bardzo specjalistyczny interfejsu użytkownika, który wymaga specjalnych formantów, najprostszym sposobem prezentować dostosowań jest za pośrednictwem **czcionki i kolory** strony w ramach **środowiska** sekcji okna dialogowego. Dla każdego elementu, który ujawnia do dostosowania użytkownik może zmienić kolor pierwszego planu i tła.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Tworzenie pakiet VSPackage dla dostosowania kolorów
Pakiet VSPackage można kontrolować, czcionki i kolory za pomocą niestandardowych kategorii i wyświetlania elementów na stronie właściwości czcionek i kolorów. Korzystając z tego mechanizmu, musi implementować VSPackages [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interfejsu i skojarzone interfejsy.

W zasadzie mechanizm ten może służyć do modyfikowania wszystkie istniejące elementy wyświetlania i kategorie, które je zawiera. Jednak nie ją stosować do modyfikowania kategorii Edytor tekstów lub jego elementów wyświetlania. Aby uzyskać więcej informacji o kategorii Edytor tekstów, zobacz [Omówienie kolorów i czcionek](../font-and-color-overview.md).

Do wdrożenia niestandardowe kategorie lub Wyświetl elementy, pakiet VSPackage musi:

-   **Tworzenie lub identyfikowanie kategorii w rejestrze.** Implementacja programu IDE **czcionki i kolory** strony właściwości używa tych informacji do poprawnie kwerendy usługi obsługujące danej kategorii.

-   **Tworzenie lub identyfikowanie grup w rejestrze (opcjonalnie).** Może być przydatne do zdefiniowania grupy, która reprezentuje sumę dwóch lub więcej kategorii. Jeśli zdefiniowano grupy, IDE automatycznie scala podkategorie i dystrybuuje wyświetlania elementów w obrębie grupy.

-   **Implementuje Obsługa środowiska IDE.**

-   **Obsługa zmiany czcionek i kolorów.**

#### <a name="to-create-or-identify-categories"></a>Aby utworzyć lub wskazać kategorii
Utworzyć specjalny typ wpisu rejestru kategorii `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` gdzie `<Category>` niezlokalizowana nazwa kategorii.

Wypełnij rejestru z dwóch wartości:

| Nazwa | Typ | Dane | Opis |
| --- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzone w celu identyfikacji kategorii |
| Package | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi pakiet VSPackage, która obsługuje kategorii |

 Usługi określonego w rejestrze musi zapewniać implementację elementu [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) odpowiedniej kategorii.

#### <a name="to-create-or-identify-groups"></a>Aby utworzyć lub wskazać grupy
Utworzyć specjalny typ wpisu rejestru kategorii `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` gdzie `<group>` to niezlokalizowana Nazwa grupy.

Wypełnij rejestru z dwóch wartości:

| Nazwa | Typ | Dane | Opis |
|--- | --- | --- | --- |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID utworzone w celu identyfikacji kategorii |
| Package | REG_SZ | Identyfikator GUID | Identyfikator GUID usługi pakiet VSPackage, która obsługuje kategorii |

Usługi określonego w rejestrze musi zapewniać implementację elementu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> dla odpowiedniej grupy.

![Implementacja IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Implementacja interfejsu `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Obsługa środowiska IDE
Implementowanie [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), który zwraca [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfejsu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu do środowiska IDE dla każdej kategorii lub grupy z podanym identyfikatorem GUID.

Dla każdej kategorii obsługuje pakiet VSPackage implementuje oddzielnego wystąpienia [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfejsu.

Metody implementowane za pośrednictwem [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) podać IDE z:

-   Lista wyświetlania elementów w kategorii

-   Lokalizowalny nazwy wyświetlania elementów

-   Wyświetl informacje dla każdego elementu członkowskiego kategorii

 > **Uwaga:** każda kategoria musi zawierać co najmniej jeden element wyświetlania.

Używa IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu, aby zdefiniować związku kilka kategorii.

Jego wdrożenie zapewnia IDE z:

-   Lista kategorii, które składają się na określonej grupy

-   Dostęp do wystąpień [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) obsługi każdej kategorii w grupie

-   Nazwy grup Lokalizowalny

#### <a name="updating-the-ide"></a>Aktualizowanie środowiska IDE
IDE przechowuje informacje o ustawieniach czcionek i kolorów. Dlatego po wszelkich zmianach konfiguracji IDE czcionek i kolorów zapewnia, że pamięć podręczna jest aktualny jest najlepszym rozwiązaniem.

Aktualizacja pamięci podręcznej odbywa się za pośrednictwem [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interfejsu i mogą być wykonywane globalnie lub tylko na wybranych elementów.

### <a name="handling-font-and-color-changes"></a>Obsługa czcionek i kolorów zmiany
Aby poprawnie obsługiwać kolorowania tekstu, który zawiera pakiet VSPackage, usługi kolorowania obsługujący pakiet VSPackage musi odpowiedzieć na zainicjowane przez użytkownika zmiany wprowadzane za pośrednictwem strony właściwości czcionek i kolorów.

Aby to zrobić, pakiet VSPackage musi:

-   **Obsługa zdarzeń generowanych przez IDE** zaimplementowanie [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interfejsu. IDE wywołuje odpowiednią metodę po modyfikacji użytkownika strony czcionek i kolorów. Na przykład wywołuje [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) metodę, jeśli wybrano nowej czcionki.

 **OR**

-   **sondowanie IDE zmiany**. Można to zrobić za pomocą systemu zaimplementowana [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfejsu. Mimo że przede wszystkim dotyczące obsługi trwałości, [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) metody można uzyskać informacji o czcionek i kolorów dla wyświetlania elementów. Aby uzyskać więcej informacji na temat ustawień czcionek i kolorów, zobacz artykuł w witrynie MSDN [podczas uzyskiwania dostępu do przechowywanych czcionkę i ustawienia koloru](../accessing-stored-font-and-color-settings.md).

> **Uwaga:** aby upewnić się, że wyniki sondowania są prawidłowe, należy użyć [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interfejs do ustalenia, czy czyszczenie pamięci podręcznej i aktualizacji są potrzebne przed wywołaniem metody pobierania [ IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfejsu.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Rejestrowanie niestandardowe czcionek i kolorów kategorii bez implementowanie interfejsów
W poniższym przykładzie pokazano, jak zarejestrować niestandardowych czcionki i kolor kategorii bez implementowanie interfejsów:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

W tym przykładzie kodu:
-   `"NameID"` Identyfikator zasobu o nazwie zlokalizowanej kategorii w pakiecie =
-   `"ToolWindowPackage"` = Identyfikator GUID pakietu
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` jest tylko przykładowe i rzeczywista wartość może być udostępniane przez implementujący nowego identyfikatora GUID.

### <a name="set-the-font-and-color-property-category-guid"></a>Ustaw kategorię właściwości czcionek i kolorów identyfikator GUID
W poniższym przykładzie kodu pokazano ustawienie kategorii identyfikatorów GUID.

```
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
