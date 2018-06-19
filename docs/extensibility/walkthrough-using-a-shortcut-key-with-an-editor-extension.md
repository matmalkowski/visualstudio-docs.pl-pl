---
title: 'Wskazówki: Używanie klawisza skrótu z rozszerzeniem edytora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8f8a310832f0691b4bc4056baddeb1fbbad78f8
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704028"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Wskazówki: Używanie klawisza skrótu z rozszerzeniem edytora
Klawisze skrótu można odpowiedzieć w rozszerzenia edytora. Poniższe wskazówki przedstawiono sposób dodawania ozdób widok na widok tekstu przy użyciu klawisza skrótu. Ten przewodnik jest oparty na szablonie Edytor ozdób okienka ekranu, i umożliwia dodawanie ozdób przy użyciu + znak.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Tworzenie projektu Framework (MEF) zarządzanych rozszerzeń  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `KeyBindingTest`.  
  
2.  Dodaj szablon elementu Edytor tekstu ozdób do projektu i nadaj mu nazwę `KeyBindingTest`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Dodaj następujące odwołania i ustaw **CopyLocal** do `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
 Plik klasy KeyBindingTest należy zmienić nazwę klasy do PurpleCornerBox. Umożliwia żarówki, która jest wyświetlana na lewym marginesie wprowadzić odpowiednie zmiany. Wewnątrz konstruktora, Zmień nazwę warstwy ozdób z **KeyBindingTest** do **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

Plik klasy KeyBindingTestTextViewCreationListener.cs, Zmień nazwę AdornmentLayer z **KeyBindingTest** do **PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handling-typechar-command"></a>Polecenie TYPECHAR obsługi
Przed Visual Studio 2017 wersji 15,6, jedynym sposobem obsługi poleceń w edytorze rozszerzenie zostało implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> na podstawie filtru polecenia. Visual Studio 2017 wersji 15,6 wprowadzono nowoczesnych metoda uproszczona oparte na programy obsługi poleceń edytora. W dwóch następnych sekcjach pokazano sposób obsługi polecenia przy użyciu zarówno podejście starszych i nowoczesny.

## <a name="defining-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definiowanie filtru polecenia (przed Visual Studio 2017 wersji 15,6)

 Polecenie filtru jest implementacją <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, który obsługuje polecenie przez utworzenie wystąpienia ozdób.  
  
1.  Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandFilter`.  
  
2.  Dodaj następujące instrukcje using.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  Klasa o nazwie KeyBindingCommandFilter powinien dziedziczyć <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  Dodać pól prywatnych dla widoku tekstu, następne polecenie w łańcuchu polecenia i flagę określającą, czy polecenie Filtr został już dodany.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  Dodaj Konstruktor, który ustawia widoku tekstu.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  Implementowanie `QueryStatus()` metody w następujący sposób.  
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  Implementowanie `Exec()` metodę, tak że dodaje purpurowa pole do widoku, jeśli + wpisany jest znak.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Dodawanie filtru polecenia (przed Visual Studio 2017 wersji 15,6)
 Dostawca ozdób należy dodać polecenie Filtr do widoku tekstu. W tym przykładzie implementuje dostawcę <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> do nasłuchiwania zdarzeń tworzenia widoku tekstu. Ten dostawca ozdób Eksportuje również warstwy ozdób, która określa porządek osi z ozdób.  
  
1.  W pliku KeyBindingTestTextViewCreationListener, Dodaj następujące instrukcje using:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  Aby uzyskać karty widoku tekstu, należy zaimportować <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  Zmień <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak że dodaje `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter` Obsługi pobiera karty widoku tekstu, a następnie dodaje filtr polecenia.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Wdrożenie programu obsługi poleceń (począwszy od programu Visual Studio 2017 wersji 15,6)

Najpierw należy zaktualizować odwołań Nuget projektu do odwołania najnowsze Edytor interfejsu API:

1. Kliknij prawym przyciskiem myszy na projekt i wybierz **Zarządzaj pakietami Nuget**.

2. W **Menedżera pakietów Nuget**, wybierz pozycję **aktualizacje** wybierz opcję **wybrać wszystkie pakiety** pole wyboru, a następnie wybierz **aktualizacji**.

Program obsługi poleceń jest implementacją <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, który obsługuje polecenie przez utworzenie wystąpienia ozdób.  
  
1.  Dodaj plik klasy i nadaj mu nazwę `KeyBindingCommandHandler`.  
  
2.  Dodaj następujące instrukcje using.  
  
    ```csharp  
    using Microsoft.VisualStudio.Commanding;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;   
    ```  
  
3.  Klasa o nazwie KeyBindingCommandHandler powinien dziedziczyć `ICommandHandler<TypeCharCommandArgs>`i wyeksportować ją jako <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
    ```csharp  
    [Export(typeof(ICommandHandler))]
    [ContentType("text")]
    [Name("KeyBindingTest")]
    internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
    ```  
  
4.  Dodaj nazwę wyświetlaną obsługi polecenia:  
  
    ```csharp  
    public string DisplayName => "KeyBindingTest";
    ```  
    
5.  Implementowanie `GetCommandState()` metody w następujący sposób. Ponieważ ten program obsługi poleceń obsługuje polecenie TYPECHAR Edytor core, można delegować, włączanie polecenia do edytora core.
  
    ```csharp  
    public CommandState GetCommandState(TypeCharCommandArgs args)
    {
        return CommandState.Unspecified;
    } 
    ```  
  
6.  Implementowanie `ExecuteCommand()` metodę, tak że dodaje purpurowa pole do widoku, jeśli + wpisany jest znak. 
  
    ```csharp  
    public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
    {
        if (args.TypedChar == '+')
        {
            bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
                "KeyBindingTextAdorned", out bool adorned) && adorned;
            if (!alreadyAdorned)
            {
                new PurpleCornerBox((IWpfTextView)args.TextView);
                args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
            }
        }

        return false;
    }
    ```  
 7. Skopiuj ozdób warstwy definicję z pliku KeyBindingTestTextViewCreationListener.cs do KeyBindingCommandHandler.cs, a następnie usuń plik KeyBindingTestTextViewCreationListener.cs:
 
    ```csharp  
    /// <summary>
    /// Defines the adornment layer for the adornment. This layer is ordered
    /// after the selection layer in the Z-order.
    /// </summary>
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("PurpleCornerBox")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    private AdornmentLayerDefinition editorAdornmentLayer;    
    ```  

## <a name="making-the-adornment-appear-on-every-line"></a>Tworzenie ozdób są wyświetlane w każdym wierszu  

Oryginalny ozdób znajdowały się na każdym znakiem "" w pliku tekstowym. Teraz, gdy zmieniono kodu w celu dodania ozdób w odpowiedzi na znak "+" dodaje ozdób tylko w wierszu gdzie '+' został wpisany. Możemy zmienić kod ozdób tak, aby ponownie ozdób pojawia się na każdym "".  
  
W pliku KeyBindingTest.cs Zmień metodę CreateVisuals() do iterowania po wszystkich wierszy w widoku do dekoracji znak "".  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie KeyBindingTest i uruchom go w eksperymentalnym wystąpieniu.  
  
2.  Utwórz lub Otwórz plik tekstowy. Wpisz część wyrazów zawierających znak "", a następnie wpisz + w dowolnym miejscu widoku tekstu.  
  
     Purpurowa kwadratowe powinny pojawiać się na każdej "" znak w pliku.
