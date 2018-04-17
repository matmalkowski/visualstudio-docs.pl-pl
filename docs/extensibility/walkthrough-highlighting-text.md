---
title: 'Wskazówki: Wyróżnianie tekstu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 90bf22bfe65b1120f5cc149d95eea25357b8ffa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-highlighting-text"></a>Wskazówki: Wyróżnianie tekstu
Różne efekty można dodać do edytora, tworząc części Managed Extensibility Framework (MEF). W tym przewodniku przedstawiono sposób zaznacz każde wystąpienie bieżącego słowa w pliku tekstowym. Jeśli wyraz występuje więcej niż jeden raz w pliku tekstowym, a następnie pozycji karetki w jedno wystąpienie, każde wystąpienie zostanie wyróżniona.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `HighlightWordTest`.  
  
2.  Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń pliki istniejące klasy.  
  
## <a name="defining-a-textmarkertag"></a>Definiowanie TextMarkerTag  
 Pierwszym krokiem w wyróżnianie tekstu jest podklasą <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> i zdefiniowania wyglądu.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Aby zdefiniować TextMarkerTag i MarkerFormatDefinition  
  
1.  Dodaj plik klasy i nadaj mu nazwę **HighlightWordTag**.  
  
2.  Dodaj następujące informacje:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Importuj następujących przestrzeni nazw.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  Utwórz klasę, która dziedziczy <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> i nadaj mu nazwę `HighlightWordTag`.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Tworzenie drugiej klasy, która dziedziczy <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>i nadaj mu nazwę HighlightWordFormatDefinition. Aby użyć tej definicji formatu dla Twojego tagu, należy go wyeksportować z następującymi atrybutami:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: tagi służy do tego formatu odwołania  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: powoduje formatu, które mają być widoczne w Interfejsie użytkownika  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  W Konstruktorze HighlightWordFormatDefinition określić jego nazwę wyświetlaną i wyglądu. Właściwość tło Określa kolor wypełnienia podczas pierwszego planu właściwość określa kolor obramowania.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  W Konstruktorze HighlightWordTag przekaż nazwę utworzonego Definicja formatu.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Implementowanie ITagger  
 Następnym krokiem jest zaimplementowanie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interfejsu. Ten interfejs przypisuje bufora podanego tekstu, tagi, które zapewniają wyróżnianie tekstu i inne efekty wizualne.  
  
#### <a name="to-implement-a-tagger"></a>Aby zaimplementować modułu znakowania  
  
1.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `HighlightWordTag`i nadaj mu nazwę `HighlightWordTagger`.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Dodaj następujące prywatne pola i właściwości klasy:  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, Które odpowiada bieżący widok tekstu.  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Które odpowiada buforu tekstu źródłową widoku tekstu.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, Która jest używana do znajdowania tekstu.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, Mającego metody poruszanie się w obrębie fragmentu tekstu.  
  
    -   A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, który zawiera zbiór słów, aby wyróżnić.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, które odpowiada bieżącego słowa.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, który odpowiada bieżącej pozycji karetki.  
  
    -   Obiekt blokady.  
  
    ```csharp  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  Dodaj Konstruktor, który inicjuje właściwości wymienione wcześniej i dodaje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> procedury obsługi zdarzeń.  
  
    ```csharp  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  Zarówno wywołań obsługi zdarzeń `UpdateAtCaretPosition` metody.  
  
    ```csharp  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  Musisz również dodać `TagsChanged` zdarzeń, która zostanie wywołana za pomocą metody aktualizacji.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()` Metoda znajdzie każdego wyrazu w buforze tekst, który jest taki sam jak word, gdy kursor znajduje się i konstruuje listę <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiektów, które odpowiadają wystąpienia wyrazu. Następnie wywołuje `SynchronousUpdate`, które generuje `TagsChanged` zdarzeń.  
  
    ```csharp  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  `SynchronousUpdate` Przeprowadzają aktualizacji synchronicznej `WordSpans` i `CurrentWord` właściwości i zgłasza `TagsChanged` zdarzeń.  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  Musisz zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metody. Ta metoda przyjmuje Kolekcja <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiekty i zwraca wyliczenie tag zakresów.  
  
     W języku C# należy zaimplementować tę metodę jako iterator wydajności, co umożliwia obliczanie leniwe (to znaczy w celu oceny zestawu tylko wtedy, gdy są dostępne poszczególne elementy) tagów. W języku Visual Basic dodać tagi do listy, a zwrócona lista.  
  
     W tym miejscu metoda zwraca <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> obiektu, który ma "blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, zapewniające niebieskie tło.  
  
    ```csharp  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>Tworzenie dostawcy modułu znakowania  
 Aby utworzyć użytkownika modułu znakowania, musisz zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Ta klasa jest część MEF, więc należy ustawić prawidłowe atrybuty, dzięki czemu to rozszerzenie jest rozpoznawana.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
#### <a name="to-create-a-tagger-provider"></a>Aby utworzyć dostawcę modułu znakowania  
  
1.  Utwórz klasę o nazwie `HighlightWordTaggerProvider` implementującej <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  Dwie usługi edytora, należy zaimportować <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> i <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, można utworzyć wystąpienia modułu znakowania.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> sposób zwrócenia wystąpienia klasy `HighlightWordTagger`.  
  
    ```csharp  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
 Do przetestowania tego kodu, Skompiluj rozwiązanie HighlightWordTest i uruchom go w eksperymentalnym wystąpieniu.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Tworzenie i testowanie rozwiązania HighlightWordTest  
  
1.  Skompiluj rozwiązanie.  
  
2.  Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio zostanie uruchomiony.  
  
3.  Utwórz plik tekstowy i wpisz dowolny tekst, w których wyrazy są powtarzane, na przykład "hello hello hello".  
  
4.  Umieść kursor w jednym z wystąpień tekst "hello". Każde wystąpienie powinno być zaznaczone na niebiesko.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)