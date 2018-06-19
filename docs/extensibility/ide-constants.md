---
title: Stałe środowiska IDE | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9c7e870b02dbe5a903ca8195954ffd5a8f63549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133121"
---
# <a name="ide-constants"></a>Stałe środowiska IDE

<xref:Microsoft.VisualStudio.VSConstants> Klasa zawiera stałe, które są specyficzne dla zintegrowane środowisko programistyczne (IDE) i które zostały wcześniej zdefiniowane tylko w plikach nagłówka.

## <a name="logical-and-physical-views"></a>Widoki logiczny i fizyczny

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi należy przekazać tę wartość na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby pobrać **Otwórz za pomocą** okno dialogowe, w tym przypadku na dostępnych widoków kodu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazać tę wartość, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby pobrać **Otwórz za pomocą** okno dialogowe, w tym przypadku są wypełniane przy użyciu możliwości <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> debugowania widoków, które mapują do tego samego widoku <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazać tę wartość na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby pobrać **Otwórz za pomocą** okno dialogowe, w tym przypadku do **Wyświetl formularz** projektanta widoków.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazać tę wartość na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby pobrać **Otwórz za pomocą** okno dialogowe, w tym przypadku widok domyślny/podstawowej fabryki edytora.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazać tę wartość na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodę, aby pobrać **Otwórz za pomocą** okno dialogowe, w tym dla dokumentu lub dane widoku edytora tekstu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` programy obsługi przekazać tę wartość na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody, które monituje użytkownika o wybranie widoku zdefiniowane przez użytkownika do użycia.|

## <a name="editor-factory-flags"></a>Flagi fabryki edytora

|Wartość|Opis|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Przestarzałe flagi łączyć alternatywy bitowej jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody.|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Połączone alternatywy bitowej jako pierwszego parametru metody <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, metody, oznacza to, fabryki edytora należy wykonać niezbędne poprawki.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Połączone alternatywy bitowej jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, ta flaga jest wzajemnie exclusive [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Połączone alternatywy bitowej jako pierwszy parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, oznacza to, fabryki edytora należy utworzyć Edytor bez wyświetlania interfejsu użytkownika (UI).|

## <a name="visual-studio-errors"></a>Visual Studio Errors

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Stała zwracana przez interfejsy do asynchronicznego zachowanie podczas danego obiektu w już zajęty|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "niezgodny dokumentu danych".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący "Pakiet nie został załadowany."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący, że "Projektu już istnieje."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący "Konfiguracja projektu nie powiodło się."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący "Projekt nie został załadowany."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący "Rozwiązanie już otwarta."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący "Rozwiązania nie jest otwarte."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Zwrócony przez interfejsy kompilacji, które mają parametry służącą do tablicy z <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfejsu, ale implementacja może dotyczyć tylko metody wszystkie dane wyjściowe.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Metoda zwraca tę wartość, jeśli dokument ma format, który nie może być otwarty w edytorze.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Wartość HRESULT, która wskazuje, że użytkownik przycisku Wstecz w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kreatora.|

## <a name="visual-studio-constants"></a>Stałe programu Visual Studio

|Wartość|Opis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Wystąpił błąd HRESULT, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wskazujący "Przekazywane projekt".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Stała, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "znacznika przybornika".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Stała, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dla komunikatu powiadomienia za pośrednictwem emisji <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodę, która wskazuje początek modalność.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Stała, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dla komunikatu powiadomienia za pośrednictwem emisji <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodę, która wskazuje koniec modalność.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Stała, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dla komunikatu powiadomienia za pośrednictwem emisji <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metody wskazujący, że metryki paska poleceń zostały zmienione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Stała, która jest specyficzna dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wskazujące, że plik cookie nie została ustawiona.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identyfikator elementu, który reprezentuje braku elementu projektu. Ta wartość jest używana, gdy nie ma żadnego bieżącego zaznaczenia.|
|[VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identyfikator elementu, który reprezentuje element główny hierarchii projektu i służy do identyfikowania całej hierarchii, w przeciwieństwie do pojedynczego elementu.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identyfikator elementu, który reprezentuje aktualnie zaznaczony element lub elementy, które mogą obejmować głównym hierarchii.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 W tym artykule opisano, jakie składnik IDE właśnie zostało zaznaczone, w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> wywołać, np.

|Stała|Wartość|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Stałe używane do wskazania nowy stan zaznaczenia.

|Stała|Wartość|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Stałe okna dialogowego selektora składnika

|Stała|Wartość|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Zobacz też

- [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)