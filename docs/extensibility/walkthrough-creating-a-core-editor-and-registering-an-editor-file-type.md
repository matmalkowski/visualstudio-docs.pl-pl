---
title: "Tworzenie edytora rdzeni i rejestrowania edytora plików typu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ace475cb94920a5c0470c1d16265349edfa441f4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Wskazówki: Tworzenie edytora rdzeni i rejestrowania edytora typu pliku
W tym przewodniku pokazano, jak utworzyć pakiet VSPackage, który rozpoczyna się [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core edytor, gdy plik ma rozszerzenie nazwy pliku .myext jest załadowany.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablonów projektu pakietu programu Visual Studio  
 Szablon projektu pakietu Visual Studio można znaleźć w trzech różnych miejscach w **nowy projekt** okna dialogowego:  
  
1.  W obszarze rozszerzalności języka Visual Basic. Domyślny język projektu jest Visual Basic.  
  
2.  W języku C# rozszerzalności. Domyślny język projektu jest C#.  
  
3.  W obszarze innych rozszerzeń typy projektu. Domyślny język projektu jest C++.  
  
### <a name="to-create-the-vspackage"></a>Aby utworzyć pakiet VSPackage  
  
-   Uruchom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i Utwórz [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pakiet VSPackage o nazwie `MyPackage`, zgodnie z opisem w [wskazówki: tworzenie pakiet VSPackage polecenia Menu](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Aby dodać fabryki edytora  
  
1.  Kliknij prawym przyciskiem myszy **MyPackage** projektu, wskaż pozycję **Dodaj** , a następnie kliknij przycisk **klasy**.  
  
2.  W **Dodaj nowy element** okna dialogowego upewnij się, **klasy** wybrano szablonu typu `EditorFactory.cs` nazwę, a następnie kliknij przycisk **Dodaj** można dodać klasy do projektu.  
  
     Plik EditorFactory.cs powinien zostać otwarty automatycznie.  
  
3.  Odwołuje się do następujących zestawów w kodzie.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Dodaj identyfikator GUID `EditorFactory` klasy, dodając `Guid` atrybutu bezpośrednio przed deklaracją klasy.  
  
     Możesz wygenerować nowy identyfikator GUID za pomocą programu guidgen.exe na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wierszu polecenia, lub klikając **utworzyć identyfikatora GUID** na **narzędzia** menu. Identyfikator GUID używany w tym miejscu jest tylko przykładem; nie należy używać go w projekcie.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  W definicji klasy Dodaj dwie zmienne prywatnej zawierają pakietu nadrzędnego i dostawcy usług.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Dodaj Konstruktor klasy publicznego, który przyjmuje jeden parametr typu <xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Modyfikowanie `EditorFactory` deklaracji pochodzić z klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Kliknij prawym przyciskiem myszy <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, kliknij przycisk **implementuj interfejs**, a następnie kliknij przycisk **zaimplementuj interfejs jawnie**.  
  
     Spowoduje to dodanie czterech metod, które muszą zostać zaimplementowane w <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu.  
  
9. Zastąp zawartość `IVsEditorFactory.Close` metodę z następującym kodem.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Zastąp zawartość `IVsEditorFactory.SetSite` z następującym kodem.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Zastąp zawartość `IVsEditorFactory.MapLogicalView` metodę z następującym kodem.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Zastąp zawartość `IVsEditorFactory.CreateEditorInstance` metodę z następującym kodem.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Skompiluj projekt i upewnij się, że nie ma żadnych błędów.  
  
### <a name="to-register-the-editor-factory"></a>Aby zarejestrować fabryki edytora  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik Resources.resx, aby otworzyć go do tabeli ciągów, w którym wpis **ciąg1 jest** wybrane.  
  
2.  Zmień nazwę identyfikatora do `IDS_EDITORNAME` i tekst, który **MyPackage edytora.** Ten ciąg będzie wyświetlana jako nazwa edytora.  
  
3.  Otwórz plik VSPackage.resx i Dodaj nową string, ustaw nazwę **101** i wartości do `IDS_EDITORNAME`. Zapewnia to pakietu z Identyfikatorem zasobu do dostępu ciąg, który został utworzony.  
  
    > [!NOTE]
    >  Jeśli plik VSPackage.resx zawiera inny ciąg, który `name` ustawić atrybutu **101**, Zastąp innej wartości liczbowe, unikatową, w tym miejscu, a w kolejnych krokach.  
  
4.  W **Eksploratora rozwiązań**, otwórz plik MyPackagePackage.cs.  
  
     To jest plik pakietu głównego.  
  
5.  Dodaj następujące atrybuty użytkownika bezpośrednio przed `Guid` atrybutu.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Atrybut kojarzy rozszerzenie pliku .myext z fabryką edytora, aby każdy razem pliku, który ma czy załadowano rozszerzenia, jest wywoływany z fabryki edytora.  
  
6.  Dodawanie zmiennej prywatnej do `MyPackage` klasy bezpośrednio przed konstruktora i nadaj mu typ `EditorFactory`.  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  Znajdź `Initialize` — metoda (może być konieczne otwarcie `Package Members` region ukryty) i Dodaj następujący kod po wywołaniu `base.Initialize()`.  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Kompilowanie programu i upewnij się, że nie ma żadnych błędów.  
  
     Ten krok rejestruje fabrykę edytora w gałęzi rejestru eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jeśli zostanie wyświetlony monit, aby zastąpić plik resource.h, kliknij przycisk **OK**.  
  
9. Utwórz przykładowy plik o nazwie TextFile1.myext.  
  
10. Naciśnij klawisz **F5** do Otwórz wystąpienie eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. W eksperymentalnym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]na **pliku** menu wskaż **Otwórz** , a następnie kliknij przycisk **pliku**.  
  
12. Znajdź TextFile1.myext, a następnie kliknij przycisk **Otwórz**.  
  
     Teraz można załadować pliku.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor core obsługuje szeroką gamę typów plików tekstowych i działa dokładnie z usług języka aby zapewnić bogaty zestaw funkcji, takich jak wyróżnianie składni, parowanie nawiasów klamrowych oraz IntelliSense zakończenia programu word i zakończenia elementu członkowskiego. Jeśli pracujesz z plików tekstowych, można użyć edytora core razem usługa języka niestandardowej, która obsługuje sieci określonych typów plików.  
  
 Pakiet VSPackage może wywołać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor core podając fabryki edytora. Ta fabryka edytora jest używana zawsze, gdy Załadowano plik, który jest skojarzony z nim. Jeśli plik jest częścią projektu, Edytor core jest wywoływana automatycznie, chyba że zastąpione VSPackage. Jednak jeśli plik został załadowany poza projektem, następnie Edytor podstawowe muszą być jawnie wywoływane przez VSPackage.  
  
 Aby uzyskać więcej informacji o Edytorze core, zobacz [w edytorze Core](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze Core](../extensibility/inside-the-core-editor.md)   
 [Tworzenie wystąpień Edytor Core przy użyciu interfejsu API starsza wersja](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)