---
title: Adresowanie Problemy2 DPI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc0801d3fb43188ac3371ed7e5e7394b0e3aad72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="addressing-dpi-issues"></a>Rozwiązywania problemów DPI
Zwiększa liczbę urządzeń jest dostarczany z ekranami "o wysokiej rozdzielczości". Te ekrany zwykle mają ponad 200 pikseli na cal (ppi). Korzystanie z aplikacji na tych komputerach będzie wymagać zawartości do skalowanie do potrzeb wyświetlania zawartości w odległości normalnego widoku dla urządzenia. Począwszy od 2014 r. miejsce docelowe głównej wyświetlacze o wysokiej gęstości pracuje w terenie, urządzenia (tablety, laptopy clamshell i telefony).  
  
 Windows 8.1 lub nowszy zawiera kilka funkcji, aby włączyć tych urządzeń do pracy z Wyświetla i środowisk, w którym komputer jest dołączony do obu o wysokiej gęstości i gęstości standard wyświetla w tym samym czasie.  
  
-   Systemu Windows można zezwolić na Skaluj zawartość do urządzenia za pomocą "Przechowuj tekst i inne elementy większy lub mniejszy" ustawienie (dostępne od systemu Windows XP).  
  
-   Windows 8.1 lub nowszy jest automatycznie skalowany zawartości dla większości aplikacji były spójne, po przeniesieniu między wyświetla różne gęstości pikseli. Gdy ekran główny jest o wysokiej gęstości (skalowanie 200%) i gęstości standardowe (100%) są wyświetlane dodatkowej, systemu Windows jest automatycznie skalowany zawartość okna aplikacji w dół na ekranie dodatkowej (1 piksela wyświetlany dla każdej 4 pikseli renderowana przez Aplikacja).  
  
-   System Windows jest domyślnie po prawej stronie skalowania gęstości pikseli i wyświetlanie odległość wyświetlania (z systemem Windows 7 lub nowszej, można skonfigurować OEM).  
  
-   System Windows może automatycznie skalować zawartości w górę do 250% w nowych urządzeniach, które przekraczają 280 ppi (lub nowszym S14 Windows 8.1).  
  
 System Windows ma sposób postępowania z skalowaniu interfejsu użytkownika przeprowadzać pikseli zwiększenie liczby. Aplikacja zdecyduje w z tym systemem przez zadeklarowanie sam "system pamiętać DPI." Aplikacje, które nie należy tego robić są skalowane w górę przez system. Może to spowodować "rozmytego" użytkowników, gdzie całej aplikacji jest jednolicie rozciągnięty pikseli. Na przykład:  
  
 ![Rozmytego wydaje DPI](../extensibility/media/dpi-issues-fuzzy.png "rozmytego wydaje DPI")  
  
 Visual Studio zażąda w ich trwa skalowanie obsługujący DPI i w związku z tym jest nie "zwirtualizowanych."  
  
 Systemu Windows (i Visual Studio) korzystać z kilku technologii interfejsu użytkownika, które mają różne sposoby postępowania w przypadku skalowania czynniki ustawiony przez system. Na przykład:  
  
-   WPF środków kontroli w sposób niezależny od urządzenia (jednostek, nie pikseli). WPF interfejsu użytkownika jest automatycznie skalowany dla bieżącego DPI.  
  
-   Wszystkich rozmiarów tekstu niezależnie od tego, w ramach interfejsu użytkownika są wyrażane w punktach, a więc są traktowane przez system jako niezależny od rozdzielczości. Tekst w Win32, WinForms oraz WPF już skalowanie w górę poprawnie narysować do urządzenia.  
  
-   Win32/WinForms okien dialogowych i systemu windows mają na włączenie układu, który zmienia rozmiar tekstem — na przykład za pomocą siatki, przepływu i panele układu tabeli. Włącz te, unikając lokalizacje ustalony pikseli, które nie są skalowane, gdy są zwiększyć rozmiary czcionek.  
  
-   Ikony dostarczane przez system lub zasobów w oparciu metryki systemu (na przykład SM_CXICON i SM_CXSMICON) są już skalowanie.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Starsze Win32 (GDI, GDI +) i na podstawie WinForms interfejsu użytkownika  
 WPF już jest wysoka obsługującą ustawienia DPI, większość naszego kodu systemu Win32/GDI nie został pierwotnie zapisany z funkcją rozpoznawanie DPI pamiętać. Windows udostępnił Skalowanie DPI interfejsów API. Rozwiązania problemów Win32 należy używać tych spójne w ramach produktu. Visual Studio udostępnił pomocnika biblioteki klas, aby uniknąć duplikowania funkcjonalność i zapewnienie spójności w ramach produktu.  
  
## <a name="high-resolution-images"></a>Obrazy o wysokiej rozdzielczości  
 W tej sekcji służy głównie do deweloperów rozszerzania programu Visual Studio 2013. Dla programu Visual Studio 2015 za pomocą usługi obrazu, wbudowane w program Visual Studio. Można również znaleźć potrzebne do obsługi/docelowego wiele wersji programu Visual Studio, a w związku z tym korzystanie z usługi obrazu w 2015 nie ma możliwości użycia, ponieważ nie istnieje w poprzednich wersjach. Ta sekcja dotyczy również należy następnie.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Skalowanie do obrazów, które są zbyt małe  
 Obrazy, które są zbyt małe można "skalowanie" i renderowane w GDI i WPF przy użyciu niektóre typowe metody. Klasy zarządzane pomocnika DPI są dostępne dla wewnętrznych i zewnętrznych integratory Visual Studio do skalowania ikony, mapy bitowe, imagestrips i imagelists adresu. C natywnego na podstawie Win32 / dostępni są pomocnicy C ++ do skalowania HICON, HBITMAP HIMAGELIST i VsUI::GdiplusImage. Tylko skalowanie mapy bitowej zwykle konieczna jest zmiana jednego wiersza po dołączeniu odwołanie do biblioteki pomocnika. Na przykład:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Skalowanie imagelist zależy od elementu imagelist zakończeniu w czasie ładowania, czy jest dołączone w czasie wykonywania. Jeśli zakończone w czasie ładowania, jak w przypadku mapy bitowej wywołać LogicalToDeviceUnits() z elementu imagelist. Gdy kod musi załadować poszczególnych mapy bitowej przed redagowania element imagelist, upewnij się, że rozmiar obrazu elementu imagelist skalowania:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 W kodzie natywnym wymiary mogą być skalowane, tworząc element imagelist w następujący sposób:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funkcje biblioteki pozwala na stosowanie algorytmu zmiany rozmiaru. Jeśli skalowania obrazów do umieszczenia w imagelists, upewnij się określić kolor tła używany przezroczystości lub użyj NearestNeighbor skalowania (co spowoduje zakłócenia w 125% i 150%).  
  
 Zapoznaj się <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> dokumentacji w witrynie MSDN.  
  
 W poniższej tabeli przedstawiono przykłady jak obrazy powinien być skalowany w odpowiedniej rozdzielczości DPI czynnik skalowania. Obrazy na zielono oznaczenia naszych najlepszych praktyk, począwszy od programu Visual Studio 2013 (100 do 200% Skalowanie DPI):  
  
 ![Problemy DPI skalowanie](../extensibility/media/dpi-issues-scaling.png "problemów DPI skalowania")  
  
## <a name="layout-issues"></a>Problemy z rozmieszczeniem  
 Przede wszystkim utrzymując punktów w Interfejsie użytkownika skalowana względem siebie, a nie za pomocą ukośnik (w szczególności w jednostkach pikseli) można uniknąć typowych problemów z układu. Na przykład:  
  
-   Układ i tekstu pozycji potrzeba do konta w celu skalowania w górę obrazów.  
  
-   Kolumn w siatkach musi być dostosowana do tekstu skalowanych szerokości.  
  
-   Ustalony rozmiar lub odstęp między elementami trzeba także skalowanie. Rozmiary oparte tylko na tekst wymiary są zwykle małe, ponieważ czcionki automatycznie są skalowane w górę.  
  
 Funkcje pomocnicze są dostępne w <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> klasy, aby umożliwić skalowanie na osi X i Y:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (Zezwalaj na funkcje skalowania w X / osi Y)  
  
-   miejsce int = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   wysokość int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Istnieją przeciążenia LogicalToDeviceUnits umożliwia skalowanie obiekty, takie jak Rect, pkt i rozmiar czcionki.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Za pomocą biblioteki DPIHelper/klasy skalowanie obrazów i układ  
 Biblioteka pomocnika Visual Studio DPI jest dostępny w formularzach natywnych i zarządzanych i mogą być używane poza powłoki programu Visual Studio przez inne aplikacje.  
  
 Korzystanie z biblioteki, przejdź do [przykłady rozszerzania VSSDK programu Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples) i klonowanie próbki wysokiej DPI_Images_Icons  
  
 W plikach źródłowych obejmują VsUIDpiHelper.h i wywoływać funkcje statyczne klasy VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Nie należy używać funkcji pomocnika w module poziomie klasy lub zmienne statyczne. Biblioteka również używa statyczne dla wątku synchronizacji i możesz napotkać problemy kolejności inicjowania. Przekonwertuj tych danych ze zmiennymi Członkowskimi Niestatyczne lub zawijać je do funkcji (Aby uzyskać one skonstruowany na pierwszym dostępie).  
  
 Dostęp do funkcji pomocnika DPI z kodu zarządzanego, który będzie uruchamiany w środowisku Visual Studio:  
  
-   Odbierającą projektu musi odwoływać się najnowszą wersję MPF powłoki. Na przykład:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Upewnij się, projekt zawiera odwołania do **System.Windows.Forms**, **PresentationCore**, i **PresentationUI**.  
  
-   W kodzie, użyj **Microsoft.VisualStudio.PlatformUI** przestrzeni nazw i wywołanie statyczne funkcje klasy DpiHelper. Dla obsługiwanych typów (punkty, rozmiary prostokąty i tak dalej) są dostarczane funkcje rozszerzenia, które zwracają nowe skalowania obiektów. Na przykład:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Zajmujących się WPF rozmycia obrazu, w którą można powiększać interfejsu użytkownika  
 Na platformie WPF mapy bitowe zmieniany jest rozmiar automatycznie przez WPF dla bieżący poziom powiększenia DPI przy użyciu algorytmu dwusześcienna wysokiej jakości (ustawienie domyślne), które działa dobrze dla obrazów lub duże zrzuty ekranu, ale jest nieodpowiedni dla ikony elementów menu, ponieważ wprowadza ona postrzegana rozmycia .  
  
 Zalecenia:  
  
-   Logo obrazu i transparentach kompozycji, domyślnie <xref:System.Windows.Media.BitmapScalingMode> zmiany rozmiaru w trybie może zostać użyty.  
  
-   Elementy menu i obrazy nadruków <xref:System.Windows.Media.BitmapScalingMode> powinien być używany, gdy nie powoduje pozostałych artefaktów zakłócenia wyeliminować rozmycia (w 200%, 300%).  
  
-   Dla dużych powiększenia poziomy nie wielokrotności 100% (na przykład 250% lub 350%), skalowanie obrazów nadruków z dwusześcienna powoduje rozmytego, rozmycia interfejsu użytkownika. Lepszą jakość są uzyskiwane przez pierwszy skalowanie obrazu o NearestNeighbor największy wielokrotności 100% (na przykład 200% lub 300%) i skalowanie przy dwusześcienna stamtąd. Zobacz szczególnych przypadkach: prescaling WPF obrazy dla dużych DPI poziomy, aby uzyskać więcej informacji.  
  
 Klasa DpiHelper w przestrzeni nazw Microsoft.VisualStudio.PlatformUI udostępnia element członkowski <xref:System.Windows.Media.BitmapScalingMode> które mogą być używane dla wiązania. Umożliwia powłoki programu Visual Studio kontrolować skalowanie tryb między produktu jednolicie, w zależności od czynnik skalowania DPI mapy bitowej.  
  
 Aby użyć go w języku XAML, należy dodać:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio shell już ustawia tę właściwość na najwyższego poziomu systemu windows i oknach dialogowych. Na architekturach WPF interfejsu użytkownika uruchomiony w programie Visual Studio będzie już dziedziczyć go. Jeśli ustawienia nie są propagowane do figur konkretnego interfejsu użytkownika, można ustawić dla elementu głównego XAML/WPF interfejsu użytkownika. Miejsca, w którym dzieje się to obejmują wyskakujące okienka w przypadku elementów z elementów nadrzędnych Win32, oraz projektanta systemu windows, które są uruchamiane z przetwarzać, takich jak program Blend.  
  
 Niektóre interfejsu użytkownika można skalować niezależnie od poziomu powiększenia DPI zestaw systemu, takich jak edytor tekstu Visual Studio i projektantów WPF (WPF Desktop i Sklepu Windows). W takich przypadkach DpiHelper.BitmapScalingMode nie można używać. Aby rozwiązać ten problem w edytorze, zespołu IDE utworzona właściwość niestandardową nazwę RenderOptions.BitmapScalingMode. Ustaw tę wartość właściwości HighQuality lub NearestNeighbor w zależności od poziomu powiększenia Scalonej systemu i Interfejsie użytkownika.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Specjalny przypadek: prescaling obrazów WPF dużych poziomów DPI  
 Poziom powiększenia bardzo dużych niebędące wielokrotności 100% (na przykład 250%, 350% i tak dalej) skalowanie obrazów nadruków dwusześcienna wyniki w interfejsie użytkownika rozmytego, rozmycia. Wrażenie tych obrazów obok wyraźny tekst jest prawie przykład iluzji optyczne. Obrazy wydaje się być bliżej oka i poza fokusu w odniesieniu do tekstu. Wynik skalowania w tym rozmiarze powiększony można zwiększyć przez pierwszy skalowanie obrazu o NearestNeighbor największy wielokrotności 100% (na przykład 200% lub 300%) i skalowanie przy dwusześcienna z pozostałą (dodatkowe 50%).  
  
 Poniżej przedstawiono przykład różnice w wynikach, gdzie skalowania pierwszy obraz z ulepszonych algorytmu skalowania o podwójnej precyzji-100% > -> 250% 200%, a drugi tylko z dwusześcienna 100% -> 250%.  
  
 ![Podwójne przykład skalowania wydaje DPI](../extensibility/media/dpi-issues-double-scaling-example.png "podwójne przykład skalowania wydaje DPI")  
  
 Aby włączyć interfejsu użytkownika, aby użyć tego skalowanie o podwójnej precyzji, znaczników XAML do wyświetlania każdego elementu obrazu należy do zmodyfikowania. W poniższych przykładach pokazano sposób użycia o podwójnej precyzji skalowanie na platformie WPF w programie Visual Studio przy użyciu biblioteki DpiHelper i Shell.12/14.  
  
 Krok 1: Prescale obrazu % 200, 300% i tak dalej, przy użyciu NearestNeighbor.  
  
 Prescale obraz za pomocą konwertera stosowane w powiązaniu lub z rozszerzeniem znacznika XAML. Na przykład:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Jeśli obraz musi być również motywów (większość, jeśli nie, należy), znaczników można użyć różnych konwerter, która najpierw motywów obrazu, a następnie wstępnie skalowania. Znaczników można użyć dowolnego <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> lub <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, zależnie od żądanego konwersji danych wyjściowych.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Krok 2: Upewnij się, że rozmiaru końcowego jest poprawna dla bieżącego DPI.  
  
 Ponieważ WPF skalowały interfejsu użytkownika dla bieżącej rozdzielczości, przy użyciu właściwości BitmapScalingMode ustawiać UIElement, formantu obrazu przy użyciu obrazu prescaled jako źródła będzie wyglądać dwie lub trzy razy większy niż powinien. Poniżej przedstawiono kilka sposobów licznika w tym celu:  
  
-   Jeśli znasz wymiar oryginalnego obrazu w skali 100%, można określić dokładny rozmiar formantu obrazu. Rozmiary będzie odzwierciedlać rozmiar interfejsu użytkownika przed skalowanie jest stosowany.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Jeśli rozmiar oryginalnego obrazu nie jest znany, można LayoutTransform skali końcowego obiektu obrazu. Na przykład:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Włączanie obsługi HDPI do obiektu  
 Domyślnie przez formanty obiektu (na przykład formantu WebBrowser w WPF lub interfejs IWebBrowser2) nie włączaj HDPI wykrywania i obsługi technicznej. Wynik będzie osadzonego formantu z zawartością wyświetlania, która jest za mały na o wysokiej rozdzielczości. Poniżej opisano sposób włączania obsługi wysokiej rozdzielczości w wystąpieniu obiektu określonego w sieci web.  
  
 Zaimplementuj interfejs IDocHostUIHandler (zobacz artykuł w witrynie MSDN na [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interfejsu):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Opcjonalnie można implementować interfejs ICustomDoc (zobacz artykuł w witrynie MSDN na [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interfejsu):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Kojarzenie klasy, która implementuje IDocHostUIHandler obiektu dokumentu. Jeśli zaimplementowano interfejs ICustomDoc powyżej, następnie jak właściwość dokumentu obiektu jest prawidłowa, rzutować go na ICustomDoc i wywołaj metodę SetUIHandler, przekazywanie klasy, która implementuje IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Jeśli użytkownik nie wdrożyła interfejsu ICustomDoc, następnie jak właściwość dokumentu obiektu jest prawidłowa, należy rzutować go do obiektu IOleObject, a następnie wywołaj metodę SetClientSite, przekazując klasy, która implementuje IDocHostUIHandler. Ustaw flagę DOCHOSTUIFLAG_DPI_AWARE na DOCHOSTUIINFO przekazany do wywołania metody GetHostInfo:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Powinno to być wszystkie punkty, które należy uzyskać formantu obiektu do obsługi HPDI.  
  
## <a name="tips"></a>Porady  
  
1.  W przypadku zmiany właściwości dokumentu w kontrolce obiektu, konieczne może być ponownie skojarzyć go z klasy IDocHostUIHandler.  
  
2.  Jeśli powyższe czynności zakończą się niepowodzeniem, jest to znany problem z obiektu nie przechwycenie zmiany flagi DPI. Najbardziej niezawodnym sposobem ustalenia to jest Przełącz optyczne powiększenia obiektu, znaczenie dwóch wywołania z dwóch różnych wartości powiększenia. Ponadto jeśli wymagana jest to rozwiązanie, może być konieczne przeprowadzenie przy każdym wywołaniu Nawigacja.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```