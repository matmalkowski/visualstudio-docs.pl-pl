---
title: Edytor kolor VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3404505da4b006327aebb5b8cd7b69fc69e218d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147951"
---
# <a name="vsix-color-editor"></a>Edytor kolor VSIX
Narzędzia Visual Studio rozszerzenia kolor edytora można tworzyć i edytować kolorów niestandardowych dla programu Visual Studio. Narzędzie można również generować klucze zasobów motywu, dzięki czemu kolory może być używane w kodzie. To narzędzie jest przydatne w przypadku wprowadzania kolorów dla rozszerzenia Visual Studio, który obsługuje tworzenia motywów. To narzędzie może otwierać pliki .pkgdef i XML. Visual Studio motywów (pliki .vstheme) może służyć z edytora programu Visual Studio rozszerzenia kolor zmieniając rozszerzenie pliku .xml. Ponadto pliki .vstheme można importować do bieżącego pliku .xml.  
  
 ![VSIX Edytor kolor bohater](../../extensibility/internals/media/vsix-color-editor-hero.png "bohater kolor edytora pliku VSIX")  
  
 **Pliki definicji pakietu**  
  
 Pliki definicji (.pkgdef) pakietu to pliki, które definiowania kompozycji. Same kolory są przechowywane w plikach XML kolor motywu, które są kompilowane do pliku .pkgdef. Pliki .pkgdef są wdrożone do wyszukiwania lokalizacji programu Visual Studio, przetwarzane w czasie wykonywania i scalane do definiowania kompozycji.  
  
 **Kolor tokenów**  
  
 Token kolor składa się z czterech elementów:  
  
-   **Nazwa kategorii:** logiczne grupowanie zestaw kolorów. Użyj istniejącej nazwy kategorii, jeśli istnieje już kolorów, które są specyficzne dla żądanego elementu interfejsu użytkownika lub grupę elementów interfejsu użytkownika.  
  
-   **Nazwa tokenu:** opisową nazwę koloru token i token zestawów. Zestawy obejmują tła i pierwszego planu (tekst) tokenu nazwy, a także ich stanów, a te powinno być nazwanym tak, aby łatwo zidentyfikować pary i stanów, które dotyczą one.  
  
-   **Kolor wartości (lub barwy):** wymagane dla każdego kolorowe motywu. Zawsze twórz tła i tekstu wartości kolorów w parach. Kolory są skojarzone dla tła/pierwszego planu, dzięki czemu jest zawsze czytelny względem koloru tła, na którym zostanie narysowana kolor tekstu. Kolorów te są połączone i będzie można używać razem w interfejsie użytkownika. Jeśli w tle nie jest przeznaczony do użycia z tekstem, nie definiują kolor pierwszego planu.  
  
-   **Nazwa systemowa kolorów:** do użycia w Wyświetla wysokim kontraście.  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 Jak to możliwe, i odpowiednio istniejących kolorów Visual Studio powinien nastąpić zamiast wprowadzania nowych. Jednak w przypadkach, gdzie są zdefiniowane nie odpowiednie kolory, kolory niestandardowe należy utworzyć przechowywania zgodne Tworzenie rozszerzeń motywów.  
  
 **Tworzenie nowych tokenów kolorów**  
  
 Aby utworzyć kolorów niestandardowych za pomocą edytora kolor rozszerzenia Visual Studio, wykonaj następujące kroki:  
  
1.  Określ nazwy kategorii i token nowe tokeny kolorów.  
  
2.  Wybierz barwy, które elementu interfejsu użytkownika będą używane dla każdej kompozycji i kolorów systemu dla dużego kontrastu.  
  
3.  Edytor kolorów do tworzenia nowych tokenów kolorów.  
  
4.  Użyj kolorów rozszerzenia programu Visual Studio.  
  
5.  Testowanie zmian w programie Visual Studio.  
  
 **Krok 1: Określanie tokenu nazwy nowe tokeny kolorów i kategorii.**  
  
 Preferowany nazewnictwa schemat jest VSColor **[kategorii] [typ interfejsu użytkownika] [stanu]**. Nie należy używać słowa "color" w nazwach VSColor, ponieważ jest nadmiarowy.  
  
 Nazwy kategorii Podaj logiczne grupy i powinien być zdefiniowany jako ściśle, jak to możliwe. Na przykład nazwa okna pojedyncze narzędzie może być nazwa kategorii, ale nazwa całej działalności zespołu jednostki lub projektu nie jest. Grupowanie wpisy na kategorie pomaga uniknąć pomylenia kolory o takiej samej nazwie.  
  
 Nazwa tokenu wyraźnie musi wskazywać typ elementu i sytuacji lub "stan", dla których zostaną zastosowane kolor. Na przykład aktywne dane Porada w **[typ interfejsu użytkownika]** może być nazwane "**etykietek danych**" i **[stanu]** może być nazwane "**Active**," wynikowe w Nazwa koloru "**DataTipActive**." Ponieważ etykietki danych mają tekstu, pierwszego planu, jak i kolor tła muszą być zdefiniowane. Za pomocą sparowania tła/pierwszego planu, Edytor kolor automatycznie utworzy kolory "**DataTipActive**" tła i "**DataTipActiveText**" planu.  
  
 Jeśli element interfejsu użytkownika ma tylko jeden stan **[stanu]** można pominąć części nazwy. Na przykład, jeśli pole wyszukiwania ma obramowanie i nie ma żadnej zmiany stanu, które będą wpływać na kolor obramowania, następnie nazwy dla tokenu kolor obramowania po prostu można wywołać "**SearchBoxBorder**."  
  
 Niektóre typowe nazwy stanu obejmują:  
  
-   Aktywne  
  
-   Nieaktywne  
  
-   Etykietka wskaźnika myszy  
  
-   MouseDown  
  
-   Wybrane  
  
-   Fokus  
  
 Przykłady kilka nazw tokenu dla części kontrolki elementu listy:  
  
-   ListItem  
  
-   ListItemBorder  
  
-   ListItemMouseOver  
  
-   ListItemMouseOverBorder  
  
-   ListItemSelected  
  
-   ListItemSelectedBorder  
  
-   ListItemDisabled  
  
-   ListItemDisabledBorder  
  
 **Krok 2: Wybierz barwy, które elementu interfejsu użytkownika będą używane dla każdej kompozycji i kolorów systemu dla dużego kontrastu.**  
  
 Wybierając kolory niestandardowe dla interfejsu użytkownika, wybierz podobne istniejącego elementu interfejsu użytkownika, a następnie użyć jego kolorów jako podstawa. Kolory — wewnętrzne elementy interfejsu użytkownika zostały poddane przeglądach i testowaniu, tak aby będzie wyglądać odpowiednie i zachowywać się poprawnie w wszystkich tematów.  
  
 **Krok 3: Edytor kolor utworzyć nowe tokeny kolorów.**  
  
 Uruchom Edytor kolorów i otwarcia lub utworzenia nowego pliku .xml niestandardowy motyw kolorów. Wybierz **Edytuj > nowy kolor** z menu. Spowoduje to otwarcie okna dialogowego służący do określania kategorii i co najmniej jedną nazwę dla wpisów kolorów w ramach tej kategorii:  
  
 ![Edytor kolor VSIX kolorem](../../extensibility/internals/media/vsix-color-editor-new-color.png "Edytor kolor VSIX kolorem")  
  
 Wybierz istniejącą kategorię lub **nową kategorię** Aby utworzyć nową kategorię. Zostanie otwarte inne okno dialogowe Tworzenie nazwę nowej kategorii:  
  
 ![VSIX Edytor kolor nową kategorię](../../extensibility/internals/media/vsix-color-editor-new-category.png "nowej kategorii Edytor kolor VSIX")  
  
 Nową kategorię stanie się dostępne w **nowy kolor** menu rozwijanego kategorii. Po wybraniu kategorii, wprowadź nazwę jeden na wiersz dla każdego nowego tokenu kolorów i wybierz opcję "Utwórz", po zakończeniu:  
  
 ![VSIX Edytor kolor nowy kolor wypełnienia](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX Edytor kolor nowy kolor wypełnienia")  
  
 Wartości kolorów są wyświetlane w parach tła/pierwszego planu z "None" wskazujący, że nie został zdefiniowany kolor. Uwaga: Jeśli kolor nie ma tekstu koloru/tła pary kolorów, następnie tylko tła musi ma zostać zdefiniowana.  
  
 ![Wartości kolorów Edytor kolor VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "wartości kolorów kolor edytora pliku VSIX")  
  
 Aby edytować token kolorów, wybierz pozycję kolor motywu (kolumna) tego tokenu. Dodaj wartość koloru, wpisując wartości szesnastkowych koloru w formacie ARGB 8-cyfrowy, wpisując nazwę kolorów systemu w komórce, lub przy użyciu menu rozwijanego wybierz żądany kolor za pomocą zestawu suwaków lub listę kolorów systemu.  
  
 ![Kolor edycji edytora kolor VSIX](../../extensibility/internals/media/vsix-color-editor-edit-color.png "kolor edycji edytora kolor VSIX")  
  
 ![VSIX Edytor kolor tła](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX Edytor kolor tła")  
  
 Dla składników, które nie są do wyświetlania tekstu, wprowadź wartość tylko jeden kolor: kolor tła. W przeciwnym razie wprowadź wartości koloru tekstu i tła rozdzielonych ukośnikiem.  
  
 Podczas wprowadzania wartości dla dużego kontrastu, wprowadź prawidłowe nazwy kolorów systemu Windows. Nie należy wprowadzać wartości ARGB zapisane na stałe. Lista nazw kolor prawidłowego systemu można wyświetlić, wybierając "Tła: System" lub "pierwszego planu:" z menu rozwijanego wartości kolorów. Podczas tworzenia elementów, które mają składniki tekstu, para kolorów systemu poprawny tła/tekst lub tekst może być niemożliwe do odczytania.  
  
 Po zakończeniu tworzenia, ustawienia i edytowanie tokenów kolorów, należy je zapisać w żądanej XML lub .pkgdef format. Kolor tokeny ani na tle ani zestaw pierwszego planu zostanie zapisana jako pusty kolorów w formacie XML, ale odrzucone w formacie .pkgdef. Okno dialogowe wyświetli ostrzeżenie o utracie kolorów przy próbie zapisać w pliku .pkgdef pusty kolorów.  
  
 **Krok 4: Użyj kolorów rozszerzenia programu Visual Studio.**  
  
 Po zdefiniowaniu nowy kolor tokeny, obejmują .pkgdef w pliku projektu z "Akcja kompilacji" ustawioną na "Zawartość" i "Obejmują w pliku VSIX" ustawiony na wartość "True".  
  
 ![Edytor kolor VSIX pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "pkgdef VSIX kolorem edytora")  
  
 W Visual Studio rozszerzenia kolor edytorze, wybierz Plik > Widok zasobów kod, aby wyświetlić kod, który służy do uzyskiwania dostępu do niestandardowego kolory na architekturach WPF interfejsu użytkownika.  
  
 ![Podgląd kolor edytora kodu zasobu VSIX](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX kolor edytora kodu zasobu podglądu")  
  
 Uwzględnij ten kod w klasie statycznej w projekcie. Odwołanie do **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** musi zostać dodany do projektu, aby użyć **elementu ThemeResourceKey** typu.  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 Umożliwia dostęp do kolorów w kodzie XAML i umożliwia interfejsu użytkownika na odpowiadanie na zmiany motywu.  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **Krok 5: Testowanie zmian w programie Visual Studio.**  
  
 Edytor kolor może tymczasowo dotyczą tokeny kolor uruchomionych wystąpień programu Visual Studio, aby wyświetlić zmiany na żywo do kolorów bez ponownie skompilować pakiet rozszerzenia. Aby to zrobić, kliknij przycisk "Zastosuj ten motyw do systemu windows dla programu Visual Studio" znajdujący się w nagłówku każdej kolumny motywu. To tymczasowe motywu zniknie po zamknięciu edytora kolor VSIX.  
  
 ![Zastosuj VSIX kolorem edytor](../../extensibility/internals/media/vsix-color-editor-apply.png "zastosować VSIX kolorem edytora")  
  
 Aby zmiany były trwałe, należy ponowne skompilowanie i wdrożenie rozszerzenia programu Visual Studio po dodaniu nowych kolorów do pliku .pkgdef i pisanie kodu, który będzie używać tych kolorów. Odbudowanie rozszerzenie programu Visual Studio będzie scalenie reszty motywy wartości rejestru dla nowych kolorów. Następnie uruchom ponownie program Visual Studio, interfejsu użytkownika i sprawdź, czy nowe kolorów są wyświetlane zgodnie z oczekiwaniami.  
  
## <a name="notes"></a>Uwagi  
 To narzędzie ma być użyta do tworzenia kolorów niestandardowych dla istniejących motywów programu Visual Studio lub w przypadku edycji kolory niestandardowe motywu programu Visual Studio. Aby utworzyć pełną niestandardowych kompozycji programu Visual Studio, Pobierz [rozszerzenia Visual Studio kolor motywu edytora](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b) z galerii rozszerzeń programu Visual Studio.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 **Dane wyjściowe kolor XML**  
  
 Plik XML wygenerowany przez narzędzie będzie podobny do poniższego:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **Kolor PKGDEF w danych wyjściowych**  
  
 Plik .pkgdef generowany przez narzędzie będzie podobny do poniższego:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **C# zasobów klucze otoki**  
  
 Kolor klucze zasobów wygenerowany przez narzędzie będzie podobny do poniższego:  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **Otoka słownika zasobów WPF**  
  
 Kolor **ResourceDictionary** klucze generowane przez narzędzie będzie podobny do poniższego:  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```