---
title: "Wskazówki: Wywoływanie Client Object Model SharePoint w rozszerzeniu Eksploratora serwera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4b7cc5797643309e7929f455bfcf94db85f90b0b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Wskazówki: wywoływanie Client Object Model SharePoint w rozszerzeniu Eksploratora serwera
  W tym przewodniku pokazano, jak wywoływanie SharePoint client object model z rozszerzeniem dla **połączeń SharePoint** w węźle **Eksploratora serwera**. Aby uzyskać więcej informacji o sposobie używania modelu obiektów klienta programu SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia, rozszerzający **połączeń SharePoint** węzła **Eksploratora serwera** w następujący sposób:  
  
    -   Dodaje rozszerzenie **Galeria składników Web Part** węzła w każdym węźle witryny programu SharePoint **Eksploratora serwera**. Ten nowy węzeł zawiera węzły podrzędne, które reprezentują każdej części sieci Web w galerii składników Web Part w witrynie.  
  
    -   Rozszerzenie definiuje nowego typu węzła, który reprezentuje wystąpienie składnika Web Part. Ten nowy typ węzła stanowi podstawę dla węzłów podrzędnych w nowym **Galeria składników Web Part** węzła. Nowy typ węzła składnika Web Part wyświetla informacje w **właściwości** okna o składnik Web Part, który reprezentuje węzeł.  
  
-   Tworzenie pakietu rozszerzenia serwera Visual Studio (VSIX), aby wdrożyć rozszerzenie.  
  
-   Debugowanie i testowanie rozszerzenia.  
  
> [!NOTE]  
>  Rozszerzenia plików, które możesz utworzyć w tym przewodniku podobny rozszerzenia, które są tworzone w [wskazówki: rozszerzanie Eksploratora serwera do części sieci Web wyświetlaną](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). W modelu obiektów serwera programu SharePoint korzysta z tego przewodnika, ale w tym przewodniku wykonuje te same zadania przy użyciu client object model.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio SDK. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX, aby wdrożyć rozszerzenie. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Przy użyciu SharePoint client object model. Aby uzyskać więcej informacji, zobacz [zarządzane Client Object Model](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Części sieci Web w programie SharePoint. Aby uzyskać więcej informacji, zobacz [przegląd części sieci Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
 W tym przewodniku, należy utworzyć dwa projekty:  
  
-   Do utworzenia pakietu VSIX do wdrażania projektu VSIX **Eksploratora serwera** rozszerzenia.  
  
-   Projektu biblioteki klas, który implementuje **Eksploratora serwera** rozszerzenia.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności**.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
4.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
     Rozszerzeń narzędzi SharePoint wymagają funkcji w tej wersji programu .NET Framework.  
  
5.  Wybierz **projektu VSIX** szablonu.  
  
6.  W **nazwa** wpisz **WebPartNode**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **WebPartNode** projektu do **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **Windows**.  
  
3.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
4.  Na liście szablony projektów, wybierz **biblioteki klas**.  
  
5.  W **nazwa** wprowadź **WebPartNodeExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **WebPartNodeExtension** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
6.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configuring-the-extension-project"></a>Konfigurowanie projekt rozszerzenia  
 Przed przystąpieniem do napisania kod w celu utworzenia rozszerzenia, należy dodać pliki kodu i odwołania do zestawów do projektu i należy zaktualizować domyślnej przestrzeni nazw.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  W **WebPartNodeExtension** projekt, dodaj dwa pliki kodu o nazwach SiteNodeExtension i WebPartNodeTypeProvider.  
  
2.  Otwórz menu skrótów projektu WebPartNodeExtension, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
3.  W **Menedżera odwołań - WebPartNodeExtension** oknie dialogowym wybierz **Framework** węzeł, a następnie zaznacz pola wyboru dla System.ComponentModel.Composition i System.Windows.Forms zestawy.  
  
4.  Wybierz **rozszerzenia** węzła, zaznacz pole wyboru dla każdej z następujących zestawów, a następnie wybierz **OK** przycisk:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Otwórz menu skrótów **WebPartNodeExtension** projektu, a następnie wybierz pozycję **właściwości**.  
  
     **Projektanta projektu** otwiera.  
  
6.  Wybierz **aplikacji** kartę.  
  
7.  W **domyślny obszar nazw** pola (C#) lub **głównej przestrzeni nazw** polu (Visual Basic), wprowadź **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Tworzenie ikon dla nowych węzłów  
 Utwórz dwie ikony dla **Eksploratora serwera** rozszerzenia: ikony dla nowego **Galeria składników Web Part** węzeł i inną ikonę dla każdego składnika Web Part podrzędnym w obszarze **Galeria składników Web Part** węzeł. W dalszej części tego przewodnika będzie pisania kodu, który kojarzy te ikony węzłów.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Aby utworzyć ikony dla węzłów  
  
1.  W **projektanta projektu** dla projektu WebPartNodeExtension wybierz **zasobów** kartę.  
  
2.  Wybierz link **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**  
  
     Visual Studio tworzy plik zasobów i otwarcie go w projektancie.  
  
3.  W górnej części projektanta, wybierz strzałkę na **dodawania zasobów** menu polecenie, a następnie wybierz pozycję **dodać nową ikonę**.  
  
4.  Wprowadź **WebPartsNode** ikony nowej nazwy, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Otwiera nową ikonę w **edytor obrazów**.  
  
5.  Edytuj wersji 16 x 16 ikony, aby projekt, który można łatwo rozpoznać.  
  
6.  Otwórz menu skrótów dla wersji 32 x 32 ikony, a następnie wybierz pozycję **usunąć typ obrazu**.  
  
7.  Powtórz kroki od 3 do 7, aby dodać drugi ikony do projektu zasobów, a nazwa ta ikona **składnika Web Part**.  
  
8.  W **Eksploratora rozwiązań**w **zasobów** folder **WebPartNodeExtension** projektu, wybierz **WebPartsNode.ico**.  
  
9. W **właściwości** okna, otwórz **Akcja kompilacji** listy, a następnie wybierz pozycję **osadzonego zasobu**.  
  
10. Powtórz ostatnie dwa kroki dla **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Dodawanie węzła Galeria składników Web Part do Eksploratora serwera  
 Utwórz klasę, która dodaje nowe **Galeria składników Web Part** węzła do każdego węzła witryny programu SharePoint. Aby dodać nowy węzeł implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu. Implementuje ten interfejs zawsze, gdy chcesz rozszerzyć zachowanie istniejący węzeł w **Eksploratora serwera**, takie jak dodanie nowego węzła podrzędnego do węzła.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Aby dodać węzeł Galeria składników Web Part do Eksploratora serwera  
  
1.  Wklej następujący kod do **SiteNodeExtension** plik kodowy dla **WebPartNodeExtension** projektu.  
  
    > [!NOTE]  
    >  Po dodaniu tego kodu projektu ma błędy kompilacji. Te błędy zniknie po dodaniu kod w kolejnych krokach.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definiowanie typu węzła, który reprezentuje część sieci Web  
 Utwórz klasę, która definiuje nowego typu węzła, który reprezentuje część sieci Web. Visual Studio korzysta z tego nowego typu węzła do wyświetlania węzłów podrzędnych w obszarze **Galeria składników Web Part** węzła. Każdy z tych węzłów podrzędnych reprezentuje jeden składnik Web Part w witrynie programu SharePoint.  
  
 Aby zdefiniować nowego typu węzła implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu. Implementuje ten interfejs umożliwia definiowanie nowego typu węzła w **Eksploratora serwera**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Aby określić typ węzła składnika Web Part  
  
1.  Wklej następujący kod do **WebPartNodeTypeProvider** plik kodowy dla **WebPartNodeExtension** projektu.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym punkcie wskazówki, całego kodu dla **Galeria składników Web Part** węzeł jest teraz w projekcie. Tworzenie **WebPartNodeExtension** projektu, aby upewnić się, że skompilowany bez błędów.  
  
#### <a name="to-build-the-project"></a>Aby skompilować projekt  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **WebPartNodeExtension** projektu, a następnie wybierz pozycję **kompilacji**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Tworzenie pakietu VSIX, aby wdrożyć rozszerzenie  
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX, modyfikując plik Source.Extension.vsixmanifest,a, który jest dołączony do projektu. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-the-vsix-package"></a>Aby skonfigurować pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**w **WebPartNode** otwarciu projektu **source.extension.vsixmanifest** plik w edytorze manifestu.  
  
     Plik Source.Extension.vsixmanifest,a stanowi podstawę dla wszystkich pakietów VSIX wymaga plik extension.vsixmanifest. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **węzła galerii części sieci Web w Eksploratorze serwera**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **dodaje niestandardowego węzła Galeria składników Web Part do węzła połączeń SharePoint w Eksploratorze serwera**.  
  
5.  Na **zasoby** karta edytora, wybierz **nowy** przycisku.  
  
6.  W **Dodaj nowy element zawartości** okna dialogowego, **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **WebPartNodeExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
9. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
10. Upewnij się, że folder wyjściowy kompilacji projektu WebPartNode zawiera teraz WebPartNode.vsix pliku.  
  
     Domyślnie jest folder wyjściowy kompilacji... folder \bin\Debug folder zawierający plik projektu.  
  
## <a name="testing-the-extension"></a>Rozszerzenie testowania  
 Teraz można przystąpić do testowania nowego **Galeria składników Web Part** w węźle **Eksploratora serwera**. Najpierw Rozpocznij debugowanie projektu rozszerzenia w eksperymentalne wystąpienie programu Visual Studio. Następnie użyj nowych **składników Web Part** węzła w eksperymentalne wystąpienie programu Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia  
  
1.  Uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz **WebPartNode** rozwiązania.  
  
2.  W projekcie WebPartNodeExtension Otwórz **SiteNodeExtension** code pliku, a następnie Dodaj punkt przerwania do pierwszych wierszy kodu w `NodeChildrenRequested` i `CreateWebPartNodes` metody.  
  
3.  Wybierz klawisz F5, aby rozpocząć debugowania.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web części galerii węzła rozszerzenie dla serwera Explorer\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestujesz, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenia  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **widoku**, **Eksploratora serwera**.  
  
2.  Sprawdź, czy witryna programu SharePoint, do którego chcesz używać do testowania jest wyświetlany w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**. Jeśli nie ma na liście, wykonaj następujące kroki:  
  
    1.  Otwórz menu skrótów **połączeń SharePoint**, a następnie wybierz pozycję **Dodawanie połączenia**.  
  
    2.  W **Dodawanie połączenia programu SharePoint** okna dialogowego wprowadź adres URL witryny programu SharePoint, do którego chcesz połączyć, a następnie wybierz pozycję **OK** przycisku.  
  
         Aby określić witrynę programu SharePoint na komputerze deweloperskim, wpisz **http://localhost**.  
  
3.  Rozwiń węzeł połączenia lokacji (która wyświetla adres URL witryny), a następnie rozwiń węzeł lokacji podrzędnych (na przykład **witryny zespołu**).  
  
4.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `NodeChildrenRequested` metody, a następnie wybierz klawisz F5, aby kontynuować debugowanie projektu.  
  
5.  W eksperymentalne wystąpienie programu Visual Studio, rozwiń węzeł **Galeria składników Web Part** węzła, który jest wyświetlany w węźle w lokacji najwyższego poziomu.  
  
6.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `CreateWebPartNodes` metody, a następnie wybierz klawisz F5, aby kontynuować debugowanie projektu.  
  
7.  W eksperymentalne wystąpienie programu Visual Studio, sprawdź, czy wszystkie składniki Web Part na podłączonej lokacji są wyświetlane w obszarze **Galeria składników Web Part** w węźle **Eksploratora serwera**.  
  
8.  Otwórz menu skrótów dla składnika Web Part, a następnie wybierz pozycję **właściwości**.  
  
9. W **właściwości** okna, sprawdź, czy są wyświetlane szczegóły dotyczące składnika Web Part.  
  
10. W **Eksploratora serwera**, otwórz menu skrótów dla tego samego składnika Web Part, a następnie wybierz **Wyświetl komunikat**.  
  
     W wyświetlonym oknie komunikatu wybierz **OK** przycisku.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Odinstalowywania rozszerzenia z programu Visual Studio  
 Po zakończeniu testowania rozszerzenia, należy ją odinstalować z programu Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenia  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **węzła galerii części sieci Web w Eksploratorze serwera**, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisku.  
  
4.  Wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
     Element projektu również zostanie odinstalowana.  
  
5.  Zamknij oba wystąpienia programu Visual Studio (eksperymentalne wystąpienie i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie WebPartNode).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)   
 [Tworzenie ikony lub innego obrazu &#40; edytor obrazów dla ikon &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  