---
title: "Pola okna właściwości i interfejsy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1f238cceb189723e3ec10fbf8db4abbd9675ae21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Pola okna właściwości i interfejsów
Model do wyboru ustalić, jakie informacje są wyświetlane w **właściwości** okna opiera się na okna z fokusem w IDE. Każdy okna, a obiekt w oknie wybranego może mieć jego zaznaczenie obiekt kontekstu do kontekst zaznaczenia globalnych. Środowiska aktualizuje kontekst zaznaczenia globalne wartościami z ramkę okna, gdy okno ma fokus. Gdy fokus się zmieni, co powoduje kontekst zaznaczenia.  
  
## <a name="tracking-selection-in-the-ide"></a>Śledzenie zaznaczenia w środowisku IDE  
 Ramki okna lub witryn, należących do środowiska IDE ma usługi o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. W poniższej procedurze pokazano sposób zmiany w wyborze, spowodowane przez użytkownika albo zmiana fokusu do innego okna lub wybraniu elementu innego projektu w **Eksploratora rozwiązań**, jest zaimplementowana, aby zmienić zawartość wyświetlaną w  **Właściwości** okna.  
  
1.  Obiekt utworzony przez VSPackage, który jest zlokalizowany w wywołaniach wybrany przedział <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> mają <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> wywołania <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Kontener wyboru udostępnione przez wybrany przedział tworzy własne <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektu. Podczas zmiany wyboru pakiet VSPackage wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> o dowolnym w środowisku, w tym **właściwości** okno o zmianie. Umożliwia także dostęp do elementu i hierarchii informacje dotyczące nowego zaznaczenia.  
  
3.  Wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie jej elementy wybranej hierarchii `VSHPROPID_BrowseObject` wypełnia parametru <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektu.  
  
4.  Obiekt pochodną [interfejsu IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) są zwracane do <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> dla żądanego elementu, a środowisko opakowuje go do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (patrz następny krok). Jeśli połączenie nie powiedzie się, środowisko nawiązuje połączenie drugi `IVsHierarchy::GetProperty`, przekazanie jej przez kontener wyboru <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> podać hierarchii element lub elementy.  
  
     Projektu nie tworzy pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ponieważ okno dostarczone przez środowisko pakiet VSPackage, który zawiera go (na przykład **Eksploratora rozwiązań**) tworzy <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jej imieniu.  
  
5.  Środowisko wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> można pobrać obiektów na podstawie `IDispatch` interfejsu, aby wypełnić **właściwości** okna.  
  
 Jeśli wartość w **właściwości** okno zostanie zmieniona, implementować VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` i `IVsTrackSelectionEx::OnSelectionChangeEx` zgłosić zmiany wartości elementu. Następnie wywołuje środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> lub <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Aby zachować informacje wyświetlane w **właściwości** okna synchronizowane z wartości właściwości. Aby uzyskać więcej informacji, zobacz [aktualizacji wartości właściwości w oknie właściwości](#updating-property-values-in-the-properties-window).  
  
 Oprócz wybranie innego elementu projektu w **Eksploratora rozwiązań** do wyświetlania właściwości powiązanych z tym elementem, można także różne obiekty z okna formularza lub dokumentu za pomocą listy rozwijanej dostępnych na **Właściwości** okna. Aby uzyskać więcej informacji, zobacz [listy obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md).  
  
 Można zmienić sposób wyświetlania informacji w **właściwości** okna siatkę z alfabetyczną podzielone na kategorie, i, jeśli jest dostępny, można także otworzyć stronę właściwości dla wybranego obiektu, klikając odpowiednie przyciski na  **Właściwości** okna. Aby uzyskać więcej informacji, zobacz [przycisków w oknie właściwości](../../extensibility/internals/properties-window-buttons.md) i [strony właściwości](../../extensibility/internals/property-pages.md).  
  
 Na koniec dołu **właściwości** okno zawiera również opis wybranym w polu **właściwości** okna siatki. Aby uzyskać więcej informacji, zobacz [pobierania opisy pola w oknie właściwości](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a>Aktualizowanie właściwości wartości w oknie właściwości
Istnieją dwa sposoby, aby zachować **właściwości** okna zsynchronizowane z zmiany wartości właściwości. Pierwsza to wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejs, który zapewnia dostęp do funkcji podstawowych okien, w tym dostęp do grupy i utworzenia systemu windows narzędzia i zarządzania dokumentami udostępniane przez środowisko. W poniższych krokach opisano ten proces synchronizacji.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości przy użyciu IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości przy użyciu interfejsu IVsUIShell  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi) wtedy tego VSPackages projektów, lub edytory muszą tworzyć ani wyliczyć windows narzędzia lub dokumentu.  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> do zachowania **właściwości** okna synchronizację ze zmianami właściwości projektu (lub inny wybrany obiekt przeglądanie przez **właściwości** okna) bez stosowania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i uruchamiania <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> zdarzenia.  
  
3.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> ustanowienie i wyłączyć, odpowiednio, powiadomienie klienta zdarzeń hierarchii bez konieczności hierarchii do zaimplementowania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości przy użyciu elementu IConnection  
 Drugim sposobem utrzymywania **właściwości** okna zsynchronizowane z zmiany wartości właściwości jest zaimplementowanie `IConnection` składnika obiektu do wskazują na istnienie wychodzących interfejsów. Jeśli chcesz zlokalizować nazwę właściwości, pochodzi z obiektu <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Implementacji można zmodyfikować deskryptorów właściwości zwraca i zmienić nazwę właściwości. Do zlokalizowania opis, utworzyć atrybutu, który jest pochodną <xref:System.ComponentModel.DescriptionAttribute> i zastąpienie właściwości Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Zagadnienia w przypadku implementowania interfejsu IConnection  
  
1.  `IConnection`zapewnia dostęp do modułu wyliczającego obiektu podrzędnego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. Umożliwia również dostęp do wszystkich połączeń punkt podrzędnych obiektów, każdy z zaimplementowanym <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu.  
  
2.  Dowolny obiekt przeglądania jest odpowiedzialny za wdrażanie <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> zdarzeń. **Właściwości** okna poda dla zdarzenia ustawiana za pośrednictwem `IConnection`.  
  
3.  Punkt połączenia określa liczbę połączeń (jeden lub więcej) umożliwia jego wykonywania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Punkt połączenia, który umożliwia tylko jeden interfejs może zwracać <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.  
  
4.  Klient może wywołać `IConnection` interfejs do uzyskania dostępu do modułu wyliczającego obiektu podrzędnego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Następnie można wywołać interfejsu wyliczyć punkty połączenia dla każdego interfejsu wychodzącego identyfikator (IID).  
  
5.  `IConnection`również można wywołać w celu uzyskania dostępu do obiektów podrzędnych punktu połączenia z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs dla każdego IID wychodzących. Za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu, klient rozpoczyna się lub kończy advisory pętli z obiektu składnika i synchronizacji przez klienta. Klient może także wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu, aby uzyskać obiekt enumerator z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfejsu wyliczyć połączeń, które bez informacji o.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>Pobieranie opisy pola w oknie właściwości
W dolnej części **właściwości** , obszar opisu wyświetlane są informacje powiązane z polem wybranej właściwości. Ta funkcja jest włączona domyślnie. Jeśli chcesz ukryć pola Opis, kliknij prawym przyciskiem myszy **właściwości** i kliknij **opis**. W ten sposób spowoduje również usunięcie znacznik wyboru obok pozycji **opis** tytuł w oknie menu. Wyświetl pole ponownie, wykonując te same kroki, aby przełączyć **opis** ponownie.  
  
 Informacje w polu Opis pochodzą z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Każdej metody, interfejsu, coclass i tak dalej może mieć Niezlokalizowany `helpstring` atrybutu w bibliotece typów. **Właściwości** okna pobiera ciąg, z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Aby określić zlokalizowane ciągi pomocy  
  
1.  Dodaj `helpstringdll` atrybutu w celu wykonania instrukcji biblioteki w bibliotece typów (`typelib`).  
  
    > [!NOTE]
    >  Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku obiektu biblioteki (.olb).  
  
2.  Określ `helpstringcontext` atrybuty dla ciągów. Można również określić `helpstring` atrybutów.  
  
     Te atrybuty różnią się od `helpfile` i `helpcontext` atrybuty, które znajdują się w tematach Pomocy .chm rzeczywisty plik.  
  
 Można pobrać informacji o opis można wyświetlić nazwy właściwości wyróżnione **właściwości** wywołań okna <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> dla wybranej właściwości, określając żądaną `lcid` atrybutu dla ciąg w danych wyjściowych. Wewnętrznie <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> znajduje określony w pliku dll `helpstringdll` atrybutu i wywołania `DLLGetDocumentation` na tego pliku dll, używając określonego kontekstu i `lcid` atrybutu.  
  
 Sygnatura i implementacja `DLLGetDocumentation` są:  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` Funkcja musi być Eksport zdefiniowany w pliku .def dla biblioteki DLL.  
  
 Wewnętrznie plik .olb jest tworzony, która jest rzeczywiście biblioteki DLL. Ta biblioteka DLL zawiera jeden zasób, typu pliku biblioteki (.tlb) i jeden wyeksportowanej funkcji, `DLLGetDocumentation`.  
  
 W przypadku plików .olb `helpstringdll` atrybutu jest opcjonalny, ponieważ jest on tego samego pliku, który zawiera w samym pliku .tlb.  
  
 Można pobrać ciągów wyświetlani w **opisy** okienko, w związku z tym minimum, musisz wykonać jest określ `helpstring` atrybutu w bibliotece typów. Jeśli chcesz, aby te ciągi do lokalizacji, należy określić `helpstringdll` (opcjonalne) atrybutu i `helpstringcontext` atrybut (wymagane) i wdrożenie `DLLGetDocumentation`.  
  
 Nie ma żadnych dodatkowych interfejsów, które muszą zostać zaimplementowane po pierwsze zlokalizowane informacji za pomocą jego idl `helpstringcontext` atrybutu i `DLLGetDocumentation`.  
  
 Innym sposobem uzyskania zlokalizowaną nazwę i opis właściwości jest zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Aby uzyskać więcej informacji dotyczących implementacja tej metody, zobacz [pola okna właściwości i interfejsów](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)