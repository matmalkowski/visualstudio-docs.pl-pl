---
title: "Zachowanie nowe lub zostały zmienione z kartami Edytor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f69bbed7c335afb6b570de34cbef70470abd373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Zachowanie nowe lub zostały zmienione z kartami edytora
Jeśli aktualizujesz kodu napisanego dla wcześniejszych wersji edytorze podstawowych programu Visual Studio i zamierzasz używać kart edytora (lub podkładek) zamiast przy użyciu nowego interfejsu API, należy zwrócić uwagę następujące różnice w zachowaniu kart edytora względem poprzedniej Edytor core.  
  
## <a name="features"></a>Funkcje  
  
#### <a name="using-setsite"></a>Przy użyciu SetSite()  
 Należy wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> po współuczestniczyć w tworzeniu bufory tekstu, widoki tekstu i kodu systemu windows, przed wykonaniem innych operacji na nich. Jednak nie jest to konieczne, jeśli używasz <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> do ich tworzenia, ponieważ wywołanie metody Create() tej usługi, same <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosting IVsCodeWindow i interfejsy IVsTextView w własną zawartość  
 Można obsługiwać oba <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> w własną zawartość przy użyciu trybu Win32 lub tryb WPF. Jednak należy mieć na uwadze, że istnieją pewne różnice w dwóch trybach.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Przy użyciu wersji IVsCodeWindow Win32 i WPF  
 Okno edytora kodu jest pochodną <xref:Microsoft.VisualStudio.Shell.WindowPane>, który implementuje starsze Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu oraz nowe WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfejsu. Można użyć <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodę, aby utworzyć na podstawie HWND Środowisko hostingu, lub <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodę, aby utworzyć środowisko macierzyste WPF. Podstawowej edytora zawsze używa WPF, ale można utworzyć rodzaj okienka, pasujące hostingu wymagań, jeśli są osadzanie tego okienka bezpośrednio do własną zawartość.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Używane wersje interfejsu IVsTextView Win32 i WPF  
 Można ustawić <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do trybu Win32 lub WPF.  
  
 Gdy fabryki edytora tworzy widoku tekstu, domyślnie jest obsługiwany HWND i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> zwraca HWND. W tym trybie nie należy używać do osadzenia edytora w formancie WPF.  
  
 Aby ustawić tryb WPF widoku tekstu, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> i podaj <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> zgodnie z jedną inicjowania flagi w `InitView` parametru. Możesz uzyskać <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Tryb WPF różni się od trybu Win32 na dwa sposoby. Po pierwsze widoku tekstu może być hostowana w kontekście WPF. Dostęp do okienka WPF przez rzutowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> i wywoływania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Drugi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> nadal zwraca HWND, ale ta HWND może służyć tylko do sprawdź jego położenie i ustawić na nim fokus. Nie wolno używać tego HWND odpowiada na komunikat WM_PAINT, ponieważ go nie wpływa na sposób Edytor umożliwia malowanie okna. Ta właściwość HWND znajduje się tylko do ułatwienia przejścia do nowego kodu z edytora za pomocą kart. Zdecydowanie zaleca się, że nie należy używać `VIF_NO_HWND_SUPPORT` Jeśli składnik wymaga do pracy z powodu ograniczeń w HWND zwrócony z właściwością HWND `GetWindowHandle` while w tym trybie.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Przekazywanie tablic jako parametrów w kodzie natywnym  
 Istnieje wiele metod w edytorze starszej wersji interfejsu API, które ma parametry, które obejmują tablicy i jego liczbę. Przykłady to:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Jeśli te metody są wywołanie w kodzie natywnym, należy podać w tylko jeden element naraz. W przypadku przekazania w więcej niż jeden element, wywołanie zostanie odrzucone, z powodu problemów z implementacją międzyoperacyjnego podstawowego.  
  
 Problem jest bardziej złożony z metody takie jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Za każdym razem, gdy ta metoda jest wywoływana, czyści poprzedniej listy typów znaczników została zignorowana, nie jest możliwe tylko po to wywołać tę metodę trzy razy z trzech znacznika różnych typów. Jest to jedyny środek tę metodę można wywołać tylko w kodzie zarządzanym.  
  
#### <a name="threading"></a>Wątkowość  
 Zawsze należy wywołać karty buforu z wątku interfejsu użytkownika. Karta buforu jest obiekt zarządzany, co oznacza, że wywołanie go z kodu zarządzanego pomijał kierowanie modelu COM i połączenia będą nie automatycznie można organizować w wątku interfejsu użytkownika.  Jeśli dzwonisz karty buforu wątku w tle, należy użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub podobnej metody.  
  
#### <a name="lockbuffer-methods"></a>Metody LockBuffer  
 Wszystkie metody LockBuffer() są przestarzałe. Przykłady to:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Zatwierdź zdarzenia  
 Zatwierdź zdarzenia nie są obsługiwane. Wywoływanie metody zaleceniem te zdarzenia powoduje, że metoda zwraca kod błędu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Nie będzie wyzwalać podczas wykonywania metody Commit(). Zamiast tego one wyzwalać dla każdej zmiany tekstu.  
  
#### <a name="text-markers"></a>Znacznikach tekstu  
 Należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> obiektów po ich usunięciu. W poprzednich wersjach potrzebne tylko do wersji znaczników.  
  
#### <a name="line-numbers"></a>Numery wiersza  
 Dla różnych metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, numery wierszy odpowiadają podstawowej numery wierszy buforu, nie liczbami współczynnik w obramowanie i zawijanie, jak w programie Visual Studio 2008.  
  
 Metody, których to dotyczy obejmują poniżej (lista nie jest wyczerpująca):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Tworzenie konspektu  
 Klienci z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> zostanie wyświetlony tylko tych regionów zwijania, które zostały dodane przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Nie zobaczą ad hoc regionach, ponieważ nie są one dodawane za pośrednictwem karty edytora. Podobnie w tych klientów zwijania regiony dodane przez języków (w tym C# i C++), które są za pomocą nowego kodu z edytora zamiast kart edytor nie będą widoczne.  
  
#### <a name="line-heights"></a>Wysokość wiersza  
 W edytorze nowe wiersze tekstu może mieć różną wysokość, w zależności od rozmiaru czcionki i transformacje możliwe wiersza, łączące wiersza względem innych wierszy. Wysokość wiersza zwracane przez metody takie jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> jest wysokość wiersza z nie transformacji wiersza zastosowanych przy użyciu domyślny rozmiar czcionki. Wysokość tego mogą lub nie mogą uwzględniać rzeczywista wysokość wiersza w widoku.  
  
#### <a name="eventing-and-undo"></a>Obsługi zdarzeń i Cofnij  
 W edytorze nowy widok kontynuuje wykonywanie operacji takich jak renderowania i wywoływanie zdarzeń, nawet wtedy, gdy klaster cofania jest otwarty. To zachowanie różni się od tego starszego widoków, które nie wykonał te operacje dopiero po upływie klastra cofania.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Metoda zakończy się niepowodzeniem w przypadku przekazania w klasie, który nie implementuje albo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Niestandardowych okienek rysowanych przez właściciela Win32 nie są już obsługiwane.  
  
#### <a name="smarttags"></a>Tagi inteligentne  
 Nie obsługuje karty tagów inteligentnych utworzone za pomocą, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfejsów.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch>nie jest zaimplementowana.  
  
## <a name="unimplemented-methods"></a>Niezaimplementowana metody  
 Niektóre metody nie zostały wdrożone na karcie buforu tekstu, karty widoku tekstu i karty warstwy tekstu.  
  
|Interface|Nie zaimplementowano|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)`nie jest zaimplementowana.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A>jest zaimplementowana w kartach sieciowych, ale została zignorowana przez zwijania interfejsu użytkownika.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A>jest zaimplementowana w kartach sieciowych, ale została zignorowana przez zwijania interfejsu użytkownika.|