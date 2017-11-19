---
title: "Subskrybowanie zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d2b5d07fb143f84b3680d51624469b9778b42a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="subscribing-to-an-event"></a>Subskrybowanie zdarzeń
W tym przewodniku opisano sposób tworzenia okna narzędzia, która reaguje na zdarzenia w uruchomionej tabeli dokumentu (Normalizacją). Okno narzędzia obsługuje kontrolkę użytkownika, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Metody łączy interfejsu zdarzenia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Subskrybowanie zdarzeń Normalizacją  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Aby utworzyć rozszerzenia za pomocą okna narzędzia  
  
1.  Tworzenie projektu o nazwie **RDTExplorer** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okna o nazwie **RDTExplorerWindow**.  
  
     Aby uzyskać więcej informacji o tworzeniu rozszerzenie z okna narzędzia, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Aby subskrybować zdarzenia Normalizacją  
  
1.  Otwórz plik RDTExplorerWindowControl.xaml i usunąć przycisk o nazwie `button1`. Dodaj <xref:System.Windows.Forms.ListBox> kontroli i zaakceptuj nazwę domyślną. Element siatki powinien wyglądać następująco:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Otwórz plik RDTExplorerWindow.cs w widoku kodu. Dodaj następujące instrukcje using na początku pliku.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Modyfikowanie `RDTExplorerWindow` klasy, że oprócz wynikających z <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> klasa implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfejsu.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Zaimplementuj interfejs. Umieść kursor na nazwie IVsRunningDocTableEvents. Żarówka na lewym marginesie powinna zostać wyświetlona. Kliknij strzałkę w prawo żarówki i wybierz **implementuj interfejs**.  
  
5.  W każdej metody w interfejsie Zastąp linię `throw new NotImplementedException();` z tym:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Dodaj pole pliku cookie do klasy RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Dotyczy pliku cookie, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metody.  
  
7.  Zastąp metodę Initialize() RDTExplorerWindow do rejestrowania zdarzeń Normalizacją. Należy zawsze uzyskać usług w metodę Initialize() obiektu ToolWindowPane, nie znajduje się w konstruktorze.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Usługi jest wywoływana w celu uzyskania <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Metody łączy Normalizacją zdarzeń do obiektu, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, w tym przypadku obiektu RDTExplorer.  
  
8.  Zaktualizuj metodę Dispose() RDTExplorerWindow.  
  
    ```csharp  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Metoda usuwa połączenie między `RDTExplorer` i powiadamianie o zdarzeniach Normalizacją.  
  
9. Dodaj następujący wiersz do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> obsługi, bezpośrednio przed `return` instrukcji.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Dodaj wiersz podobny do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> obsługi i inne zdarzenia, które mają być wyświetlane w polu listy.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.  
  
12. Otwórz **RDTExplorerWindow** (**widoku / innych okien / RDTExplorerWindow**).  
  
     **RDTExplorerWindow** zostanie otwarte okno z listy zdarzeń puste.  
  
13. Otwarcia lub utworzenia rozwiązania.  
  
     Jako `OnBeforeLastDocument` i `OnAfterFirstDocument` uruchomienia zdarzeń, każdego zdarzenia pojawi się powiadomienie zdarzeń listy.