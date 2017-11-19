---
title: "Obraz usługi i wykaz | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5813788834a7a5a99c10fe6dafc35a300bac007
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="image-service-and-catalog"></a>Usługa obrazów i katalogu
Ta cookbook zawiera wskazówki i najlepsze rozwiązania dotyczące przyjmująca Usługa obrazów w usłudze Visual Studio i katalogu obrazu wprowadzone w programie Visual Studio 2015.  
  
 Usługa obrazów wprowadzone w programie Visual Studio 2015 umożliwia deweloperom uzyskać najlepsze obrazy dla urządzenia i wybranego motywu użytkownika do wyświetlania obrazu, w tym poprawne motywów dla kontekstu, w którym są wyświetlane. Przyjmowanie Usługa obrazów pomoże wyeliminować głównych słabe punkty dotyczące obsługi zasobów, HDPI skalowanie i motywów.  
  
|||  
|-|-|  
|**Dzisiaj problemów**|**Rozwiązania**|  
|Przenikanie kolor tła|Wbudowane przenikanie alfa|  
|Obrazy motywów (niektóre)|Metadane motywu|  
|Trybu wysoki kontrast|Alternatywne zasobów duży kontrast|  
|Wymagają wielu zasobów dla różnych trybach DPI|Wybranie zasoby z wektorowa powrotu|  
|Zduplikowana obrazów|Jeden identyfikator na koncepcji obrazu|  
  
 Dlaczego warto przyjąć Usługa obrazów?  
  
-   Zawsze uzyskać najnowsze obrazu "pikseli idealnych" z programu Visual Studio  
  
-   Można przesłać i korzystać z własnych obrazów  
  
-   Nie trzeba przetestować obrazy się po dodaje nowe Skalowanie DPI systemu Windows  
  
-   Adres starego przeszkód architektury w implementacjach użytkownika  
  
 Visual Studio shell narzędzi przed i po przy użyciu usługi obrazu:  
  
 ![Usługa obrazów przed i po](../extensibility/media/image-service-before-and-after.png "Usługa obrazów przed i po nich")  
  
## <a name="how-it-works"></a>Jak to działa  
 Usługa obrazu można podać obraz mapy bitowej odpowiednie dla dowolnej obsługiwanej architektury interfejsu użytkownika:  
  
-   WPF: element BitmapSource  
  
-   WinForms: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 Diagram przepływu usługi obrazu  
  
 ![Obraz diagramu przepływu usługi](../extensibility/media/image-service-flow-diagram.png "obrazu diagramu przepływu usługi")  
  
 **Monikery obrazu**  
  
 Moniker obrazu (lub krótkiej nazwy w skrócie) jest parę GUID/identyfikator unikatowo identyfikujący zasób obrazu lub obraz listy zasobów w bibliotece obrazów.  
  
 **Monikery znane**  
  
 Zestaw monikerów obrazów zawartych w Visual Studio obraz katalogu i publicznie niestandardowe składnika programu Visual Studio lub rozszerzenia.  
  
 **Pliki manifestu obrazu**  
  
 Pliki manifestu (.imagemanifest) obrazu są plików XML, które definiują zestaw zasobów obrazu, krótkie, reprezentujących tych zasobów i rzeczywistego obrazu lub obrazów, które reprezentują każdego zasobu. Manifesty obrazu można zdefiniować obrazy autonomicznej lub listy obrazów do obsługi starszych wersji interfejsu użytkownika. Ponadto są atrybuty, które można ustawić elementu zawartości lub na poszczególnych obrazów za każdego zasobu do zmiany czasu i sposób wyświetlania tych zasobów.  
  
 **Schematu manifestu obrazu**  
  
 Manifest pełny obraz wygląda następująco:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Symbole**  
  
 Jak zwiększyć czytelność, a obsługa pomocy, manifestu obrazu można użyć symboli dla wartości atrybutu. Symbole są zdefiniowane następująco:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Podelement**|**Definicja**|  
|Import|Importuje symbole dany plik manifestu do użycia w bieżącym manifestu|  
|Identyfikator GUID|Symbol reprezentuje identyfikator GUID i muszą być zgodne, identyfikator GUID formatowania|  
|ID|Symbol reprezentuje identyfikator i musi być nieujemną liczbą całkowitą.|  
|String|Symbol reprezentuje wartość dowolny ciąg|  
  
 Symbole jest rozróżniana wielkość liter i do którego istnieje odwołanie przy użyciu składni $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą być one używane w atrybucie Uri \<źródło > lub \<Import > elementu do ścieżek odwołania na komputerze lokalnym.  
  
|||  
|-|-|  
|**Symbol**|**Opis**|  
|CommonProgramFiles|Wartość zmiennej środowiskowej % CommonProgramFiles %|  
|LocalAppData|Wartość zmiennej środowiskowej % LocalAppData %|  
|ManifestFolder|Folder zawierający plik manifestu|  
|Moje dokumenty|Pełna ścieżka do folderu Moje dokumenty bieżącego użytkownika|  
|ProgramFiles|Wartość zmiennej środowiskowej % ProgramFiles %|  
|System|Do folderu Windows\System32|  
|WinDir|Wartość zmiennej środowiskowej % WinDir %|  
  
 **Obraz**  
  
 \<Obrazu > element definiuje obrazu, który może odwoływać się krótkiej nazwy. Identyfikator GUID i identyfikator razem tworzą krótką nazwę obrazu. Moniker obrazu musi być unikatowa w bibliotece całego obrazu. Jeśli więcej niż jeden obraz ma danego krótkiej nazwy, pierwsza z nich podczas tworzenia biblioteki jest ten, który jest przechowywany.  
  
 Musi zawierać co najmniej jedno źródło. Niezależny od rozmiaru źródeł zapewni najlepsze wyniki tożsamość w szerokiej gamie rozmiary, ale nie są wymagane. Jeśli usługa monitu dla obrazu o rozmiarze nie jest zdefiniowany w \<obrazu > element i nie istnieje źródło niezależny od rozmiaru, usługa Wybierz najlepsze źródło określonego rozmiaru i skalować ją do żądany rozmiar.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID część moniker obrazu|  
|ID|[Wymagane] Część Identyfikatora moniker obrazu|  
|AllowColorInversion|[Opcjonalne, domyślne true] Wskazuje, czy obraz mogą mieć jego kolorów programowo odwrócony, gdy jest używany w tle ciemny.|  
  
 **Źródło**  
  
 \<Źródło > element definiuje pojedynczy źródła zasób obrazu (XAML i PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Identyfikator URI|[Wymagane] Identyfikator URI, który określa, gdzie można załadować obrazu z. Może być jedną z następujących czynności:<br /><br /> -A [identyfikatora URI elementu Pack](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) przy użyciu aplikacji: / / / urzędu<br />-Odwołania zasobu składnika bezwzględne<br />Ścieżka do pliku zawierającego zasób macierzysty|  
|Tło|[Opcjonalnie] Wskazuje, co na rodzaj tła, którego źródłem jest przeznaczona do użycia.<br /><br /> Może być jedną z następujących czynności:<br /><br /> *Jasny:* źródło może być używane na jasnym.<br /><br /> *Ciemny:*źródło może być używany na ciemny tła.<br /><br /> *HighContrast:* źródła można używać na dowolnym tła w trybie dużego kontrastu.<br /><br /> *HighContrastLight:* źródło może być używane na jasnym w trybie dużego kontrastu.<br /><br /> *HighContrastDark:* źródło może być używany na ciemny tła w trybie dużego kontrastu.<br /><br /> W przypadku pominięcia atrybut tła źródło może służyć na dowolnym tła.<br /><br /> Jeśli tło jest *światła*, *ciemny*, *HighContrastLight*, lub *HighContrastDark*, nigdy nie są odwrócone kolory źródła. Jeśli tła jest pominięty, lub wartość *HighContrast*, odwracanie kolorów źródło jest kontrolowane przez obrazu **AllowColorInversion** atrybutu.|  
|||  
  
 A \<źródło > element może mieć dokładnie jeden opcjonalny następujące elementy podrzędne:  
  
||||  
|-|-|-|  
|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|  
|\<Rozmiar >|Wartość|Źródło będzie używany na potrzeby obrazów dany rozmiar (w jednostkach urządzenia). Obraz będzie kwadratowych.|  
|\<SizeRange >|MinSize, MaxSize|Źródło będzie używany dla obrazów z MinSize MaxSize (w jednostkach urządzenia) włącznie. Obraz będzie kwadratowych.|  
|\<Wymiary >|Szerokość, wysokość|Źródło będzie używany dla obrazów o danym szerokość i wysokość (w jednostkach urządzenia).|  
|\<DimensionRange >|Wartości elementu MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie służyć do obrazów z szerokość/wysokość minimalna szerokość/wysokość maksymalna (w jednostkach urządzenia) włącznie.|  
  
 A \<źródło > element może być również opcjonalne \<NativeResource > podelement, który definiuje \<źródło > który został załadowany z natywny zestaw zamiast zarządzanego zestawu.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Typ|[Wymagane] Typ zasobu natywnego XAML lub PNG|  
|ID|[Wymagane] Część Identyfikatora całkowitą zasobów natywnych|  
  
 **Listy obrazów**  
  
 \<ImageList > element definiuje kolekcją obrazów, które mogą być zwracane w jednej taśmy. Pasek jest oparty na żądanie, zgodnie z potrzebami.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID część moniker obrazu|  
|ID|[Wymagane] Część Identyfikatora moniker obrazu|  
|Zewnętrzna|[Opcjonalne, wartość domyślna to false] Wskazuje, czy moniker obrazu odwołuje się do obrazu w manifeście bieżącej.|  
  
 Moniker obrazu zawartych w niej ma odwołania zdefiniowane w manifeście bieżącego obrazu. Jeśli nie można odnaleźć obrazu zawartych w bibliotece obrazów, obraz pusty symbol zastępczy będzie używany w jego miejscu.  
  
## <a name="using-the-image-service"></a>Przy użyciu usługi obrazu  
  
### <a name="first-steps-managed"></a>Pierwsze kroki (zarządzane)  
 Do korzystania z usługi obrazu, należy dodać odwołania do niektóre lub wszystkie z następujących zestawów do projektu:  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   Wymagane w przypadku użycia wykazu wbudowanych obrazów KnownMonikers  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   Wymagane w przypadku użycia **CrispImage** i **ImageThemingUtilities** w Interfejsie użytkownika WPF  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   Wymagane w przypadku użycia **ImageMoniker** i **ImageAttributes** typów  
  
    -   **EmbedInteropTypes** powinien być ustawiony na wartość true  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   Wymagane w przypadku użycia **IVsImageService2** typu  
  
    -   **EmbedInteropTypes** powinien być ustawiony na wartość true  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   Wymagane w przypadku użycia **BrushToColorConverter** dla ImageThemingUtilities. **ImageBackgroundColor** w Interfejsie użytkownika WPF  
  
-   **Microsoft.VisualStudio.Shell. \<VSVersion >.0**  
  
    -   Wymagane w przypadku użycia **IVsUIObject** typu  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   Wymagane w przypadku użycia pomocników powiązane WinForms interfejsu użytkownika  
  
    -   **EmbedInteropTypes** powinien być ustawiony na wartość true  
  
### <a name="first-steps-native"></a>Pierwsze kroki (native)  
 Do korzystania z usługi obrazu, należy uwzględnić niektóre lub wszystkie następujące nagłówki do projektu:  
  
-   **KnownImageIds.h**  
  
    -   Wymagane w przypadku użycia wykazu wbudowanych obrazów **KnownMonikers**, ale nie można użyć **ImageMoniker** typu, na przykład gdy zwracanie wartości z **IVsHierarchy GetGuidProperty**lub **GetProperty** wywołania.  
  
-   **KnownMonikers.h**  
  
    -   Wymagane w przypadku użycia wykazu wbudowanych obrazów **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Wymagane w przypadku użycia **ImageMoniker** i **ImageAttributes** typów.  
  
-   **VSShell140.h**  
  
    -   Wymagane w przypadku użycia **IVsImageService2** typu.  
  
-   **ImageThemingUtilities.h**  
  
    -   Wymagane, jeśli to nie można zezwolić obrazu, obsługi motywów dla Ciebie.  
  
    -   Jeśli Usługa obrazów mogą obsługiwać Twoje motywów obrazu, nie używają tego nagłówka.  
  
-   **VSUIDPIHelper.h**  
  
    -   Wymagane w przypadku użycia pomocników DPI można pobrać bieżącego DPI.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>Jak napisać nowy interfejs użytkownika WPF  
  
1.  Start przez dodanie odwołania do zestawów w powyższych wymagane najpierw kroki sekcji do projektu. Nie trzeba dodać wszystkie z nich, a więc Dodaj tylko odwołania, które są potrzebne. (Uwaga: Jeśli używasz lub mieć dostęp do **kolory** zamiast **pędzle**, możesz przejść odwołanie do **narzędzia**, ponieważ konwerter nie są wymagane.)  
  
2.  Wybierz odpowiedni obraz i uzyskać jego nazwie. Użyj **KnownMoniker**, lub skorzystać z własnego, jeśli mają własne niestandardowe obrazy i monikerów.  
  
3.  Dodaj **CrispImages** do Twojej XAML. (Zobacz poniżej przykład).  
  
4.  Ustaw **ImageThemingUtilities.ImageBackgroundColor** właściwości w hierarchii interfejsu użytkownika. (Ten należy ustawić w tej lokalizacji, w którym kolor tła jest znany, nie zawsze na **CrispImage**.) (Zobacz poniżej przykład).  
  
```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  
  
 **Jak zaktualizować istniejące WPF interfejsu użytkownika?**  
  
 Aktualizowanie istniejących WPF interfejsu użytkownika jest stosunkowo prosty proces obejmuje trzy podstawowe kroki:  
  
1.  Zamień wszystkie \<obrazu > elementów w Interfejsie użytkownika z \<CrispImage > elementów  
  
2.  Zmień wszystkie atrybuty źródła do krótkiej nazwy atrybutów  
  
    -   Jeśli obraz nie ulega zmianie i za pomocą **KnownMonikers**, statycznie powiązanie tej właściwości, aby **KnownMoniker**. (Zobacz przykład powyżej).  
  
    -   Jeśli używasz niestandardowego obrazu obraz nie ulega zmianie, następnie statycznie powiązać własne krótkiej nazwy.  
  
    -   Zmiana obrazu można powiązać właściwości kodu, który powiadamia o zmianach właściwości atrybutu krótkiej nazwy.  
  
3.  Gdzieś w hierarchii interfejsu użytkownika, należy ustawić **ImageThemingUtilities.ImageBackgroundColor** aby upewnić się, że odwrócenie kolorów działa prawidłowo.  
  
    -   Może to wymagać użycia **BrushToColorConverter** klasy. (Zobacz przykład powyżej).  
  
## <a name="how-do-i-update-win32-ui"></a>Jak zaktualizować Win32 interfejsu użytkownika?  
 Dodaj następującą wartość do kodu wszędzie tam, gdzie zastąpienie raw ładowania obrazów. Przełącz wartości dla zwracania HBITMAPs i HICONs i HIMAGELIST zgodnie z potrzebami.  
  
 **Pobierz usługę obrazu**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **Żądanie obrazu**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>Jak zaktualizować WinForms interfejsu użytkownika?  
 Dodaj następującą wartość do kodu wszędzie tam, gdzie zastąpienie raw ładowania obrazów. Przełącz wartości dla zwracania mapy bitowe i ikony, zgodnie z potrzebami.  
  
 **Pomocne przy użyciu instrukcji**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Pobierz usługę obrazu**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Żądanie dotyczące obrazu**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Jak używać monikerów obrazu w nowym oknie narzędzia?  
 Szablon projektu pakietu VSIX został zaktualizowany na potrzeby programu Visual Studio 2015. Aby utworzyć nowe okno narzędzi, kliknij prawym przyciskiem myszy dla projektu VSIX i wybierz opcję "Dodaj nowy element..." (Ctrl + Shift + A). W węźle rozszerzeń dla projektów języka, wybierz "Okno Narzędzie niestandardowe" nadaj nazwę okna narzędzia, a następnie kliknij przycisk "Dodaj".  
  
 Są to miejsca klucza do użycia monikerów w oknie narzędzia. Postępuj zgodnie z instrukcjami dla każdego:  
  
1.  Karta okna narzędzia do karty małych wystarczająco (także używane w przełącznik okien klawiszy Ctrl + Tab).  
  
     Dodaj następujący wiersz do konstruktora dla klasy, która jest pochodną **obiektu ToolWindowPane** typu:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  Polecenie, aby otworzyć okno narzędzia.  
  
     W pliku vsct pakietu należy edytować przycisku polecenia oknie narzędzia:  
  
    ```xml  
    <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
      <Icon guid="ImageCatalogGuid" id="Blank" />  
      <!-- Add this -->  
      <CommandFlag>IconIsMoniker</CommandFlag>  
      <Strings>  
        <ButtonText>MyToolWindow</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
 **Jak używać monikerów obrazu w istniejących okna narzędzia?**  
  
 Aktualizowanie istniejącego okna narzędzia do użycia monikerów obrazu jest podobny do procedury służące do tworzenia nowego okna narzędzia.  
  
 Są to miejsca klucza do użycia monikerów w oknie narzędzia. Postępuj zgodnie z instrukcjami dla każdego:  
  
1.  Karta okna narzędzia do karty małych wystarczająco (także używane w przełącznik okien klawiszy Ctrl + Tab).  
  
    1.  Usuń te wiersze (jeśli istnieją) w konstruktorze klasy, która jest pochodną **obiektu ToolWindowPane** typu:  
  
        ```csharp  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  Zobacz krok #1 "Jak monikerów obraz używany w nowym oknie narzędzia?" powyższej sekcji.  
  
2.  Polecenie, aby otworzyć okno narzędzia.  
  
    -   Zobacz krok #2 "Jak monikerów obraz używany w nowym oknie narzędzia?" powyższej sekcji.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Jak używać monikerów obraz w pliku vsct?  
 Zaktualizuj plik vsct opisane w poniższych wierszach komentarze:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we're using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  
  
 **Co zrobić, jeśli plik vsct musi również zostać odczytany przez starsze wersje programu Visual Studio?**  
  
 Starsze wersje programu Visual Studio nie rozpoznają **IconIsMoniker** polecenia flagi. Obrazy z obrazu usługi można użyć w wersjach programu Visual Studio, które obsługuje, ale nadal używać obrazów w starym stylu w starszych wersjach programu Visual Studio. Aby to zrobić, czy opuszczeniu pliku vsct bez zmian (i w związku z tym zgodne ze starszymi wersjami programu Visual Studio) i Utwórz plik CSV (wartości rozdzielane przecinkami), który mapuje z pary GUID/identyfikator zdefiniowane w pliku vsct \<map bitowych > element do obrazu pary GUID/identyfikator krótkiej nazwy.  
  
 Format pliku CSV mapowania jest:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 Plik CSV jest wdrażany z pakietu i jego lokalizacji jest określona przez **IconMappingFilename** właściwość **ProvideMenuResource** atrybut pakietu:  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 **IconMappingFilename** jest względną ścieżką niejawnie początek w $PackageFolder$ (tak jak w powyższym przykładzie), lub ścieżką bezwzględną jawnie umieszczone w katalogu zdefiniowany przez zmienną środowiskową, takich jak @"%UserProfile%\ dir1\dir2\MyMappingFile.csv".  
  
## <a name="how-do-i-port-a-project-system"></a>Jak port system projektu?  
 **Jak podać ImageMonikers dla projektu**  
  
1.  Implementowanie **VSHPROPID_SupportsIconMonikers** do projektu **IVsHierarchy**i zwraca wartość true.  
  
2.  Implementowanie albo **VSHPROPID_IconMonikerImageList** (Jeśli oryginalny projekt **VSHPROPID_IconImgList**) lub **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (Jeśli oryginalny projekt  **VSHPROPID_IconHandle** i **VSHPROPID_OpenFolderIconHandle**).  
  
3.  Zmień implementację oryginalnego VSHPROPIDs dla ikony na tworzenie wersji "starszych" ikony, jeśli punkty rozszerzenia ich zażądać. **IVsImageService2** udostępnia funkcje niezbędne do pobrania tych ikon  
  
 **Dodatkowe wymagania dotyczące VB / odmian projektu C#**  
  
 Tylko zaimplementować **VSHPROPID_SupportsIconMonikers** jeśli wykryje, że Twój projekt jest **peryferyjnych podtyp**. W przeciwnym razie wartość rzeczywista podtyp peryferyjnych może nie obsługiwać monikerów obrazu w rzeczywistości, a sieci podstawowej wersji może efektywnie "ukryć" dostosowanych obrazów.  
  
 **Jak używać monikerów obrazu w systemie CPS?**  
  
 Ustawianie niestandardowych obrazów w systemie CPS (Common Project System) można ręcznie lub za pomocą szablonu elementu, który jest dostarczany z zestawem SDK rozszerzeń systemu projektu.  
  
 **Przy użyciu rozszerzeń systemu projekt zestawu SDK**  
  
 Postępuj zgodnie z instrukcjami w [Podaj ikon niestandardowych dla typu elementu typu projektu](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) dostosować obrazy CPS. Więcej informacji na temat CPS można znaleźć w folderze [dokumentacja rozszerzalności systemu projektu programu Visual Studio](https://github.com/Microsoft/VSProjectSystem)  
  
 **Użyj ręcznie ImageMonikers**  
  
1.  Implementowanie i eksportowanie **IProjectTreeModifier** interfejsu w systemie projektu.  
  
2.  Określenie, które **KnownMoniker** lub krótkiej nazwy niestandardowego obrazu, którego chcesz użyć.  
  
3.  W **ApplyModifications** metody, wykonaj następujące czynności metoda przed zwróceniem nowe drzewo, podobnie jak w poniższym przykładzie:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  W przypadku tworzenia nowego drzewa, można ustawić niestandardowych obrazów przez przekazywanie żądaną monikerów NewTree do metody, podobnie jak poniższym przykładzie:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Jak konwertować z paska rzeczywistego obrazu do paska obrazu krótkiej nazwy?  
 **Potrzebne do obsługi HIMAGELISTs**  
  
 Jeśli istnieje już istniejącą paska obrazu dla swój kod, który ma zostać zaktualizowany do korzystania z usługi obrazu, ale są ograniczone przez interfejsy API, które wymagają przekazywanie wokół listy obrazów, można korzystać z zalet usługi obrazu. Aby utworzyć paska obrazu krótkiej nazwy, wykonaj poniższe kroki, aby utworzyć manifestu na podstawie istniejących monikerów.  
  
1.  Uruchom **ManifestFromResources** narzędzie przekazanie jej paska obrazu. Spowoduje to wygenerowanie manifestu paska.  
  
    -   Zalecane: Podaj nazwę z systemem innym niż domyślny dla manifest, aby odpowiadały jej użycia.  
  
2.  Jeśli używane są tylko **KnownMonikers**, następnie wykonaj następujące czynności:  
  
    -   Zastąp \<obrazów > sekcji manifestu z \<obrazów / >.  
  
    -   Usuń wszystkie subimage identyfikatorów (cokolwiek z \<imagestrip name > _ ##).  
  
    -   Zalecane: Zmień nazwę symbolu AssetsGuid i symbol paska obrazu do własnych jego użycia.  
  
    -   Zastąp każdego **ContainedImage**w identyfikatora GUID $(ImageCatalogGuid), Zastąp każdego **ContainedImage**w identyfikatorze o $(\<krótkiej nazwy >) i dodać atrybut zewnętrznych = "true" do każdego **ContainedImage**  
  
        -   \<Moniker > powinien zostać zamieniony **KnownMoniker** odpowiadającego obrazu, ale "KnownMonikers." usunięte z nazwy.  
  
    -   Dodaj < Import Manifest="$(ManifestFolder)\\< względem zainstalować ścieżkę katalogu do\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> na początku \<symbole > sekcji.  
  
        -   Ścieżka względna jest określana przez zdefiniowano w ustawieniach autorstwa dla manifest lokalizacji wdrożenia.  
  
3.  Uruchom **ManifestToCode** narzędzie do generowania otoki tak, aby istniejący kod moniker, można użyć do zapytania usługi obrazu dla paska obrazu.  
  
    -   Zalecane: Podaj niestandardowe nazwy otoki i przestrzenie nazw zgodnie z własnymi ich użycia.  
  
4.  Wykonaj wszystkie dodaje, tworzenia instalacji/wdrażania i inne zmiany kodu do pracy z usługą obrazu i nowych plików.  
  
 Manifest próbki wewnętrznych i zewnętrznych obrazy, aby zobaczyć, jak jego powinien wyglądać w tym:  
  
```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  
  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  
  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  
  
  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  
  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  
  
</ImageManifest>  
```  
  
 **I nie musisz zapewniać obsługi HIMAGELISTs**  
  
1.  Określa zestaw **KnownMonikers** odpowiada obrazów w Twojej paska obrazu lub utworzyć własne monikerów obrazów w Twojej paska obrazu.  
  
2.  Niezależnie od mapowania używany do pobrania obrazu pod indeksem wymagane paska obrazu zamiast tego użyć monikerów aktualizacji.  
  
3.  Zaktualizuj kod w celu żądania monikerów za pomocą mapowania zaktualizowane przy użyciu usługi obrazu. (Może to oznaczać, aktualizacja do **CrispImages** dla zarządzanego kodu, lub żądania HBITMAPs lub HICONs z usługi obrazu i przekazywanie ich wokół dla kodu natywnego.)  
  
## <a name="testing-your-images"></a>Testowanie obrazów  
 Narzędzie Image Viewer biblioteki do testowania z manifestów obrazu, aby upewnić się, że wszystko jest poprawnie przypisany. Możesz znaleźć tego narzędzia w [programu Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx). Można znaleźć w dokumentacji to narzędzie i innych [tutaj](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
  
### <a name="samples"></a>Przykłady  
 Kilka przykładów programu Visual Studio w witrynie GitHub zostały zaktualizowane w usłudze pokazują, jak korzystać z usługi obrazu w ramach różnych punktów rozszerzalności programu Visual Studio.  
  
 Sprawdź [http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples) dla najnowszej próbki.  
  
### <a name="tooling"></a>Narzędzia  
 Zestaw narzędzi pomocy technicznej dla usługi obraz został utworzony ułatwiających tworzenie/Aktualizowanie interfejsu użytkownika, który współpracuje z usługą obrazu. Aby uzyskać więcej informacji o poszczególnych narzędzi dokumentacji dołączoną narzędzi. Narzędzia są dołączane jako część [Visual Studio 2015 SDK.](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 Manifest z zasobów narzędzia przyjmuje listę zasoby obrazów (PNG lub XAML) i generuje plik manifestu obrazu korzystania z usługi obrazu przy użyciu tych obrazów.  
  
 **ManifestToCode**  
  
 Manifest, aby narzędzie kodu pobiera plik manifestu obrazu i generuje plik otoki dla odwołania do wartości manifestu kodu (C++, C# i VB) lub vsct plików.  
  
 **ImageLibraryViewer**  
  
 Narzędzia Podgląd obrazu biblioteki można załadować obrazu manifestów i umożliwia użytkownikowi do manipulowania je w taki sam sposób, Visual Studio, czy upewnij się, że plik manifestu jest poprawnie przypisany. Użytkownik może zmienić tła, rozmiary, ustawienie DPI, duży kontrast i inne ustawienia. Również wyświetlane informacje ładowania, aby znaleźć błędy w manifestach i wyświetla informacje o źródle dla każdego obrazu w manifeście.  
  
## <a name="faq"></a>Najczęściej zadawane pytania  
  
-   Czy istnieją wszelkie zależności, które należy uwzględnić podczas ładowania \<Include="Microsoft.VisualStudio.* odwołania. Interop.14.0.DesignTime"/ >?  
  
    -   Ustaw EmbedInteropTypes = "true" na wszystkie biblioteki DLL międzyoperacyjnego.  
  
-   Jak wdrożyć manifestu obrazu z Moje rozszerzenie?  
  
    -   Dodaj plik .imagemanifest do projektu.  
  
    -   "Dołącz w pliku VSIX" należy ustawić na wartość True.  
  
-   Jestem I aktualizowanie systemu CPS projektu. Co się stało z **Nazwa_obrazu** i **StockIconService**?  
  
    -   o te zostały usunięte podczas CPS zostało zaktualizowane do używania monikerów. Nie trzeba wywołać **StockIconService**, po prostu Przekaż żądaną **KnownMoniker** do metody lub używając właściwości **ToProjectSystemType()** — metoda rozszerzenia w narzędzia CPS. Można znaleźć mapowanie **Nazwa_obrazu** do **KnownMonikers** poniżej:  
  
        |||  
        |-|-|  
        |**Nazwa_obrazu**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   Jestem I aktualizowanie świadczącej listy uzupełniania. Co **KnownMonikers** pasuje do starego **StandardGlyphGroup** i **StandardGlyph** wartości?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||Tematy pomocy|  
        |GlyphLibrary||Biblioteka|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||Okno dialogowe|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||Przejdź do następnego|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||fragment kodu|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Rekursja|  
        |GlyphXmlItem||Tag|  
        |GlyphJSharpProject||Elementu DocumentCollection|  
        |GlyphJSharpDocument||dokument|  
        |GlyphForwardType||Przejdź do następnego|  
        |GlyphCallersGraph||Użyciu CallTo|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||Użyciu CallTo|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||Element XmlAttribute|  
        |GlyphXmlChild||Element XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|