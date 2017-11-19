---
title: "Wskazówki: Dodawanie funkcji do edytora niestandardowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df3621d87ae80c0eee105183edbc97a4e7ade62f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Wskazówki: Dodawanie funkcji do edytora niestandardowego
Po utworzeniu niestandardowego edytora, można dodać więcej funkcji do niego.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Aby utworzyć Edytor pakiet VSPackage  
  
1.  Tworzenie niestandardowego edytora za pomocą szablonu projektu pakietu Visual Studio.  
  
     Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie edytora niestandardowego](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Zdecyduj, czy chcesz edytora do obsługi widoku jednego lub wielu widoków.  
  
     Edytor, który obsługuje **nowe okno** polecenia lub widoku formularza i widoku kodu, wymaga innego dokumentu obiekty danych i Widok dokumentu. W edytorze, który obsługuje tylko jeden widok można zaimplementować obiekt danych dokumentu i obiekt widoku dokumentu na tym samym obiekcie.  
  
     Na przykład wiele widoków zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
3.  Wdrożenie fabryki edytora zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfejsu.  
  
     Aby uzyskać więcej informacji, zobacz [fabryki edytora](../extensibility/editor-factories.md).  
  
4.  Zdecydować, czy mają edytora na potrzeby używania aktywacji w miejscu, czy uproszczone osadzanie do zarządzania okna obiektu widoku dokumentu.  
  
     Uproszczony osadzania okna edytora obsługuje widoku standardowego dokumentu, gdy okno edytora Aktywacja w miejscu obsługuje formantu ActiveX lub innych aktywnego obiektu jako jego widok dokumentu. Aby uzyskać więcej informacji, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md) i [Aktywacja w miejscu](../extensibility/in-place-activation.md).  
  
5.  Implementowanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs do obsługi poleceń.  
  
6.  Zawierają trwałości dokumentów oraz odpowiedzi na zmiany pliku zewnętrznego, wykonując następujące czynności:  
  
    1.  Aby utrwalić pliku, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> na obiekt danych dokumentu w edytorze.  
  
    2.  Aby reagowania na zmiany pliku zewnętrznego, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> na obiekt danych dokumentu w edytorze.  
  
        > [!NOTE]
        >  Wywołanie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> uzyskać wskaźnik do `IVsFileChangeEx`.  
  
7.  Koordynowanie zdarzeń Edycja dokumentów z kontroli kodu źródłowego. W tym celu:  
  
    1.  Wskaźnik do uzyskania `IVsQueryEditQuerySave2` przez wywołanie metody `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  W przypadku pierwszego zdarzenia edycji wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody.  
  
         To monituje użytkownika o wyewidencjonować plik, jeśli go nie został już wyewidencjonowany. Pamiętaj obsłużyć warunek "pliku nie jest wyewidencjonowany" w celu uniknięcia błędów  
  
    3.  Podobnie, przed zapisaniem pliku, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metody.  
  
         Ta metoda monituje użytkownika o Zapisz plik, jeśli nie zostały zapisane lub został zmieniony od ostatniego zapisu.  
  
8.  Włącz **właściwości** okno, aby wyświetlić właściwości dla tekstu zaznaczonego w edytorze. W tym celu:  
  
    1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> każdego zaznaczonego tekstu czasu zmiany przekazywanie w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Wywołanie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> usługi do uzyskiwania wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Umożliwianie użytkownikom przeciąganie i upuszczanie elementów między edytora i **przybornika**, lub między edytory zewnętrzne (na przykład Microsoft Word) i **przybornika**. W tym celu:  
  
    1.  Implementowanie `IDropTarget` na edytora do alertów IDE, że edytor jest miejsca docelowego.  
  
    2.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfejsu w widoku, dlatego edytor można włączać i wyłączać elementów w **przybornika**.  
  
    3.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> i Wywołaj `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> usługi do uzyskiwania wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfejsów.  
  
         Dzięki temu VSPackage do dodawania nowych elementów do **przybornika**.  
  
10. Zdecyduj, czy mają inne funkcje opcjonalne tego edytora.  
  
    -   Jeśli chcesz edytora do obsługi Znajdź i Zamień poleceń, wdrożenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Jeśli chcesz użyć narzędzia okno konspektu dokumentu w edytorze, zaimplementować `IVsDocOutlineProvider`.  
  
    -   Aby użyć paska stanu w edytorze, należy wdrożyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> i Wywołaj `QueryService` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> uzyskać wskaźnik do `IVsStatusBar`.  
  
         Na przykład edytor można wyświetlić linii / informacji o kolumnie, tryb zaznaczania (strumienia / polu) i tryb wstawiania (Wstaw / nakładanie).  
  
    -   Jeśli chcesz, aby edytora do obsługi `Undo` polecenia zalecaną metodą jest używany model menedżera cofania OLE. Alternatywnie, można mieć dojście edytor `Undo` polecenia bezpośrednio.  
  
11. Utwórz rejestru informacje, w tym identyfikatory GUID dla pakiet VSPackage, menu edytora i innych funkcji.  
  
     Oto przykładowy kod, aby przełączyć w pliku .rgs skryptu pokazują, jak zarejestrować prawidłowo edytora.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implementuje Obsługa pomocy kontekstowej.  
  
     Dzięki temu można zapewnić obsługę pomocy F1 i okna Pomoc dynamiczna dla elementów w edytorze. Aby uzyskać więcej informacji o tym, zobacz [porady: Podaj kontekst dla edytory](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Ujawnia Model obiektowy automatyzacji z edytora zaimplementowanie `IDispatch` interfejsu.  
  
     Aby uzyskać więcej informacji, zobacz [Współtworzenie Model automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   Jest tworzone wystąpienie edytor, gdy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. Jeśli Edytor obsługuje wiele widoków, `CreateEditorInstance` tworzy zarówno dane dokumentu i obiekty widoku dokumentu. Jeśli obiekt danych dokumentu jest już otworzyć, inną niż null `punkDocDataExisting` wartość jest przekazywana do `IVsEditorFactory::CreateEditorInstance`. Wdrożenie fabryki edytora musi ustalić, czy istniejący obiekt danych dokumentu jest zgodne przez wysyłanie zapytań do odpowiednich interfejsów na nim. Aby uzyskać więcej informacji, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
-   Użycie metoda osadzania uproszczona zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu.  
  
-   Jeśli zdecydujesz się używać aktywacji w miejscu, należy zaimplementować następujących interfejsów:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` Interfejs jest używany w celu uniknięcia scalania menu OLE 2.  
  
     Twoje `IOleCommandTarget` implementacji obsługi poleceń, takich jak **Wytnij**, **kopiowania**, i **Wklej**. Podczas implementowania `IOleCommandTarget`, zdecyduj, czy edytor wymaga własnego pliku vsct, aby zdefiniować własny struktury menu polecenie lub jeśli można zaimplementować standardowych poleceń zdefiniowanych przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zazwyczaj edytory użycia i rozszerzyć menu IDE i definiować własne paski narzędzi. Jednak często jest niezbędna dla edytora do zdefiniowania własnych określonych poleceń oprócz przy użyciu zestawu poleceń standardowych IDE. Aby to zrobić, w edytorze należy zadeklarować standardowych poleceń wykorzystuje, a następnie zdefiniuj w pliku vsct nowego polecenia, menu kontekstowe, najwyższego poziomu menu i pasków narzędzi. Aktywacja w miejscu utworzyć edytora, następnie należy wdrożyć <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i zdefiniuj menu i pasków narzędzi edytora w pliku vsct, a nie za pomocą scalania menu OLE 2.  
  
-   Aby zapobiec polecenie stłoczenie w interfejsie użytkownika, należy używać istniejących poleceń w IDE przed inventing nowych poleceń. Polecenia udostępnionego są definiowane w SharedCmdDef.vsct i ShellCmdDef.vsct. Te pliki są instalowane domyślnie w podkatalogu VisualStudioIntegration\Common\Inc Twojego [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalacji.  
  
-   `ISelectionContainer`można wyrazić zarówno pojedynczych i wielu opcji. Każdy wybrany obiekt jest zaimplementowany jako `IDispatch` obiektu.  
  
-   Implementuje IDE `IOleUndoManager` jako dostępny z usługą <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> lub jako obiekt, który można wdrożyć za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementuje z edytora `IOleUndoUnit` interfejsu dla każdego `Undo` akcji.  
  
-   Istnieją dwa miejsca niestandardowego edytora mogą uwidaczniać obiekty automatyzacji:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Zobacz też  
 [Współtworzenie Model automatyzacji](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Porady: Podaj kontekstu edytorów](../extensibility/how-to-provide-context-for-editors.md)