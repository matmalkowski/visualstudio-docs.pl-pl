---
title: "Wskazówki: Używanie klawisza skrótu z rozszerzeniem edytora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 60cfb35e2c3acbe3b52f460b040dd5c220e6b045
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
## <a name="defining-the-command-filter"></a>Definiowanie filtru polecenia  
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
  
    ```vb  
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
  
## <a name="adding-the-command-filter"></a>Dodawanie filtru polecenia  
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
  
2.  W definicji warstwy ozdób, Zmień nazwę AdornmentLayer z **KeyBindingTest** do **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3.  Aby uzyskać karty widoku tekstu, należy zaimportować <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4.  Zmień <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak że dodaje `KeyBindingCommandFilter`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5.  `AddCommandFilter` Obsługi pobiera karty widoku tekstu, a następnie dodaje filtr polecenia.  
  
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