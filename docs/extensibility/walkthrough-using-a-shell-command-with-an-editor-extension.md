---
title: 'Wskazówki: Korzystanie z polecenia powłoki z rozszerzeniem edytora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112e78e6143d0a3bd67ff2a65814f2d77b85cdc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Wskazówki: Korzystanie z polecenia powłoki z rozszerzeniem edytora
W pakiet VSPackage można dodać funkcji, takich jak polecenia menu do edytora. W tym przewodniku przedstawiono sposób dodawania ozdób widoku tekstu w edytorze za pomocą polecenia menu.  
  
 W tym przewodniku zademonstrowano użycie pakiet VSPackage wraz z część Managed Extensibility Framework (MEF). Pakiet VSPackage musi służy do rejestrowania poleceń menu z powłoki programu Visual Studio i można uzyskać dostępu do części składników MEF polecenia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia Menu  
 Utwórz pakiet VSPackage, który umieszcza polecenie menu o nazwie **dodać ozdób** na **narzędzia** menu.  
  
1.  Tworzenie projektu VSIX C# o nazwie `MenuCommandTest`i Dodaj nazwę szablonu elementu polecenia niestandardowych **AddAdornment**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Rozwiązanie o nazwie MenuCommandTest jest otwarty. Plik MenuCommandTestPackage zawiera kod, który tworzy polecenia menu i umieszcza je na **narzędzia** menu. W tym momencie polecenie tak powoduje, że komunikat, który będzie wyświetlany. Dalszych krokach pokazano, jak zmienić, aby wyświetlić ozdób komentarza.  
  
3.  Otwórz plik Source.Extension.vsixmanifest,a w edytorze manifestu VSIX. `Assets` Kartę powinny mieć wiersza dla Microsoft.VisualStudio.VsPackage o nazwie MenuCommandTest.  
  
4.  Zapisz i zamknij plik Source.Extension.vsixmanifest,a.  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Dodawanie rozszerzenia MEF do rozszerzenia polecenia  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**. W **Dodawanie nowego projektu** okno dialogowe, kliknij przycisk **rozszerzalności** w obszarze **Visual C#**, następnie **projektu VSIX**. Nazwij projekt `CommentAdornmentTest`.  
  
2.  Ponieważ ten projekt będzie współpracować z zestawu o silnej nazwie pakiet VSPackage, należy podpisać zestawu. Można użyć ponownie już utworzone dla zestawu pakiet VSPackage pliku klucza.  
  
    1.  Otwórz właściwości projektu i wybierz **podpisywanie** kartę.  
  
    2.  Wybierz **Podpisz zestaw**.  
  
    3.  W obszarze **wybierz plik klucza o silnej nazwie**, wybierz plik Key.snk, który został wygenerowany dla zestawu MenuCommandTest.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Odwołanie do rozszerzenia MEF w projekcie pakiet VSPackage  
 Ponieważ dodawania składników MEF do pakiet VSPackage, należy określić oba rodzaje zasoby w manifeście.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Aby odwołać się do składników MEF w projekcie pakiet VSPackage  
  
1.  W projekcie MenuCommandTest Otwórz plik Source.Extension.vsixmanifest,a w edytorze manifestu VSIX.  
  
2.  Na **zasoby** , kliknij pozycję **nowy**.  
  
3.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
5.  W **projektu** wybierz **CommentAdornmentTest**.  
  
6.  Zapisz i zamknij plik Source.Extension.vsixmanifest,a.  
  
7.  Upewnij się, że projekt MenuCommandTest zawiera odwołanie do projektu CommentAdornmentTest.  
  
8.  W projekcie CommentAdornmentTest Ustaw projekt do tworzenia zestawu. W **Eksploratora rozwiązań**, wybierz projekt i Znajdź **właściwości** w oknie **dane wyjściowe kompilacji kopiowania do OutputDirectory** właściwości i ustaw ją na **true**.  
  
## <a name="defining-a-comment-adornment"></a>Definiowanie ozdób komentarza  
 Ozdób komentarza, sama składa się z <xref:Microsoft.VisualStudio.Text.ITrackingSpan> który śledzi zaznaczonego tekstu, a niektóre ciągów, które reprezentują autora i opis tekstu.  
  
#### <a name="to-define-a-comment-adornment"></a>Aby zdefiniować ozdób komentarza  
  
1.  W projekcie CommentAdornmentTest Dodaj nowy plik klasy i nadaj mu nazwę `CommentAdornment`.  
  
2.  Dodaj następujące informacje:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Dodaj następujące `using` instrukcji.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Plik powinien zawierać klasę o nazwie `CommentAdornment`.  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  Dodaj trzy pola `CommentAdornment` klasy dla <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, autora i opis.  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Dodaj Konstruktor, który inicjuje pola.  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Tworzenie elementu wizualnego dla ozdób  
 Element wizualny również muszą być zdefiniowane dla Twojego ozdób. W ramach tego przewodnika, zdefiniuj formant, który dziedziczy z klasy Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.  
  
1.  Utwórz klasę w projekcie CommentAdornmentTest i nadaj mu nazwę `CommentBlock`.  
  
2.  Dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Wprowadź `CommentBlock` klasa dziedziczy <xref:System.Windows.Controls.Canvas>.  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Dodać niektórych pól prywatnych do definiowania visual aspektów ozdób.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Dodaj konstruktora, który definiuje ozdób komentarz i dodaje tekst.  
  
    ```csharp  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
         Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
         Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  Implementuje również <xref:System.Windows.Controls.Panel.OnRender%2A> obsługi zdarzeń, który pobiera ozdób.  
  
    ```csharp  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Dodawanie IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Jest częścią składników MEF służącego do nasłuchiwania do wyświetlania zdarzeń tworzenia.  
  
1.  Dodaj plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `Connector`.  
  
2.  Dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Deklarowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text" i <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. Atrybut typu zawartości określa typ zawartości, którego dotyczy składnika. Typ tekst jest typem podstawowym dla wszystkich typów plików z systemem innym niż dane binarne. W związku z tym będzie niemal każdego widoku tekstu, który jest tworzony tego typu. Atrybut roli widoku tekstu określa rodzaj widoku tekstu, którego dotyczy składnika. Role widoku tekstu dokument zazwyczaj Pokaż tekst, który składa się z wierszy i są przechowywane w pliku.  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak że wywołuje statycznych `Create()` zdarzenie `CommentAdornmentManager`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Dodaj metodę, która służy do wykonania polecenia.  
  
    ```csharp  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="defining-an-adornment-layer"></a>Definiowanie ozdób warstwy  
 Aby dodać nowy ozdób, należy zdefiniować warstwy ozdób.  
  
#### <a name="to-define-an-adornment-layer"></a>Aby zdefiniować ozdób warstwy  
  
1.  W `Connector` klasy zadeklarować pole publiczne typu <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>i wyeksportować go przy użyciu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , który określa unikatową nazwę warstwy ozdób i <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> definiuje relację porządek osi z tą warstwą ozdób na inny tekst Wyświetl warstwy (tekst, karetki i wyboru).  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Zapewnianie skojarzenia komentarza  
 Podczas definiowania ozdób także zaimplementować dostawcę ozdób komentarz i menedżerem ozdób komentarza. Dostawca ozdób komentarz przechowuje listę komentarz skojarzenia, nasłuchuje <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń w podstawowej buforu tekstu i usuwa komentarz skojarzenia po usunięciu tekst źródłowy.  
  
1.  Dodaj nowy plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `CommentAdornmentProvider`.  
  
2.  Dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Dodaj klasę o nazwie `CommentAdornmentProvider`.  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Dodaj pola prywatne dla buforu tekstu i listę komentarz skojarzenia związane z buforu.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  Dodaj Konstruktor do `CommentAdornmentProvider`. Ten konstruktor powinien mieć dostępu prywatnego, ponieważ dostawca jest utworzone przez `Create()` metody. Dodaje konstruktora `OnBufferChanged` program obsługi zdarzeń do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> zdarzeń.  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Dodaj `Create()` metody.  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Dodaj `Detach()` metody.  
  
    ```csharp  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  Dodaj `OnBufferChanged` obsługi zdarzeń.  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Dodaj deklarację dla `CommentsChanged` zdarzeń.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Utwórz `Add()` metody w celu dodania ozdób.  
  
    ```csharp  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. Dodaj `RemoveComments()` metody.  
  
    ```csharp  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. Dodaj `GetComments()` metodę zwracającą wszystkie komentarze w zakresie danego migawki.  
  
    ```csharp  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. Dodaj klasę o nazwie `CommentsChangedEventArgs`, wykonując następujące czynności.  
  
    ```csharp  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="managing-comment-adornments"></a>Zarządzanie skojarzenia komentarza  
 Menedżer ozdób komentarz tworzy ozdób i dodaje go do warstwy ozdób. Wykrywa on <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzeń, dzięki czemu można przenieść ani usunąć ozdób. On również nasłuchuje `CommentsChanged` zdarzenia wywoływane przez dostawcę ozdób komentarza po komentarze zostały dodane lub usunięte.  
  
1.  Dodaj plik klasy do projektu CommentAdornmentTest i nadaj mu nazwę `CommentAdornmentManager`.  
  
2.  Dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Dodaj klasę o nazwie `CommentAdornmentManager`.  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Dodać niektórych pól prywatnych.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Dodaj Konstruktor, który subskrybuje Menedżera do <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> zdarzenia, a także do `CommentsChanged` zdarzeń. Konstruktor jest prywatny, ponieważ Menedżer jest utworzone przez statycznych `Create()` metody.  
  
    ```csharp  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  Dodaj `Create()` metodę, która pobiera dostawcę lub tworzy jeden, jeśli jest to wymagane.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Dodaj `CommentsChanged` obsługi.  
  
    ```csharp  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  Dodaj <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> obsługi.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Dodaj <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> obsługi.  
  
    ```csharp  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. Dodaj metody prywatnej, która pobiera komentarz.  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>Aby dodać komentarz ozdób za pomocą polecenia Menu  
 To polecenie umożliwia utworzenie ozdób komentarz zaimplementowanie `MenuItemCallback` metody pakiet VSPackage.  
  
1.  Dodaj następujące odwołania do projektu MenuCommandTest:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Otwórz plik AddAdornment.cs i dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Usuń metodę ShowMessageBox() i Dodaj następujący program obsługi poleceń.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Dodaj kod, aby pobrać widoku aktywnego. Należy uzyskać `SVsTextManager` powłoki programu Visual Studio można pobrać aktywne `IVsTextView`.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Ten widok tekstu w przypadku wystąpienia widoku edytora tekstu, należy rzutować go na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> interfejs, a następnie zachęcić <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> i skojarzone <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Użyj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> do wywołania `Connector.Execute()` metodę, która pobiera dostawcę ozdób komentarz i dodaje ozdób. Program obsługi poleceń powinna wyglądać następująco:  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
                            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  Ustaw metodę AddAdornmentHandler jako program obsługi dla polecenia AddAdornment w Konstruktorze AddAdornment.  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
2.  Utwórz plik tekstowy. Wpisz tekst, a następnie zaznacz go.  
  
3.  Na **narzędzia** menu, kliknij przycisk **wywołania ozdób dodać**. Dymek powinna być wyświetlana po prawej stronie okna tekstowego i powinien zawierać tekst, który jest podobny do następującego.  
  
     Nazwa_użytkownika  
  
     Fourscore...  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)