---
title: Adaptacja starszego kodu do edytora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e90a0f8ba27199e3837c59cd7980f027d0485a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adaptacja starszego kodu do edytora
Edytor programu Visual Studio zawiera wiele funkcji, które są dostępne z istniejącymi elementami kodu. Poniższe instrukcje przedstawiają sposób dostosowania składników MEF nie, na przykład pakiet VSPackage, aby korzystać z funkcji edytora. Instrukcje również pokazują, jak używać kart można pobrać usługi edytora kodu zarządzane i niezarządzane.  
  
## <a name="editor-adapters"></a>Edytor kart  
 Edytor kart lub podkładek, są otoki dla obiektów edytora, które również udostępniają klasy i interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop> interfejsu API. Używając kart do przechodzenia między usług z systemem innym niż edytora, na przykład polecenia powłoki programu Visual Studio i Edytor usług. (To jest jak edytor jest obecnie hostowany w programie Visual Studio). Karty również włączyć starszej wersji rozszerzenia usługi edytora i języka działać poprawnie w programie Visual Studio.  
  
## <a name="using-editor-adapters"></a>Za pomocą edytora kart  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Udostępnia metody, które przełączać się między nowe interfejsy edytora i interfejsy starszej wersji, a także metody tworzące kart.  
  
 Jeśli używasz tej usługi w ramach składników MEF, usługi można zaimportować w następujący sposób.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Jeśli chcesz używać tej usługi w składniku z systemem innym niż MEF, postępuj zgodnie z instrukcjami w sekcji "Przy użyciu programu Visual Studio edytora w Non-MEF składnik usług" w dalszej części tego tematu.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Przełączanie między nowy interfejs API edytora i starsza wersja interfejsu API  
 Użyj następujących metod można przełączać się między obiekt edytora i starszej wersji interfejsu.  
  
|Metoda|Konwersja|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Konwertuje <xref:Microsoft.VisualStudio.Text.ITextBuffer> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Konwertuje <xref:Microsoft.VisualStudio.Text.Editor.ITextView> do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Konwertuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Tworzenie kart  
 Następujące metody umożliwiają utworzenie kart interfejsów starszej wersji.  
  
|Metoda|Konwersja|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> dla określonej <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dla <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Tworzy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Tworzenie kart za pomocą kodu niezarządzanego  
 Wszystkie klasy karty zarejestrowanych lokalną wspólnie możliwość utworzenia i mogą zostać utworzone przy użyciu `VsLocalCreateInstance()` funkcji.  
  
 Wszystkie karty są tworzone za pomocą identyfikatorów GUID, które są zdefiniowane w pliku vsshlids.h... \VisualStudioIntegration\Common\Inc\ folder instalacji programu Visual Studio SDK. Aby utworzyć wystąpienie VsTextBufferAdapter, użyj następującego kodu.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Tworzenie kart w kodzie zarządzanym  
 W kodzie zarządzanym kart można utworzyć umieszczone w taki sam sposób jak opisana dla niezarządzanego kodu. Umożliwia także MEF usługa, która umożliwia tworzenie i interakcję z kartami. Ten sposób pobierania adapter umożliwia bardziej szczegółową kontrolę niż liczba kupionych po utworzeniu wspólnie.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Aby utworzyć adaptera dla interfejsu IVsTextView  
  
1.  Dodaj odwołanie do Microsoft.VisualStudio.Editor.dll. Upewnij się, że `CopyLocal` ma ustawioną wartość `false`.  
  
2.  Utwórz wystąpienie <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, wykonując następujące czynności.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Wywołanie `CreateX()` metody.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Za pomocą edytora programu Visual Studio bezpośrednio z kodem niezarządzanym  
 Przestrzeń nazw Microsoft.VisualStudio.Platform.VSEditor i przestrzeni nazw Microsoft.VisualStudio.Platform.VSEditor.Interop uwidocznić interfejsy COM można wywołać jako IVx * interfejsów. Na przykład interfejs Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer jest wersja COM <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfejsu. Z `IVxTextBuffer`, można uzyskać dostęp do migawek buforu, zmodyfikuj buforu, nasłuchiwania zdarzeń zmiany tekstu w buforze i tworzenie punktów śledzenia i zakresami. W poniższej procedurze pokazano, jak uzyskać dostęp do `IVxTextBuffer` z `IVsTextBuffer`.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Aby uzyskać IVxTextBuffer  
  
1.  Definicje dla interfejsów IVx * znajdują się w pliku VSEditor.h w... \VisualStudioIntegration\Common\Inc\ folder instalacji programu Visual Studio SDK.  
  
2.  Poniższy kod tworzy buforu tekstu przy użyciu `IVsUserData->GetData()` metody. W poniższym kodzie `pData` jest wskaźnikiem do `IVsUserData` obiektu.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>W składniku MEF z systemem innym niż przy użyciu usługi w edytorze programu Visual Studio  
 Jeśli masz istniejący składnik kodu zarządzanego, które nie są używane MEF i chcesz korzystać z usług w edytorze programu Visual Studio, musisz dodać odwołanie do zestawu, który zawiera pakiet ComponentModelHost VSPackage i pobrać jego SComponentModel usługi.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Użycie składników edytora programu Visual Studio z składnika z systemem innym niż MEF  
  
1.  Dodaj odwołanie do zestawu Microsoft.VisualStudio.ComponentModelHost.dll w... \Common7\IDE\ folder instalacji programu Visual Studio. Upewnij się, że `CopyLocal` ma ustawioną wartość `false`.  
  
2.  Dodaj prywatnej `IComponentModel` elementu członkowskiego do klasy, w której chcesz użyć usługi edytora programu Visual Studio, w następujący sposób.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Utworzenie wystąpienia składnika modelu w metodzie inicjowania dla składnika.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Dowolny usług edytora programu Visual Studio po to, można uzyskać przez wywołanie metody `IComponentModel.GetService<T>()` metody dla usługi ma.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```