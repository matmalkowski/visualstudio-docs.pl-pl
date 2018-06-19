---
title: Tworzenie ozdób widoku, poleceń i ustawienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 57a7696eae0da92d88babf64c580a4767775dffd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148197"
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Wskazówki: Tworzenie ozdób widoku, poleceń i ustawień (prowadnice kolumn)
Można rozszerzyć Edytor tekstu/kodu programu Visual Studio z poleceniami i efekty widoku.  W tym temacie opisano Rozpoczynanie pracy z funkcją popularnych rozszerzenia prowadnice kolumn.  Przewodniki kolumny są wizualnie światła linii w widoku edytora tekstu w celu zarządzania kodu do określonej szerokości.  W szczególności sformatowany kod może być ważne dla przykładów dokumentów, wpisy na blogu lub usterek raportów.  
  
 W tym przewodniku obejmują:  
  
-   Tworzenie projektu VSIX  
  
-   Dodawanie ozdób widoku edytora  
  
-   Dodaj obsługę zapisywania i pobierania ustawień (w przypadku gdy w celu rysowania prowadnice kolumn i ich kolor)  
  
-   Dodawanie poleceń (Dodawanie/usuwanie kolumn, zmienić kolor)  
  
-   Umieścić polecenia w menu Edycja i menu kontekstowe dokumentu tekstu  
  
-   Dodaj obsługę wywoływania poleceń w oknie polecenia programu Visual Studio  
  
 Wersja funkcji przewodniki kolumny z tej galerii programu Visual Studio można wypróbować[rozszerzenia](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Uwaga**: w tym przewodniku wklejania dużej ilości kodu w kilka plików generowanych przez Szablony rozszerzenia programu visual studio, ale wkrótce w tym przewodniku będzie dotyczyć gotowego rozwiązania w serwisie github z innymi przykładami rozszerzenia.  Kompletny kod różni się nieznacznie, w tym ma ikony poleceń rzeczywistych zamiast generictemplate ikon.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Trwa konfigurowanie rozwiązania  
 Najpierw zostanie tworzenia projektu VSIX, Dodaj ozdób widoku edytora, a następnie dodaj polecenie (który dodaje pakiet VSPackage własności polecenie).  Podstawowa architektura wygląda następująco:  
  
-   Masz odbiornik tworzenia widoku tekstu, który tworzy `ColumnGuideAdornment` obiektu na widok.  Ten obiekt nasłuchuje zdarzenia związane ze zmianą widoku lub zmianę ustawienia, aktualizowania lub ponownego narysowania kolumny prowadzi zgodnie z potrzebami.  
  
-   Brak `GuidesSettingsManager` obsługująca odczytywanie i zapisywanie z magazynu ustawienia programu Visual Studio.  Menedżer ustawień są również operacje aktualizowania ustawień, które obsługują polecenia użytkownika (Dodaj kolumnę, usunąć kolumnę, zmienić kolor).  
  
-   Brak pakietu VSIP, które są niezbędne, jeśli masz poleceń użytkownika, ale jest po prostu schematyczny kod, który inicjuje obiekt wykonania polecenia.  
  
-   Brak `ColumnGuideCommands` obiekt, który implementuje poleceń użytkownika i przechwytuje się programy obsługi poleceń dla polecenia zadeklarowany w pliku vsct.  
  
 **VSIX**.  Użyj **pliku &#124; nowych...**  polecenie, aby utworzyć projekt.  Wybierz węzeł rozszerzalności w języku C# w lewym okienku nawigacji, a następnie wybierz pozycję **projektu VSIX** w okienku po prawej stronie.  Wprowadź nazwę ColumnGuides i wybierz polecenie **OK** Aby utworzyć projekt.  
  
 **Wyświetl ozdób**.  Naciśnij przycisk prawo wskaźnika na węzeł projektu w Eksploratorze rozwiązań.  Wybierz **dodać &#124; nowy element...**  polecenie, aby dodać nowy element ozdób widoku.  Wybierz **rozszerzalności &#124; edytor** w okienku nawigacji po lewej stronie i wybierz polecenie **ozdób okienka ekranu edytor** w okienku po prawej stronie.  Wprowadź nazwę ColumnGuideAdornment jako nazwa elementu, a następnie wybierz pozycję **Dodaj** ją dodać.  
  
 Spowoduje to szablon elementu dodanie dwóch plików do projektu (a także odwołań i tak dalej): ColumnGuideAdornment.cs i ColumnGuideAdornmentTextViewCreationListener.cs.  Szablony tylko Rysuj prostokąt purpurowy w widoku.  Poniżej będzie zmienić kilka wierszy w widoku tworzenie odbiornika i Zastąp zawartość ColumnGuideAdornment.cs.  
  
 **Polecenia**.  Naciśnij przycisk prawo wskaźnika na węzeł projektu w Eksploratorze rozwiązań.  Wybierz **dodać &#124; nowy element...**  polecenie, aby dodać nowy element ozdób widoku.  Wybierz **rozszerzalności &#124; pakiet VSPackage** w okienku nawigacji po lewej stronie i wybierz polecenie **polecenia niestandardowych** w okienku po prawej stronie.  Wprowadź nazwę ColumnGuideCommands jako nazwa elementu, a następnie wybierz pozycję **Dodaj** ją dodać.  Oprócz kilka odwołań polecenia i pakietu dodać ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs i ColumnGuideCommandsPackage.vsct.  Poniżej spowoduje zastąpienie zawartości imię i nazwisko plików do definiowania i wykonania polecenia.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Konfigurowanie odbiornika tworzenia widoku tekstu  
 Otwórz ColumnGuideAdornmentTextViewCreationListener.cs w edytorze.  Ten kod implementuje obsługi dla zawsze, gdy program Visual Studio tworzy widoki tekstu.  Brak atrybutów, które kontrolują, gdy program obsługi jest wywoływana w zależności od właściwości widoku.  
  
 Kod musi również deklarować warstwy ozdób.  Gdy Edytor aktualizuje widoków, pobiera warstwy ozdób widoku i niż pobiera elementy ozdób.  Można zadeklarować kolejność warstwą względem innych atrybutów.  Zastąp następujący wiersz:  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 z tych dwóch wierszy:  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 Wiersz, który zostanie zastąpiony znajduje się w grupie atrybutów, które deklaruje warstwy ozdób.   Pierwszy wiersz zmienić jedynie zmian wprowadzonych w którym są wyświetlane linie przewodnik kolumn.  Rysowanie linii "przed" tekst w widoku oznacza, że pojawią się one poniżej tekst lub za.  Drugi wiersz deklaruje skojarzenia przewodnik kolumny mają zastosowanie do jednostek tekstu, spełniających Twoje pojęcie dokumentu, że można zadeklarować ozdób, na przykład tylko pracy do edycji.  Więcej informacji można znaleźć w [usługi języka oraz punktów rozszerzenia Edytora](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Implementowanie Menedżer ustawień  
 Zastąp zawartość GuidesSettingsManager.cs następujący kod (co omówiono poniżej):  
  
```csharp  
using Microsoft.VisualStudio.Settings;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Settings;  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows.Media;  
  
namespace ColumnGuides  
{  
    internal static class GuidesSettingsManager  
    {  
        // Because my code is always called from the UI thred, this succeeds.  
        internal static SettingsManager VsManagedSettingsManager =  
            new ShellSettingsManager(ServiceProvider.GlobalProvider);  
  
        private const int _maxGuides = 5;  
        private const string _collectionSettingsName = "Text Editor";  
        private const string _settingName = "Guides";  
        // 1000 seems reasonable since primary scenario is long lines of code  
        private const int _maxColumn = 1000;   
  
        static internal bool AddGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column",  
                    "The paramenter must be between 1 and " + _maxGuides.ToString());  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            if (offsets.Count() >= _maxGuides)  
                return false;  
            // Check for duplicates  
            if (offsets.Contains(column))  
                return false;  
            offsets.Add(column);  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);  
            return true;  
        }  
  
        static internal bool RemoveGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column", "The paramenter must be between 1 and 10,000");  
            var columns = GuidesSettingsManager.GetColumnOffsets();  
            if (! columns.Remove(column))  
            {  
                // Not present.  Allow user to remove the last column   
                // even if they're not on the right column.  
                if (columns.Count != 1)  
                    return false;  
  
                columns.Clear();  
            }  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);  
            return true;  
        }  
  
        static internal bool CanAddGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                return false;  
            var offsets = GetColumnOffsets();  
            if (offsets.Count >= _maxGuides)  
                return false;  
            return ! offsets.Contains(column);  
        }  
  
        static internal bool CanRemoveGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                return false;  
            // Allow user to remove the last guideline regardless of the column.  
            // Okay to call count, we limit the number of guides.  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            return offsets.Contains(column) || offsets.Count() == 1;  
        }  
  
        static internal void RemoveAllGuidelines()  
        {  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);  
        }  
  
        private static bool IsValidColumn(int column)  
        {  
            // zero is allowed (per user request)  
            return 0 <= column && column <= _maxColumn;  
        }  
  
        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".  
        // There can be any number of ints following the RGB part,   
        // and each int is a column (char offset into line) where to draw.  
        static private string _guidelinesConfiguration;  
        static private string GuidelinesConfiguration  
        {  
            get  
            {  
                if (_guidelinesConfiguration == null)  
                {  
                    _guidelinesConfiguration =   
                        GetUserSettingsString(  
                            GuidesSettingsManager._collectionSettingsName,  
                            GuidesSettingsManager._settingName)  
                        .Trim();  
                }  
                return _guidelinesConfiguration;  
            }  
  
            set  
            {  
                if (value != _guidelinesConfiguration)  
                {  
                    _guidelinesConfiguration = value;  
                    WriteUserSettingsString(  
                        GuidesSettingsManager._collectionSettingsName,  
                        GuidesSettingsManager._settingName, value);  
                    // Notify ColumnGuideAdornments to update adornments in views.  
                    var handler = GuidesSettingsManager.SettingsChanged;  
                    if (handler != null)  
                        handler();  
                }  
            }  
        }  
  
        internal static string GetUserSettingsString(string collection, string setting)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);  
            return store.GetString(collection, setting, "RGB(255,0,0) 80");  
        }  
  
        internal static void WriteUserSettingsString(string key, string propertyName,  
                                                     string value)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetWritableSettingsStore(SettingsScope.UserSettings);  
            store.CreateCollection(key);  
            store.SetString(key, propertyName, value);  
        }  
  
        // Persists settings and sets property with side effect of signaling  
        // ColumnGuideAdornments to update.  
        static private void WriteSettings(Color color, IEnumerable<int> columns)  
        {  
            string value = ComposeSettingsString(color, columns);  
            GuidelinesConfiguration = value;  
        }  
  
        private static string ComposeSettingsString(Color color,  
                                                    IEnumerable<int> columns)  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);  
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();  
            if (columnsEnumerator.MoveNext())  
            {  
                sb.AppendFormat(" {0}", columnsEnumerator.Current);  
                while (columnsEnumerator.MoveNext())  
                {  
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);  
                }  
            }  
            return sb.ToString();  
        }  
  
        // Parse a color out of a string that begins like "RGB(255,0,0)"  
        static internal Color GuidelinesColor  
        {  
            get  
            {  
                string config = GuidelinesConfiguration;  
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))  
                {  
                    int lastParen = config.IndexOf(')');  
                    if (lastParen > 4)  
                    {  
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');  
  
                        if (rgbs.Length >= 3)  
                        {  
                            byte r, g, b;  
                            if (byte.TryParse(rgbs[0], out r) &&  
                                byte.TryParse(rgbs[1], out g) &&  
                                byte.TryParse(rgbs[2], out b))  
                            {  
                                return Color.FromRgb(r, g, b);  
                            }  
                        }  
                    }  
                }  
                return Colors.DarkRed;  
            }  
  
            set  
            {  
                WriteSettings(value, GetColumnOffsets());  
            }  
        }  
  
        // Parse a list of integer values out of a string that looks like  
        // "RGB(255,0,0) 1, 5, 10, 80"  
        static internal List<int> GetColumnOffsets()  
        {  
            var result = new List<int>();  
            string settings = GuidesSettingsManager.GuidelinesConfiguration;  
            if (String.IsNullOrEmpty(settings))  
                return new List<int>();  
  
            if (!settings.StartsWith("RGB("))  
                return new List<int>();  
  
            int lastParen = settings.IndexOf(')');  
            if (lastParen <= 4)  
                return new List<int>();  
  
            string[] columns = settings.Substring(lastParen + 1).Split(',');  
  
            int columnCount = 0;  
            foreach (string columnText in columns)  
            {  
                int column = -1;  
                // VS 2008 gallery extension didn't allow zero, so per user request ...  
                if (int.TryParse(columnText, out column) && column >= 0)  
                {  
                    columnCount++;  
                    result.Add(column);  
                    if (columnCount >= _maxGuides)  
                        break;  
                }  
            }  
            return result;  
        }  
  
        // Delegate and Event to fire when settings change so that ColumnGuideAdornments   
        // can update.  We need nothing special in this event since the settings manager   
        // is statically available.  
        //  
        internal delegate void SettingsChangedHandler();  
        static internal event SettingsChangedHandler SettingsChanged;  
  
    }  
}  
  
```  
  
 Większość ten kod po prostu tworzy i analizuje ustawienia format: "RGB (\<int >,\<int >,\<int >) \<int >, \<int >,...".  Liczby całkowite na końcu są kolumn oparte na jednym miejscu prowadnice kolumn.  Rozszerzenie przewodniki kolumny przechwytuje wszystkie jego ustawienia w ciągu jednego ustawienie wartości.  
  
 Brak niektórych części kodu, warto wyróżniania.  Następujący wiersz kodu pobiera zarządzany otok Visual Studio do przechowywania ustawień.  W większości przypadków to abstracts w rejestrze systemu Windows, ale ten interfejs API jest niezależna od mechanizmu magazynowania.  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Magazyn ustawień programu Visual Studio używa identyfikatora kategorii i identyfikator ustawień do unikatowego identyfikowania wszystkie ustawienia:  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 Nie trzeba używać `"Text Editor"` jak kategoria Nazwa i wybrać niczego chcesz.  
  
 Pierwszy kilka funkcji są punkty wejścia, aby zmienić ustawienia.  Sprawdź ich ograniczenia wysokiego poziomu, takich jak maksymalna liczba przewodniki dozwolone.  Następnie wywołują `WriteSettings` co Redaguj ciąg ustawień i ustawia właściwość `GuideLinesConfiguration`.  Ustawienie dla tej właściwości wartość ustawienia jest zapisywany do programu Visual Studio ustawienia magazynu i uruchamiany `SettingsChanged` zdarzeń, aby zaktualizować wszystkie `ColumnGuideAdornment` obiekty, każdy powiązany z widokiem tekstu.  
  
 Istnieje kilka funkcji punktu wejścia, takich jak `CanAddGuideline`, które są używane do implementowania poleceń, które zmieniają ustawienia.  Gdy program Visual Studio zawiera menu, wysyła zapytanie, polecenia implementacji, aby zobaczyć, jeśli polecenie jest obecnie włączony, co to jest jego nazwa,... itd.  Poniżej zobaczysz jak podłączenie te punkty wejścia dla implementacji polecenia.  Zobacz [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md) Aby uzyskać więcej informacji na temat poleceń.  
  
## <a name="implementing-the-columnguideadornment-class"></a>Implementująca klasa ColumnGuideAdornment  
 `ColumnGuideAdornment` Utworzyć wystąpienia klasy dla każdego widoku tekstu, który może mieć skojarzenia.  Ta klasa nasłuchuje zdarzenia związane ze zmianą widoku lub zmianę ustawienia, aktualizowania lub ponownego narysowania kolumny prowadzi zgodnie z potrzebami.  
  
 Zastąp zawartość ColumnGuideAdornment.cs następujący kod (co omówiono poniżej):  
  
```csharp  
using System;  
using System.Windows.Media;  
using Microsoft.VisualStudio.Text.Editor;  
using System.Collections.Generic;  
using System.Windows.Shapes;  
using Microsoft.VisualStudio.Text.Formatting;  
using System.Windows;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Adornment class, one instance per text view that draws a guides on the viewport  
    /// </summary>  
    internal sealed class ColumnGuideAdornment  
    {  
        private const double _lineThickness = 1.0;  
        private IList<Line> _guidelines;  
        private IWpfTextView _view;  
        private double _baseIndentation;  
        private double _columnWidth;  
  
        /// <summary>  
        /// Creates editor column guidelines  
        /// </summary>  
        /// <param name="view">The <see cref="IWpfTextView"/> upon   
        /// which the adornment will be drawn</param>  
        public ColumnGuideAdornment(IWpfTextView view)  
        {  
            _view = view;  
            _guidelines = CreateGuidelines();  
            GuidesSettingsManager.SettingsChanged +=   
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);  
            view.LayoutChanged +=   
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);  
            _view.Closed += new EventHandler(OnViewClosed);  
        }  
  
        void SettingsChanged()  
        {  
            _guidelines = CreateGuidelines();  
            UpdatePositions();  
            AddGuidelinesToAdornmentLayer();  
        }  
  
        void OnViewClosed(object sender, EventArgs e)  
        {  
            _view.LayoutChanged -= OnViewLayoutChanged;  
            _view.Closed -= OnViewClosed;  
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;  
        }  
  
        private bool _firstLayoutDone;  
  
        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
        {  
            bool fUpdatePositions = false;  
  
            IFormattedLineSource lineSource = _view.FormattedLineSource;  
            if (lineSource == null)  
            {  
                return;  
            }  
            if (_columnWidth != lineSource.ColumnWidth)  
            {  
                _columnWidth = lineSource.ColumnWidth;  
                fUpdatePositions = true;  
            }  
            if (_baseIndentation != lineSource.BaseIndentation)  
            {  
                _baseIndentation = lineSource.BaseIndentation;  
                fUpdatePositions = true;  
            }  
            if (fUpdatePositions ||  
                e.VerticalTranslation ||  
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||  
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)  
            {  
                UpdatePositions();  
            }  
            if (!_firstLayoutDone)  
            {  
                AddGuidelinesToAdornmentLayer();  
                _firstLayoutDone = true;  
            }  
        }  
  
        private static IList<Line> CreateGuidelines()  
        {  
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);  
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });  
            IList<Line> result = new List<Line>();  
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())  
            {  
                Line line = new Line()  
                {  
                    // Use the DataContext slot as a cookie to hold the column  
                    DataContext = column,  
                    Stroke = lineBrush,  
                    StrokeThickness = _lineThickness,  
                    StrokeDashArray = dashArray  
                };  
                result.Add(line);  
            }  
            return result;  
        }  
  
        void UpdatePositions()  
        {  
            foreach (Line line in _guidelines)  
            {  
                int column = (int)line.DataContext;  
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;  
                line.X1 = line.X2;  
                line.Y1 = _view.ViewportTop;  
                line.Y2 = _view.ViewportBottom;  
            }  
        }  
  
        void AddGuidelinesToAdornmentLayer()  
        {  
            // Grab a reference to the adornment layer that this adornment   
            // should be added to  
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener  
            IAdornmentLayer adornmentLayer =   
                _view.GetAdornmentLayer("ColumnGuideAdornment");  
            if (adornmentLayer == null)  
                return;  
            adornmentLayer.RemoveAllAdornments();  
            // Add the guidelines to the adornment layer and make them relative   
            // to the viewport  
            foreach (UIElement element in _guidelines)  
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,  
                                            null, null, element, null);  
        }  
    }  
  
}  
```  
  
 Wystąpienia tej klasy są przechowywane na skojarzonym <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> oraz listę `Line` obiektów na widoku.  
  
 Konstruktora (wywoływane z `ColumnGuideAdornmentTextViewCreationListener` po Visual Studio tworzy nowe widoki) tworzy przewodnik kolumny `Line` obiektów.  Konstruktor również dodaje obsługę `SettingsChanged` zdarzenia (zdefiniowany w `GuidesSettingsManager`) i Wyświetl zdarzenia `LayoutChanged` i `Closed`.  
  
 `LayoutChanged` Zdarzenia generowane z powodu różnych typów zmian w widoku, w przypadku programu Visual Studio tworzy widok.  `OnViewLayoutChanged` Wywołań obsługi `AddGuidelinesToAdornmentLayer` do wykonania.  Kod w `OnViewLayoutChanged` Określa, czy należy zaktualizować pozycje wiersza w oparciu o zmiany, takie jak zmiany rozmiaru czcionek, odstępy widoku przewijanie w poziomie i tak dalej.  Kod w `UpdatePositions` powoduje, że zasady do rysowania między znakami lub zaraz po kolumnie tekst w przesunięciu określony znak w wierszu tekstu.  
  
 Zawsze, gdy zmiana ustawień `SettingsChanged` funkcja tylko odtwarza wszystkie `Line` obiekty są niezależnie od nowych ustawień.  Po ustawieniu pozycje wiersza, kod usuwa wszystkie poprzednie `Line` obiektów z `ColumnGuideAdornment` ozdób warstwy i dodaje nowe pliki.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Definiowanie polecenia menu i Menu rozmieszczanie  
 Może istnieć wiele deklarowanie poleceń i menu wprowadzania grupy poleceń lub menu na różnych innych menu i Podłączanie programy obsługi poleceń.  W tym przewodniku prezentuje sposób działania poleceń, w tym rozszerzeniu, ale uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Wprowadzenie do kodu  
 Pokazuje rozszerzenie prowadnice kolumn deklarowanie grupy poleceń, które należy razem (Dodaj kolumnę, usunąć kolumnę, zmienić kolor linii) i następnie w menu sub menu kontekstowe edytora wprowadzania do tej grupy.  Rozszerzenie prowadnice kolumn również dodaje polecenia do głównego **Edytuj** menu ale jednocześnie dbając o ich niewidoczne, omówiony jako wspólnego wzorca poniżej.  
  
 Implementacja poleceń, składa się z trzech części: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct i ColumnGuideCommands.cs.  Kod wygenerowany przez Szablony umieszcza polecenie na **narzędzia** menu, które pojawia się okno dialogowe jako implementacja.  Można przyjrzeć się jak zaimplementowanym w plikach ColumnGuideCommands.cs i vsct ponieważ jest dość proste.  Kod w tych plikach poniżej spowoduje zastąpienie.  
  
 Kod pakietu jest deklaracje standardowej, które są wymagane dla programu Visual Studio dowiedzieć się, że rozszerzenie oferuje polecenia i gdzie należy umieścić polecenia.  Inicjuje pakietu, utworzyć wystąpienia klasy wykonania polecenia.  Zobacz poleceń połączyć powyżej, aby uzyskać więcej informacji na temat pakietów odnoszących się do polecenia.  
  
### <a name="a-common-commands-pattern"></a>Wspólnego wzorca poleceń  
 Polecenia w rozszerzeniu prowadnice kolumn są przykładem bardzo typowy wzorzec w programie Visual Studio.  Umieścić pokrewnych poleceń w grupie, a można wprowadzić tej grupy menu głównego, często z "`<CommandFlag>CommandWellOnly</CommandFlag>`" ustawioną niewidoczna polecenia.  Wprowadzanie polecenia menu głównego (takich jak **Edytuj**) w ten sposób umożliwi im nazwy nieuprzywilejowany (takich jak **Edit.AddColumnGuide**) które są przydatne w przypadku znalezienia poleceń podczas ponownego przypisywania powiązań klucza w  **Narzędzia opcje** i pobrania ukończenia podczas wywoływania polecenia z **okno polecenia**.  
  
 Następnie dodaj grupy poleceń do menu kontekstowe lub sub, którego można spodziewać się użytkownikowi korzystanie z poleceń menu.  Visual Studio traktuje `CommandWellOnly` jako flagi niewidoczności tylko menu głównego.  Po umieszczeniu tej samej grupy poleceń menu kontekstowego lub sub menu polecenia są widoczne.  
  
 W ramach wspólnego wzorca rozszerzenia prowadnice kolumn tworzy grupę drugi zawierający pojedynczy podmenu.  Z kolei pod menu zawiera pierwszej grupy za pomocą poleceń przewodnik cztery kolumny.  Drugiej grupy, która przechowuje pod menu jest element wielokrotnego użytku zawartości, który można umieścić na różnych menu kontekstowego, który umieszcza pod menu na tych menu kontekstowe.  
  
### <a name="the-vsct-file"></a>Pliku vsct  
 Pliku vsct deklaruje poleceń i ich gdzie, wraz z ikon i tak dalej.  Zastąp zawartość pliku vsct następujący kod (co omówiono poniżej):  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <!--  This is the file that defines the actual layout and type of the commands.  
        It is divided in different sections (e.g. command definition, command  
        placement, ...), with each defining a specific set of properties.  
        See the comment before each section for more details about how to  
        use it. -->  
  
  <!--  The VSCT compiler (the tool that translates this file into the binary  
        format that VisualStudio will consume) has the ability to run a preprocessor  
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so  
        it is possible to define includes and macros with the same syntax used  
        in C++ files. Using this ability of the compiler here, we include some files  
        defining some of the constants that we will use inside the file. -->  
  
  <!--This is the file that defines the IDs for all the commands exposed by   
      VisualStudio. -->  
  <Extern href="stdidcmd.h"/>  
  
  <!--This header contains the command ids for the menus provided by the shell. -->  
  <Extern href="vsshlids.h"/>  
  
  <!--The Commands section is where commands, menus, and menu groups are defined.  
      This section uses a Guid to identify the package that provides the command   
      defined inside it. -->  
  <Commands package="guidColumnGuideCommandsPkg">  
    <!-- Inside this section we have different sub-sections: one for the menus, another    
    for the menu groups, one for the buttons (the actual commands), one for the combos   
    and the last one for the bitmaps used. Each element is identified by a command id  
    that is a unique pair of guid and numeric identifier; the guid part of the identifier  
    is usually called "command set" and is used to group different command inside a  
    logically related group; your package should define its own command set in order to  
    avoid collisions with command ids defined by other packages. -->  
  
    <!-- In this section you can define new menu groups. A menu group is a container for   
         other menus or buttons (commands); from a visual point of view you can see the   
         group as the part of a menu contained between two lines. The parent of a group   
         must be a menu. -->  
    <Groups>  
  
      <!-- The main group is parented to the edit menu. All the buttons within the group  
           have the "CommandWellOnly" flag, so they're actually invisible, but it means  
           they get canonical names that begin with "Edit". Using placements, the group  
           is also placed in the GuidesSubMenu group. -->  
      <!-- The priority 0xB801 is chosen so it goes just after   
           IDG_VS_EDIT_COMMANDWELL -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that  
           drops the sub menu). The group is parented to  
           the context menu for code windows. That takes care of most editors, but it's  
           also placed in a couple of other windows using Placements -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />  
      </Group>  
  
    </Groups>  
  
    <Menus>  
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"  
            type="Menu">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />  
        <Strings>  
          <ButtonText>&Column Guides</ButtonText>  
        </Strings>  
      </Menu>  
    </Menus>  
  
    <!--Buttons section. -->  
    <!--This section defines the elements the user can interact with, like a menu command or a button   
        or combo box in a toolbar. -->  
    <Buttons>  
      <!--To define a menu group you have to specify its ID, the parent menu and its   
          display priority.   
          The command is visible and enabled by default. If you need to change the   
          visibility, status, etc, you can use the CommandFlag node.  
          You can add more than one CommandFlag node e.g.:  
              <CommandFlag>DefaultInvisible</CommandFlag>  
              <CommandFlag>DynamicVisibility</CommandFlag>  
          If you do not want an image next to your command, remove the Icon node or   
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
              priority="0x0100" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicAddGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Add Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"   
              priority="0x0101" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Remove Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"   
              priority="0x0103" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicChooseColor" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Column Guide &Color...</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"   
              priority="0x0102" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Remove A&ll Columns</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
  
    <!--The bitmaps section is used to define the bitmaps that are used for the  
        commands.-->  
    <Bitmaps>  
      <!--  The bitmap id is defined in a way that is a little bit different from the  
            others:   
            the declaration starts with a guid for the bitmap strip, then there is the  
            resource id of the bitmap strip containing the bitmaps and then there are   
            the numeric ids of the elements used inside a button definition. An important  
            aspect of this declaration is that the element id   
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->  
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"   
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />  
    </Bitmaps>  
  
  </Commands>  
  
  <CommandPlacements>  
  
    <!-- Define secondary placements for our groups -->  
  
    <!-- Place the group containing the three commands in the sub-menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                      priority="0x0100">  
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
    </CommandPlacement>  
  
    <!-- The HTML editor context menu, for some reason, redefines its own groups  
         so we need to place a copy of our context menu there too. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />  
    </CommandPlacement>  
  
    <!-- The HTML context menu in Dev12 changed. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />  
    </CommandPlacement>  
  
    <!-- Similarly for Script -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />  
    </CommandPlacement>  
  
    <!-- Similarly for ASPX  -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />  
    </CommandPlacement>  
  
    <!-- Similarly for the XAML editor context menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x0600">  
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />  
    </CommandPlacement>  
  
  </CommandPlacements>  
  
  <!-- This defines the identifiers and their values used above to index resources  
       and specify commands. -->  
  <Symbols>  
    <!-- This is the package guid. -->  
    <GuidSymbol name="guidColumnGuideCommandsPkg"   
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />  
  
    <!-- This is the guid used to group the menu commands together -->  
    <GuidSymbol name="guidColumnGuidesCommandSet"   
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />  
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />  
      <IDSymbol name="GuidesSubMenu" value="0x1022" />  
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />  
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />  
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />  
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
      <IDSymbol name="bmpPicAddGuide" value="1" />  
      <IDSymbol name="bmpPicRemoveGuide" value="2" />  
      <IDSymbol name="bmpPicChooseColor" value="3" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"   
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />  
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />  
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">  
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />  
    </GuidSymbol>  
  </Symbols>  
  
</CommandTable>  
  
```  
  
 **IDENTYFIKATORY GUID**.  Dla programu Visual Studio można znaleźć programu obsługi polecenia i wywołaj je należy upewnić się, że pakiet, który GUID zadeklarowany w pliku ColumnGuideCommandsPackage.cs (wygenerowane z szablonu elementu projektu) jest zgodna pakiet, który GUID zadeklarowany w pliku vsct (skopiowany z powyższych ).  Jeśli używasz ponownie ten przykładowy kod, należy upewnić się, że inny identyfikator GUID, aby nie powodują konfliktów z wszystkich osób, które zostały skopiowane tego kodu.  
  
 Znajdź tego wiersza w ColumnGuideCommandsPackage.cs i skopiować identyfikator GUID znajdujące znaki cudzysłowu:  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 Następnie wklej identyfikator GUID w pliku vsct, tak aby było możliwe następujący wiersz Twojej `Symbols` deklaracje:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Ustaw identyfikatory GUID dla polecenia i plik obrazu mapy bitowej powinna być unikatowa dla rozszerzeń za:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Jednak nie należy zmieniać zestaw poleceń i map bitowych identyfikatorów GUID obrazu w ramach tego przewodnika uzyskać kod do działania.  Polecenie ustawiony identyfikator GUID musi odpowiadać deklaracji w pliku ColumnGuideCommands.cs, ale zawartość tego pliku spowoduje zastąpienie w związku z tym identyfikatory GUID będzie zgodny.  
  
 Innych identyfikatorów GUID w pliku vsct zidentyfikować istniejące menu, do których zostaną dodane polecenia przewodnik kolumny, więc nigdy nie ulegną zmianie.  
  
 **Plik sekcje**.  Vsct zawiera trzy sekcje zewnętrzne: poleceń, rozmieszczenia i symbole.  Sekcja polecenia definiuje grup polecenia, menu przycisków lub elementów menu i map bitowych ikon.  W sekcji rozmieszczanie deklaruje, gdzie grupy menu lub dodatkowe rozmieszczanie do istniejącego menu.  W sekcji symbole deklaruje identyfikatory używane w innym miejscu w pliku vsct, co sprawia, że kod vsct jest bardziej przejrzysta niż w przypadku identyfikatorów GUID i cyfr szesnastkowych wszędzie.  
  
 **Sekcja polecenia, definicje grup**.  Sekcja polecenia najpierw definiuje polecenie grupy.  Grupy poleceń są dostępne w menu nieznaczne liniami szare oddzielanie grupy polecenia.  Grupy mogą także wypełnić cały pod menu, jak w poniższym przykładzie, i w takim przypadku oddzielanie wierszy w kolorze szarym nie są wyświetlane.  Pliki vsct deklaruje dwie grupy `GuidesMenuItemsGroup` który jest elementem nadrzędnym w `IDM_VS_MENU_EDIT` (głównym **Edytuj** menu) i `GuidesContextMenuGroup` który jest elementem nadrzędnym w `IDM_VS_CTXT_CODEWIN` (menu kontekstowe edytora kodu).  
  
 Druga deklaracja grupy zawiera `0x0600` priorytet:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 Koncepcja jest umieszczenie kolumny prowadzi pod menu na końcu dowolnego menu kontekstowego, do którego możemy dodać grupy menu sub.  Jednak nie należy zakładać, najlepiej znasz i wymusić pod menu zawsze być ostatnim przy użyciu priorytet `0xFFFF`.  Należy odtworzyć z tym numerem, aby zobaczyć, których Twoje pod menu znajduje się w menu kontekstowe, gdzie umieścić.  W takim przypadku `0x0600` jest wystarczająco duża, aby ją na końcu menu jakim możemy stwierdzić, ale pozostawia miejsca dla innej osobie projektowania ich rozszerzenia są niższe niż rozszerzenie przewodniki kolumny, jeśli jest to pożądane.  
  
 **Polecenia menu definicji sekcji**.  Obok polecenia sekcja definiuje pod menu `GuidesSubMenu`, nadrzędnego do `GuidesContextMenuGroup`.  `GuidesContextMenuGroup` Jest grupa dodania do menu odpowiedni kontekst.  W sekcji rozmieszczanie kod umieszcza grupy za pomocą poleceń przewodnik cztery kolumny w tym menu podrzędnego.  
  
 **Sekcja polecenia, przyciski definicje**.  Polecenia sekcja definiuje elementy menu lub przycisków, które są cztery kolumny prowadzi poleceń.  `CommandWellOnly`, opisanych wyżej, oznacza polecenia są niewidoczne, umieszczone w menu głównym.  Dwa elementu menu przycisku deklaracje (Przewodnik Dodaj i Usuń przewodnik) również `AllowParams` flagi:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Ta flaga umożliwia wraz z konieczności rozmieszczanie menu głównego, polecenie do odbierania argumentów w przypadku programu Visual Studio wywołuje program obsługi poleceń.  Jeśli użytkownik wywołuje polecenia w oknie polecenia, argument jest przekazywane do programu obsługi poleceń w zdarzeniu argumentów.  
  
 **Polecenie sekcje, definicje map bitowych**.  Na koniec sekcji commands deklaruje map bitowych lub ikon używanych dla poleceń.  Jest to prosty deklaracji, która identyfikuje zasób projektu i listy jedynki indeksy używane ikon.  Symbole części pliku vsct deklaruje wartości identyfikatorów używany jako indeksy.  W tym przewodniku zastosowano paska mapy bitowej wyposażony szablon elementu polecenia niestandardowych dodane do projektu.  
  
 **Rozmieszczanie sekcji**.  Po poleceniach sekcja jest sekcją rozmieszczanie.  Pierwsza z nich jest, gdzie kod dodaje pierwszej grupy opisanych wyżej, który zawiera przewodnik cztery kolumny poleceń do sub menu miejsce polecenia:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Dodaj wszystkie inne rozmieszczanie `GuidesContextMenuGroup` (która zawiera `GuidesSubMenu`) do innych menu kontekstowe edytora.  Jeśli kod jest zadeklarowany `GuidesContextMenuGroup`, został on elementem nadrzędnym, w menu kontekstowe edytora kodu.  Właśnie dlatego nie ma umieszczania menu kontekstowe edytora kodu.  
  
 **Symbole sekcji**.  Jak już wspomniano w sekcji symbole deklaruje identyfikatory używane w innym miejscu w pliku vsct, co sprawia, że kod vsct jest bardziej przejrzysta niż w przypadku identyfikatorów GUID i cyfr szesnastkowych wszędzie.  Ważne punktów w tej sekcji są, że identyfikator GUID pakietu należy uzgodnić z deklaracją klasy pakietu i zestaw poleceń się, że identyfikator GUID należy uzgodnić z deklaracji w implementacji klasy poleceń.  
  
## <a name="implementing-the-commands"></a>Implementacja poleceń  
 Plik ColumnGuideCommands.cs implementuje poleceń i przechwytuje się obsługi.  Gdy program Visual Studio ładuje pakiet i inicjuje go, pakiet z kolei wywołuje `Initialize` w klasie wykonania polecenia.  Inicjowanie polecenia po prostu tworzy wystąpienie klasy i konstruktora przechwytuje się wszystkie programy obsługi poleceń.  
  
 Zastąp zawartość pliku ColumnGuideCommands.cs następujący kod (co omówiono poniżej):  
  
```csharp  
using System;  
using System.ComponentModel.Design;  
using System.Globalization;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
using Microsoft.VisualStudio.Text.Editor;  
using Microsoft.VisualStudio;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Command handler  
    /// </summary>  
    internal sealed class ColumnGuideCommands  
    {  
  
        const int cmdidAddColumnGuide = 0x0100;  
        const int cmdidRemoveColumnGuide = 0x0101;  
        const int cmdidChooseGuideColor = 0x0102;  
        const int cmdidRemoveAllColumnGuides = 0x0103;  
  
        /// <summary>  
        /// Command menu group (command set GUID).  
        /// </summary>  
        static readonly Guid CommandSet =   
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");  
  
        /// <summary>  
        /// VS Package that provides this command, not null.  
        /// </summary>  
        private readonly Package package;  
  
        OleMenuCommand _addGuidelineCommand;  
        OleMenuCommand _removeGuidelineCommand;  
  
        /// <summary>  
        /// Initializes the singleton instance of the command.  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        public static void Initialize(Package package)  
        {  
            Instance = new ColumnGuideCommands(package);  
        }  
  
        /// <summary>  
        /// Gets the instance of the command.  
        /// </summary>  
        public static ColumnGuideCommands Instance  
        {  
            get;  
            private set;  
        }  
  
        /// <summary>  
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.  
        /// Adds our command handlers for menu (commands must exist in the command   
        /// table file)  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        private ColumnGuideCommands(Package package)  
        {  
            if (package == null)  
            {  
                throw new ArgumentNullException("package");  
            }  
  
            this.package = package;  
  
            // Add our command handlers for menu (commands must exist in the .vsct file)  
  
            OleMenuCommandService commandService =  
                this.ServiceProvider.GetService(typeof(IMenuCommandService))  
                    as OleMenuCommandService;  
            if (commandService != null)  
            {  
                // Add guide  
                _addGuidelineCommand =   
                    new OleMenuCommand(AddColumnGuideExecuted, null,  
                                       AddColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidAddColumnGuide));  
                _addGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_addGuidelineCommand);  
                // Remove guide  
                _removeGuidelineCommand =  
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,  
                                       RemoveColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidRemoveColumnGuide));  
                _removeGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_removeGuidelineCommand);  
                // Choose color  
                commandService.AddCommand(  
                    new MenuCommand(ChooseGuideColorExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidChooseGuideColor)));  
                // Remove all  
                commandService.AddCommand(  
                    new MenuCommand(RemoveAllGuidelinesExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidRemoveAllColumnGuides)));  
            }  
        }  
  
        /// <summary>  
        /// Gets the service provider from the owner package.  
        /// </summary>  
        private IServiceProvider ServiceProvider  
        {  
            get  
            {  
                return this.package;  
            }  
        }  
  
        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _addGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanAddGuideline(currentColumn);  
        }  
  
        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _removeGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);  
        }  
  
        private int GetCurrentEditorColumn()  
        {  
            IVsTextView view = GetActiveTextView();  
            if (view == null)  
            {  
                return -1;  
            }  
  
            try  
            {  
                IWpfTextView textView = GetTextViewFromVsTextView(view);  
                int column = GetCaretColumn(textView);  
  
                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based  
                // positions.  
                // However, do not subtract one here since the caret is positioned to the  
                // left of  
                // the given column and the guidelines are positioned to the right. We  
                // want the  
                // guideline to line up with the current caret position. e.g. When the  
                // caret is  
                // at position 1 (zero-based), the status bar says column 2. We want to  
                // add a  
                // guideline for column 1 since that will place the guideline where the  
                // caret is.  
                return column;  
            }  
            catch (InvalidOperationException)  
            {  
                return -1;  
            }  
        }  
  
        /// <summary>  
        /// Find the active text view (if any) in the active document.  
        /// </summary>  
        /// <returns>The IVsTextView of the active view, or null if there is no active  
        /// document or the  
        /// active view in the active document is not a text view.</returns>  
        private IVsTextView GetActiveTextView()  
        {  
            IVsMonitorSelection selection =  
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))  
                                                    as IVsMonitorSelection;  
            object frameObj = null;  
            ErrorHandler.ThrowOnFailure(  
                selection.GetCurrentElementValue(  
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));  
  
            IVsWindowFrame frame = frameObj as IVsWindowFrame;  
            if (frame == null)  
            {  
                return null;  
            }  
  
            return GetActiveView(frame);  
        }  
  
        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)  
        {  
            if (windowFrame == null)  
            {  
                throw new ArgumentException("windowFrame");  
            }  
  
            object pvar;  
            ErrorHandler.ThrowOnFailure(  
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));  
  
            IVsTextView textView = pvar as IVsTextView;  
            if (textView == null)  
            {  
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
                if (codeWin != null)  
                {  
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
                }  
            }  
            return textView;  
        }  
  
        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)  
        {  
  
            if (view == null)  
            {  
                throw new ArgumentNullException("view");  
            }  
  
            IVsUserData userData = view as IVsUserData;  
            if (userData == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            object objTextViewHost;  
            if (VSConstants.S_OK  
                   != userData.GetData(Microsoft.VisualStudio  
                                                .Editor  
                                                .DefGuidList.guidIWpfTextViewHost,  
                                       out objTextViewHost))  
            {  
                throw new InvalidOperationException();  
            }  
  
            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
            if (textViewHost == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            return textViewHost.TextView;  
        }  
  
        /// <summary>  
        /// Given an IWpfTextView, find the position of the caret and report its column  
        /// number. The column number is 0-based  
        /// </summary>  
        /// <param name="textView">The text view containing the caret</param>  
        /// <returns>The column number of the caret's position. When the caret is at the  
        /// leftmost column, the return value is zero.</returns>  
        private static int GetCaretColumn(IWpfTextView textView)  
        {  
            // This is the code the editor uses to populate the status bar.  
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
                textView.Caret.ContainingTextViewLine;  
            double columnWidth = textView.FormattedLineSource.ColumnWidth;  
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                       / columnWidth));  
        }  
  
        /// <summary>  
        /// Determine the applicable column number for an add or remove command.  
        /// The column is parsed from command arguments, if present. Otherwise  
        /// the current position of the caret is used to determine the column.  
        /// </summary>  
        /// <param name="e">Event args passed to the command handler.</param>  
        /// <returns>The column number. May be negative to indicate the column number is  
        /// unavailable.</returns>  
        /// <exception cref="ArgumentException">The column number parsed from event args  
        /// was not a valid integer.</exception>  
        private int GetApplicableColumn(EventArgs e)  
        {  
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
            if (!string.IsNullOrEmpty(inValue))  
            {  
                int column;  
                if (!int.TryParse(inValue, out column) || column < 0)  
                    throw new ArgumentException("Invalid column");  
                return column;  
            }  
  
            return GetCurrentEditorColumn();  
        }  
  
        /// <summary>  
        /// This function is the callback used to execute a command when the a menu item  
        /// is clicked. See the Initialize method to see how the menu item is associated  
        /// to this function using the OleMenuCommandService service and the MenuCommand  
        /// class.  
        /// </summary>  
        private void AddColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.AddGuideline(column);  
            }  
        }  
  
        private void RemoveColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.RemoveGuideline(column);  
            }  
        }  
  
        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)  
        {  
            GuidesSettingsManager.RemoveAllGuidelines();  
        }  
  
        private void ChooseGuideColorExecuted(object sender, EventArgs e)  
        {  
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;  
  
            using (System.Windows.Forms.ColorDialog picker =   
                new System.Windows.Forms.ColorDialog())  
            {  
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,  
                                                             color.B);  
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
                {  
                    GuidesSettingsManager.GuidelinesColor =   
                        System.Windows.Media.Color.FromRgb(picker.Color.R,  
                                                           picker.Color.G,   
                                                           picker.Color.B);  
                }  
            }  
        }  
  
    }  
}  
  
```  
  
 **Usuń odwołania**.  W tym momencie Brak odwołania.  Naciśnij przycisk prawo wskaźnika w węźle odwołania w Eksploratorze rozwiązań.  Wybierz **Dodaj...**  polecenia.  **Dodaj odwołanie** okno dialogowe zawiera pole wyszukiwania w prawym górnym rogu.  Wprowadź "editor" (bez cudzysłowów).  Wybierz **Microsoft.VisualStudio.Editor** elementu (użytkownik musi zaznacz pole wyboru na lewo od elementu nie jest po prostu zaznacz element) i wybierz polecenie **OK** można dodać odwołania.  
  
 **Inicjowanie**.  Gdy klasa pakietu, wywołuje `Initialize` w klasie wykonania polecenia.  `ColumnGuideCommands` Inicjowania tworzy wystąpienie klasy i zapisuje wystąpienie klasy i odwołanie do pakietu w elementach członkowskich klasy.  
  
 Oto jeden ups haku programu obsługi poleceń z konstruktora klasy:  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Możesz utworzyć `OleMenuCommand`.  Visual Studio korzysta z pakietu Microsoft Office polecenia.  Klucza argumentów podczas tworzenia wystąpienia OleMenuCommand to funkcja, która implementuje polecenia (`AddColumnGuideExecuted`), funkcja wywoływana, gdy program Visual Studio zawiera menu przy użyciu polecenia (`AddColumnGuideBeforeQueryStatus`), a identyfikator polecenia.  Visual studio wywołuje funkcję stanu zapytania przed pokazaniem polecenie menu, aby polecenie lub mogą być się niewidoczne szarym dla konkretnego wyświetlanie menu (na przykład wyłączenie **kopii** Jeśli nie ma żadnego zaznaczenia), Zmień jego ikonę lub nawet zmienić jego nazwę (na przykład z Dodaj element do usunięcia coś) i tak dalej.  Identyfikator polecenia musi być zgodna Identyfikatora polecenia zadeklarowany w pliku vsct.  Ustawienie parametrów dla polecenia i prowadnice kolumn dodanie polecenia musi być taka sama między pliku vsct i ColumnGuideCommands.cs.  
  
 Następujący wiersz jest dostępna pomoc podczas użytkowników Wywołaj polecenie za pomocą okna wiersza polecenia (co omówiono poniżej):  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Zbadać stan**.  Funkcje zapytań stanu `AddColumnGuideBeforeQueryStatus` i `RemoveColumnGuideBeforeQueryStatus` Sprawdź niektórych ustawień (takich jak maksymalna liczba przewodników i maksymalnej kolumny) lub jeśli brakuje linii do usunięcia.  Umożliwiają one poleceń, jeśli warunki są prawidłowe.  Funkcje zapytań stanu muszą być bardzo efektywnym, ponieważ są uruchamiane za każdym razem, gdy Visual Studio zawiera menu, dla każdego polecenia w menu.  
  
 **Funkcja AddColumnGuideExecuted**.  Interesujące część Dodawanie przewodnik jest ustaleniem bieżącą lokalizację widoku i karetka edytora.  Najpierw wywołania tej funkcji `GetApplicableColumn` który sprawdza, czy argumentem dostarczone przez użytkownika w argumentach zdarzenia program obsługi poleceń, a jeśli nie ma none, funkcja sprawdzi widoku edytora:  
  
```csharp  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
    return GetCurrentEditorColumn();  
}  
  
```  
  
 `GetCurrentEditorColumn` ma szczegółowej, aby pobrać <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> widoku kodu.  Jeśli śledzenie za pośrednictwem `GetActiveTextView`, `GetActiveView`, i `GetTextViewFromVsTextView`, można zobaczyć, jak to zrobić.  Poniżej znajduje się odpowiedni kod, pobieranej, począwszy od bieżącego zaznaczenia, uzyskiwanie ramki wyboru, a następnie uzyskiwanie widoku ramki dokumentu jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, następnie konfigurowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> interfejsu IVsTextView, a następnie uzyskiwanie hostem widoku i na koniec element IWpfTextView:  
  
```csharp  
   IVsMonitorSelection selection =  
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))   
           as IVsMonitorSelection;  
   object frameObj = null;  
  
ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(  
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,  
                                out frameObj));  
  
   IVsWindowFrame frame = frameObj as IVsWindowFrame;  
   if (frame == null)  
       <<do nothing>>;  
  
...  
   object pvar;  
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,  
                                                  out pvar));  
  
   IVsTextView textView = pvar as IVsTextView;  
   if (textView == null)  
   {  
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
       if (codeWin != null)  
       {  
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
       }  
   }  
  
...  
   if (textView == null)  
       <<do nothing>>  
  
   IVsUserData userData = textView as IVsUserData;  
   if (userData == null)  
       <<do nothing>>  
  
   object objTextViewHost;  
   if (VSConstants.S_OK   
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList  
                                                            .guidIWpfTextViewHost,  
                                out objTextViewHost))  
   {  
       <<do nothing>>  
   }  
  
   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
   if (textViewHost == null)  
       <<do nothing>>  
  
   IWpfTextView textView = textViewHost.TextView;  
  
```  
  
 Po utworzeniu element IWpfTextView, możesz uzyskać kolumny, w którym znajduje się karetkę:  
  
```csharp  
private static int GetCaretColumn(IWpfTextView textView)  
{  
    // This is the code the editor uses to populate the status bar.  
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
        textView.Caret.ContainingTextViewLine;  
    double columnWidth = textView.FormattedLineSource.ColumnWidth;  
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                / columnWidth));  
}  
  
```  
  
 Z bieżącej kolumny w strony w przypadku, gdy użytkownik kliknie, kod po prostu wywołuje w Menedżer ustawień, aby dodać lub usunąć kolumny.  Menedżer ustawień generowane zdarzenie wszystkie `ColumnGuideAdornment` nasłuchiwania obiektów.  Wyzwala zdarzenie, te obiekty aktualizacji poglądów tekst skojarzony z nowych ustawień przewodnik kolumny.  
  
## <a name="invoking-command-from-the-command-window"></a>Wywoływanie polecenia w oknie polecenia  
 Przykładowe przewodniki kolumny umożliwia użytkownikom wywołać dwa polecenia w oknie polecenia rodzaj rozszerzalności.  Jeśli używasz **widoku &#124; inne okna &#124; okno polecenia** polecenia, można wyświetlić okno polecenia.  Pozwala na interakcję z okna poleceń wprowadzając "Edytuj", a z uzupełnianie nazw poleceń i przekazując argument 120, masz następujące:  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Części próbki, które są w deklaracjach pliku vsct, Włącz `ColumnGuideCommands` konstruktora klasy po jego przechwytuje programy obsługi poleceń i implementacje obsługi polecenia, które Sprawdź, czy argumenty zdarzeń.  
  
 Widać "`<CommandFlag>CommandWellOnly</CommandFlag>`" w pliku vsct, a także rozmieszczanie w menu głównym edycji mimo że firma Microsoft nie pokazuj poleceń w **Edytuj** menu interfejsu użytkownika.  Po ich w menu głównym edycji daje im nazwy, jak **Edit.AddColumnGuide**.  Polecenia grupy deklaracji, która przetrzymuje cztery polecenia umieścić grupy menu Edycja bezpośrednio:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 Sekcja przycisków później zadeklarowana polecenia `CommandWellOnly` aby były widoczne w menu głównym i zadeklarowane je za pomocą `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Widać program obsługi poleceń Podłączanie kodu w `ColumnGuideCommands` konstruktora klasy podać opis parametru dozwolonych:  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Widać `GetApplicableColumn` funkcji kontroli `OleMenuCmdEventArgs` dla wartości przed zaewidencjonowaniem widok edytora dla bieżącej kolumny:  
  
```csharp  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
```  
  
## <a name="trying-your-extension"></a>W trakcie rozszerzenia  
 Teraz możesz nacisnąć **F5** można wykonać rozszerzenia prowadnice kolumn.  Otwórz plik tekstowy i użyj menu kontekstowe edytora, aby dodać zasady, usuń je i zmienić kolor.  Musisz kliknąć przycisk w tekście (znak inny niż odstęp Przekroczono koniec wiersza) aby dodać kolumnę przewodnik lub edytorze dodaje go do ostatniej kolumny w wierszu.  Jeśli okno polecenia i Wywołaj poleceń z argumentem, możesz dodać prowadnice kolumn w dowolnym miejscu.  
  
 Jeśli chcesz spróbować rozmieszczanie inne polecenie, Zmień nazwy, zmienić ikony i tak dalej, a masz problemy z programem Visual Studio przedstawiający najnowsze kod w menu, można zresetować eksperymentalne hive, możesz debugowania.  Wywołaj **Menu Start systemu Windows** i wpisz "Resetowanie".  Znajdź i wywołaj polecenie **Zresetuj dalej Visual Studio eksperymentalne wystąpienie programu**.  To spowoduje oczyszczenie gałęzi rejestru eksperymentalne wszystkich składników rozszerzenia.  Nie ma oczyszczania limit ustawienia ze składników, więc wszystkie prowadnice miał podczas zamykania eksperymentalne hive Visual Studio będą po kod odczytuje magazyn ustawień przy następnym uruchomieniu.  
  
## <a name="finished-code-project"></a>Kod zakończenia projektu  
 Wkrótce będzie github projektu Visual Studio Extensibility próbek, a zostaną ukończone projektu.  W tym temacie, aby wskazywały istnieje w takim przypadku będą aktualizowane.  Ukończono przykładowy projekt może mieć różne identyfikatory GUID i będzie miał inną map bitowych pasek ikon polecenia.  
  
 Wersja funkcji przewodniki kolumny z tej galerii programu Visual Studio można wypróbować[rozszerzenia](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze](../extensibility/inside-the-editor.md)   
 [Rozszerzanie edytora i usług języka](../extensibility/extending-the-editor-and-language-services.md)   
 [Usługa języka i punkty rozszerzenia Edytora](../extensibility/language-service-and-editor-extension-points.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Dodawanie do Menu podmenu](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)