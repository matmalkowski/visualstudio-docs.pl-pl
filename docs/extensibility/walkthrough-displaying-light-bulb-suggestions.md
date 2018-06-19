---
title: 'Wskazówki: Wyświetlanie sugestii żarówki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 750e3b0915478b4249ce8db1ac294c1f2a3006f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148704"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Wskazówki: Wyświetlanie sugestii żarówka
Żarówki są ikon używanych w edytorze programu Visual Studio, które Rozwiń, aby wyświetlić zestaw akcji, na przykład poprawki dla problemy zidentyfikowane przez analizatorów wbudowanego kodu lub refaktoryzacji kodu.  
  
 W edytorach Visual C# i Visual Basic umożliwia także kompilatora platformy .NET ("Roslyn") do zapisu i analizatorów własnego kodu z akcjami, które automatycznie wyświetlać żarówki. Aby uzyskać więcej informacji, zobacz:  
  
-   [Porady: Pisanie diagnostyki C# i poprawki kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Porady: Pisanie diagnostycznych Visual Basic i poprawki kodu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Inne języki, takie jak C++ stanowią Ponadto żarówki niektóre szybkie akcje, takie jak uwag do tworzenia szkieletu stosowania tej funkcji.  
  
 Oto, jak wygląda żarówka. W projektach Visual Basic lub Visual C# czerwona falista jest wyświetlany w obszarze Nazwa zmiennej, gdy jest on nieprawidłowy. Jeśli myszą nieprawidłowy identyfikator, żarówka jest wyświetlany obok kursora.  
  
 ![żarówki](../extensibility/media/lightbulb.png "żarówka")  
  
 Jeśli klikniesz przycisk strzałki w dół przez żarówkę, wyświetlany jest zestaw sugerowanych akcji wraz z wersji zapoznawczej wybranej akcji. W takim przypadku go zawiera zmiany, które zostaną wprowadzone w kodzie, jeśli wykonanie akcji.  
  
 ![Podgląd żarówki](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Żarówki służy do nadania sugerowanych akcji. Na przykład można udostępnić akcje przenieść je na końcu poprzedniego wiersza lub Przenieś otwierających nawiasów klamrowych do nowego wiersza. Poniższe wskazówki przedstawiono sposób tworzenia żarówki, który pojawia się na bieżącego słowa i ma dwa sugerowanych akcji: **Konwertuj na wielkie litery** i **przekonwertować na małe litery**.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `LightBulbTest`.  
  
2.  Dodaj **klasyfikatora edytor** szablon elementu do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
4.  Dodaj następujące odwołanie do projektu i ustawić **Kopiuj lokalnie** do `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Dodaj nowy plik klasy i nadaj mu nazwę **LightBulbTest**.  
  
6.  Dodaj następujące instrukcje using:  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementowanie dostawcy źródła żarówka  
  
1.  Plik klasy LightBulbTest.cs Usuń klasy LightBulbTest. Dodaj klasę o nazwie **TestSuggestedActionsSourceProvider** implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Wyeksportować go przy użyciu nazwy **testu sugerowane akcje** i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Wewnątrz klasy dostawcy źródłowej, należy zaimportować <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i dodaj go jako właściwość.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodę, aby zwrócić <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> obiektu. Omówimy źródła w następnej sekcji.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementowanie ISuggestedActionSource  
 Źródło sugerowanych akcji jest odpowiedzialny za zbieranie zestaw sugerowanych akcji i dodawanie ich w kontekście prawo. W takim przypadku kontekst jest bieżącego słowa i sugerowane akcje są **UpperCaseSuggestedAction** i **LowerCaseSuggestedAction**, który omówimy w następnej sekcji.  
  
1.  Dodaj klasę **TestSuggestedActionsSource** implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Dodać pól prywatnych tylko do odczytu dla zalecane działanie źródłowego dostawcy, buforu tekstu i widoku tekstu.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Dodaj Konstruktor, który ustawia pól prywatnych.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Dodaj metody prywatnej, która zwraca słowa, które jest obecnie pod kursorem. Następującą metodę wygląda w bieżącej lokalizacji kursora i prosi Nawigatora struktury tekst o stopniu Word. Jeśli kursor znajduje się na wyraz <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> jest zwracane w parametrze wyjściowym; w przeciwnym razie `out` parametr jest `null` i metoda zwraca `false`.  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metody. Edytor wywołuje tę metodę, aby dowiedzieć się, czy mają być wyświetlane żarówkę. To wywołanie bardzo często, na przykład zawsze, gdy kursor są przenoszone z jednego wiersza do innego lub gdy wskaźnik myszy jest przesuwany nad wężyk błąd. Jest asynchroniczne, aby umożliwić inne operacje interfejsu użytkownika do przenoszenia, gdy ta metoda działa. W większości przypadków ta metoda musi wykonać niektóre analizowania i analizy bieżącego wiersza więc przetwarzanie może zająć trochę czasu.  
  
     W naszym implementacji asynchronicznie pobiera <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> i określa, czy zakres jest istotne, tj., czy ma ona tekst inne niż odstępy.  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodę, która zwraca tablicę <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> obiektów zawierających różnych <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> obiektów. Ta metoda jest wywoływana po rozwinięciu żarówkę.  
  
    > [!WARNING]
    >  Upewnij się, że implementacje `HasSuggestedActionsAsync()` i `GetSuggestedActions()` są spójne; która jest, jeśli `HasSuggestedActionsAsync()` zwraca `true`, następnie `GetSuggestedActions()` powinny mieć określone akcje do wyświetlenia. W wielu przypadkach `HasSuggestedActionsAsync()` jest wywoływana tuż przed `GetSuggestedActions()`, ale nie zawsze jest wielkość liter. Na przykład, jeśli użytkownik wywołuje akcje żarówki naciskając (CTRL +.) tylko `GetSuggestedActions()` jest wywoływana.  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Zdefiniuj `SuggestedActionsChanged` zdarzeń.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Aby ukończyć implementacji, należy dodać implementacji dla `Dispose()` i `TryGetTelemetryId()` metody. Nie chcemy nie telemetrii, zwraca wartość false, więc po prostu i Ustaw identyfikator GUID na element Empty.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Implementowanie akcje żarówka  
  
1.  W projekcie Dodaj odwołanie do Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll i zestaw **Kopiuj lokalnie** do `False`.  
  
2.  Utwórz dwie klasy o nazwie pierwszy `UpperCaseSuggestedAction` i drugiego o nazwie `LowerCaseSuggestedAction`. Zarówno klasy implementować <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Obie klasy są podobne, z wyjątkiem tego, że jeden wywołuje <xref:System.String.ToUpper%2A> i inne wywołania <xref:System.String.ToLower%2A>. W poniższych krokach opisano tylko klasy akcji wielkie litery, ale musi implementować zarówno klasy. Wykonaj kroki implementacji wielkie akcji jako wzorzec do wykonania akcji małe litery.  
  
3.  Dodaj następujące instrukcje using dla tych klas:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Deklarowanie zestaw pól prywatnych.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Dodaj Konstruktor, który ustawia pola.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metody, którego nie wyświetla podgląd akcji.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metody, dzięki czemu zwraca pustą <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> wyliczenia.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementowanie właściwości w następujący sposób.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metody, zastępując tekst w zakresie odpowiadającym mu wielkie litery.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Akcja żarówki **Invoke** nie oczekiwano metody można wyświetlić interfejsu użytkownika.  Jeśli Twoja Akcja wyświetlić nowy interfejs użytkownika (na przykład podgląd lub zaznaczenie okna dialogowego), nie są bezpośrednio z poziomu interfejsu użytkownika **Invoke** metody, ale zamiast tego harmonogramu do wyświetlenia interfejsu użytkownika po powrocie z **Invoke**.  
  
10. Aby ukończyć implementację, Dodaj `Dispose()` i `TryGetTelemetryId()` metody.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Nie zapomnij tak samo postąpić w `LowerCaseSuggestedAction` zmiana wyświetlany tekst "Konwersji"{0}"na małe litery" i wywołanie <xref:System.String.ToUpper%2A> do <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie LightBulbTest i uruchom go w eksperymentalnym wystąpieniu.  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz tekst. Powinny pojawić się żarówka się po lewej stronie tekstu.  
  
     ![Testowanie żarówkę](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Wskaż żarówkę. Powinny pojawić się strzałkę w dół.  
  
5.  Po kliknięciu żarówkę dwóch sugerowanych akcji powinien zostać wyświetlony wraz z wersji zapoznawczej wybranej akcji.  
  
     ![Testowanie żarówki rozwinięty](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Jeśli klikniesz pierwszą akcją cały tekst w bieżącego słowa powinny być konwertowane na wielkie litery. Jeśli klikniesz przycisk drugiej akcji, cały tekst powinien zostać przekonwertowany na małe litery.  
  