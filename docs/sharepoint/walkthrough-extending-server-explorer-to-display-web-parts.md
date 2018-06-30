---
title: 'Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci Web | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b0bbea76c3c63cf562203f9a622acb2a54804bde
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117839"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Wskazówki: Rozszerzanie Eksploratora serwera do wyświetlania elementów sieci web
  W programie Visual Studio, można użyć **połączeń SharePoint** węzła **Eksploratora serwera** Aby wyświetlić składniki w witrynach programu SharePoint. Jednak **Eksploratora serwera** nie są wyświetlane domyślnie niektórych składników. W tym przewodniku będzie można rozszerzyć **Eksploratora serwera** tak, aby Wyświetla Galeria składników Web Part na każdy jest połączony witryny programu SharePoint.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie rozszerzenia programu Visual Studio, która rozszerza **Eksploratora serwera** w następujący sposób:  
  
    -   Dodaje rozszerzenie **Galeria składników Web Part** węzła w każdym węźle witryny programu SharePoint **Eksploratora serwera**. Ten nowy węzeł zawiera węzły podrzędne, które reprezentują każdej części sieci Web w galerii składników Web Part w witrynie.  
  
    -   Rozszerzenie definiuje nowego typu węzła, który reprezentuje wystąpienie składnika Web Part. Ten nowy typ węzła stanowi podstawę dla węzłów podrzędnych w nowym **Galeria składników Web Part** węzła. Nowy typ węzła składnika Web Part wyświetla informacje w **właściwości** okna składnik Web Part, który reprezentuje informacje. Typ węzła zawiera również element menu skrótów niestandardowych, który służy jako punkt początkowy do wykonywania innych zadań, które odnoszą się do składnika Web Part.  
  
-   Utwórz dwa niestandardowych poleceń programu SharePoint, które wywołuje zestawu rozszerzenia. Polecenia SharePoint są metody, które mogą być wywoływane przez zestawy rozszerzenia, aby użyć interfejsów API w modelu obiektów serwera dla programu SharePoint. W tym przewodniku tworzenia poleceń, które pobrać informacji o części sieci Web z lokalnej witryny programu SharePoint na komputerze dewelopera. Aby uzyskać więcej informacji, zobacz [wywołują modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Tworzenie pakietu rozszerzenia serwera Visual Studio (VSIX), aby wdrożyć rozszerzenie.  
  
-   Debugowanie i testowanie rozszerzenia.  
  
> [!NOTE]  
>  Dla alternatywnej wersji tego przewodnika, która używa client object model dla programu SharePoint zamiast jego modelu obiektów serwera, zobacz [wskazówki: wywołują modelu obiektów klienta programu SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio SDK. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrażania elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Za pomocą modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [za pomocą modelu obiektów programu SharePoint Foundation po stronie serwera](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Składniki Web Part w rozwiązań programu SharePoint. Aby uzyskać więcej informacji, zobacz [przegląd części sieci Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Tworzenie projektów
 W tym przewodniku, należy utworzyć trzy projekty:  
  
-   Aby utworzyć pakiet VSIX, aby wdrożyć rozszerzenie projekt VSIX.  
  
-   Projektu biblioteki klas, który implementuje rozszerzenia. Ten projekt musi wskazywać na .NET Framework 4.5.  
  
-   Projektu biblioteki klas, który definiuje niestandardowe polecenia programu SharePoint. Ten projekt muszą wskazywać środowiska.NET Framework 3.5.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **nowy** > **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
4.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
5.  Wybierz **projektu VSIX** szablonu, nazwy projektu **WebPartNode**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartNode** projektu do **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** węzła lub **Visual Basic** węzeł, a następnie wybierz **Windows** węzła.  
  
3.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
4.  Na liście szablony projektów, wybierz **biblioteki klas**, nazwij projekt **WebPartNodeExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartNodeExtension** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Aby utworzyć projekt polecenia SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** węzła lub **Visual Basic** węzeł, a następnie wybierz pozycję **systemu Windows** węzła.  
  
3.  W górnej części okna dialogowego, wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.  
  
4.  Na liście szablony projektów, wybierz **biblioteki klas**, nazwij projekt **WebPartCommands**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **WebPartCommands** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed przystąpieniem do napisania kod w celu utworzenia rozszerzenia, należy dodać pliki kodu i odwołania do zestawów i skonfiguruj ustawienia projektu.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Aby skonfigurować projekt WebPartNodeExtension
  
1.  W projekcie WebPartNodeExtension Dodaj cztery pliki kodu, które mają następujące nazwy:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Otwórz menu skrótów **WebPartNodeExtension** projektu, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
3.  W **Menedżera odwołań - WebPartNodeExtension** oknie dialogowym wybierz **Framework** karcie, a następnie zaznacz pole wyboru dla każdej z następujących zestawów:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Wybierz **rozszerzenia** karcie, zaznacz pole wyboru dla zestawu Microsoft.VisualStudio.SharePoint, a następnie wybierz **OK** przycisku.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów **WebPartNodeExtension** węzła projektu, a następnie wybierz **właściwości**.  
  
     **Projektanta projektu** otwiera.  
  
6.  Wybierz **aplikacji** kartę.  
  
7.  W **domyślny obszar nazw** pola (C#) lub **głównej przestrzeni nazw** pola ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), wprowadź **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Aby skonfigurować projekt webpartcommands
  
1.  W projekcie WebPartCommands Dodaj plik kodu o nazwie WebPartCommands.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów **WebPartCommands** węzła projektu, wybierz **Dodaj**, a następnie wybierz pozycję **istniejący element**.  
  
3.  W **Dodaj istniejący element** okno dialogowe, przejdź do folderu, który zawiera pliki kodu dla projektu WebPartNodeExtension, a następnie wybierz pliki kodu WebPartNodeInfo i WebPartCommandIds.  
  
4.  Wybierz strzałkę obok pozycji **Dodaj** przycisk, a następnie wybierz pozycję **Dodaj jako Link** w wyświetlonym menu.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje pliki kodu do projektu WebPartCommands jako łącza. W związku z tym pliki kodu znajdują się w projekcie WebPartNodeExtension, ale również kompilowane w projekcie WebPartCommands kodu w plikach.  
  
5.  Otwórz menu skrótów **WebPartCommands** ponownie projekt i wybierz polecenie **Dodaj odwołanie**.  
  
6.  W **Menedżera odwołań - WebPartCommands** oknie dialogowym wybierz **rozszerzenia** karcie, zaznacz pole wyboru dla każdej z następujących zestawów, a następnie wybierz **OK** przycisk:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  W **Eksploratora rozwiązań**, otwórz menu skrótów **WebPartCommands** ponownie projekt, a następnie wybierz **właściwości**.  
  
     **Projektanta projektu** otwiera.  
  
8.  Wybierz **aplikacji** kartę.  
  
9. W **domyślny obszar nazw** pola (C#) lub **głównej przestrzeni nazw** pola ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), wprowadź **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Tworzenie ikony dla nowych węzłów
 Utwórz dwie ikony dla **Eksploratora serwera** rozszerzenia: ikony dla nowego **Galeria składników Web Part** węzeł i inną ikonę dla każdego składnika Web Part podrzędnym w obszarze **Galeria składników Web Part** węzeł. W dalszej części tego przewodnika pisania kodu, który kojarzy te ikony węzłów.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Aby utworzyć ikony dla węzłów  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **WebPartNodeExtension** projektu, a następnie wybierz pozycję **właściwości**.  
  
2.  **Projektanta projektu** otwiera.  
  
3.  Wybierz **zasobów** karcie, a następnie wybierz pozycję **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby utworzyć** łącza.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy plik zasobów i otwarcie go w projektancie.  
  
4.  W górnej części projektanta, wybierz strzałkę **dodawania zasobów** menu polecenie, a następnie wybierz pozycję **dodać nową ikonę** w wyświetlonym menu.  
  
5.  W **Dodaj nowy zasób** okno dialogowe, nazwa nową ikonę **WebPartsNode**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Otwiera nową ikonę w **edytor obrazów**.  
  
6.  Edytuj wersji 16 x 16 ikony, aby projekt, który można łatwo rozpoznać.  
  
7.  Otwórz menu skrótów dla wersji 32 x 32 ikony, a następnie wybierz pozycję **usunąć typ obrazu**.  
  
8.  Powtórz kroki od 5 do 8, aby dodać drugi ikony do projektu zasobów, a nazwa ta ikona **składnika Web Part**.  
  
9. W **Eksploratora rozwiązań**w obszarze **zasobów** folder **WebPartNodeExtension** projektu, otwórz menu skrótów **WebPartsNode.ico**.  
  
10. W **właściwości** okna, wybierz strzałkę obok pozycji **Akcja kompilacji**, a następnie wybierz pozycję **osadzonego zasobu** w wyświetlonym menu.  
  
11. Powtórz ostatnie dwa kroki dla **WebPart.ico**.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Dodaj węzeł Galeria składników Web Part do Eksploratora serwera
 Utwórz klasę, która dodaje nowe **Galeria składników Web Part** węzła do każdego węzła witryny programu SharePoint. Aby dodać nowy węzeł implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfejsu. Implementuje ten interfejs zawsze, gdy chcesz rozszerzyć zachowanie istniejący węzeł w **Eksploratora serwera**, takie jak dodanie węzła podrzędnego do węzła.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Aby dodać węzeł Galeria składników Web Part do Eksploratora serwera
  
1.  W projekcie WebPartNodeExtension Otwórz plik kodu SiteNodeExtension, a następnie wklej następujący kod do niego.  
  
    > [!NOTE]  
    >  Po dodaniu tego kodu, projektu mają błędy kompilacji, ale będzie zniknie po dodaniu kod w kolejnych krokach.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Zdefiniuj typ węzła, który reprezentuje składnik web part
 Utwórz klasę, która definiuje nowego typu węzła, który reprezentuje część sieci Web. Visual Studio korzysta z tego nowego typu węzła do wyświetlania węzłów podrzędnych w obszarze **Galeria składników Web Part** węzła. Każdy węzeł podrzędny reprezentuje jeden składnik Web Part w witrynie programu SharePoint.  
  
 Aby zdefiniować nowego typu węzła implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfejsu. Implementuje ten interfejs umożliwia definiowanie nowego typu węzła w **Eksploratora serwera**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Aby określić typ węzła części sieci web
  
1.  W projekcie WebPartNodeExtension Otwórz plik kodu WebPartNodeTypeProvder, a następnie wklej następujący kod do niego.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="define-the-web-part-data-class"></a>Definiowanie klas danych części sieci web
 Definiowanie klasy, która zawiera dane dotyczące pojedynczego składnika Web Part w witrynie programu SharePoint. W dalszej części tego przewodnika spowoduje utworzenie niestandardowego polecenie programu SharePoint, która pobiera dane dotyczące każdej części sieci Web w witrynie, a następnie przypisuje danych do wystąpienia tej klasy.  
  
#### <a name="to-define-the-web-part-data-class"></a>Do definiowania klas danych części sieci web
  
1.  W projekcie WebPartNodeExtension Otwórz plik kodu WebPartNodeInfo, a następnie wklej następujący kod do niego.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="define-the-ids-for-the-sharepoint-commands"></a>Określ identyfikatory poleceń programu SharePoint
 Zdefiniuj kilka ciągów, które identyfikują niestandardowych poleceń programu SharePoint. Te polecenia zostaną zaimplementowane w dalszej części tego przewodnika.  
  
#### <a name="to-define-the-command-ids"></a>Aby zdefiniować identyfikatory poleceń
  
1.  W projekcie WebPartNodeExtension Otwórz plik kodu WebPartCommandIds, a następnie wklej następujący kod do niego.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Tworzenie niestandardowych poleceń programu SharePoint
 Tworzenie niestandardowych poleceń, które wywołują modelu obiektów serwera dla programu SharePoint można pobrać danych dotyczących składników Web Part w witrynie programu SharePoint. Każde polecenie to metoda, która ma <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> zastosować dla niego.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować polecenia SharePoint  
  
1.  W projekcie WebPartCommands Otwórz plik kodu WebPartCommands, a następnie wklej następujący kod do niego.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym punkcie wskazówki, całego kodu dla **Galeria składników Web Part** węzłów i polecenia SharePoint są teraz w projektach. Tworzenie rozwiązania, aby upewnić się, że oba projekty Kompiluj bez błędów.  
  
#### <a name="to-build-the-solution"></a>Tworzenie rozwiązania  
  
1.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
    > [!WARNING]  
    >  W tym momencie projektu WebPartNode mogą mieć błędu kompilacji, ponieważ plik manifestu VSIX nie ma wartości dla autora. Ten błąd zniknie po dodaniu wartości w kolejnych krokach.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Utwórz pakiet VSIX, aby wdrożyć rozszerzenie
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakietu VSIX, modyfikując plik Source.Extension.vsixmanifest,a w projekcie VSIX. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-the-vsix-package"></a>Aby skonfigurować pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**, w ramach projektu WebPartNode Otwórz **source.extension.vsixmanifest** plik w edytorze manifestu.  
  
     Plik Source.Extension.vsixmanifest,a stanowi podstawę dla wszystkich pakietów VSIX wymaga plik extension.vsixmanifest. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **węzła galerii części sieci Web w Eksploratorze serwera**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **dodaje niestandardowego węzła Galeria składników Web Part do węzła połączeń SharePoint w Eksploratorze serwera. To rozszerzenie używa niestandardowego polecenia SharePoint do wywołania w modelu obiektów serwera.**  
  
5.  Wybierz **zasoby** Karta Edytor, a następnie wybierz pozycję **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **WebPartNodeExtension** , a następnie wybierz **OK** przycisku.  
  
9. W edytorze manifestu wybierz **nowy** przycisk ponownie.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
10. W **typu** wprowadź **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Ten element określa rozszerzenie niestandardowe, które chcesz uwzględnić w rozszerzenie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [zasobów — Element (schemat VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu** elementu listy.  
  
12. W **projektu** wybierz **WebPartCommands**, a następnie wybierz pozycję **OK** przycisku.  
  
13. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
14. Upewnij się, że folder wyjściowy kompilacji projektu WebPartNode zawiera teraz WebPartNode.vsix pliku.  
  
     Domyślnie jest folder wyjściowy kompilacji... folder \bin\Debug folder zawierający plik projektu.  
  
## <a name="test-the-extension"></a>Rozszerzenie testu
 Teraz możesz przetestować nową **Galeria składników Web Part** w węźle **Eksploratora serwera**. Najpierw należy uruchomić debugowanie rozszerzenie w eksperymentalne wystąpienie programu Visual Studio. Następnie należy użyć nowego **składników Web Part** węzła w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia  
  
1.  Uruchom ponownie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie WebPartNode.  
  
2.  W projekcie WebPartNodeExtension, otwórz plik kodu SiteNodeExtension, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `NodeChildrenRequested` i `CreateWebPartNodes` metody.  
  
3.  Wybierz **F5** klucza można rozpocząć debugowania.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web części galerii węzła rozszerzenie dla serwera Explorer\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestuje w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenia  
  
1.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **widoku** > **Eksploratora serwera**.  
  
2.  Wykonaj poniższe czynności, jeśli witryna programu SharePoint, do którego chcesz używać do testowania nie są wyświetlane w polu **połączeń SharePoint** w węźle **Eksploratora serwera**:  
  
    1.  W **Eksploratora serwera**, otwórz menu skrótów **połączeń SharePoint**, a następnie wybierz pozycję **Dodawanie połączenia**.  
  
    2.  W **Dodawanie połączenia programu SharePoint** okna dialogowego wprowadź adres URL witryny programu SharePoint, do którego chcesz połączyć, a następnie wybierz pozycję **OK** przycisku.  
  
         Aby określić witrynę programu SharePoint na komputerze deweloperskim, wprowadź **http://localhost**.  
  
3.  Rozwiń węzeł połączenia lokacji (która wyświetla adres URL witryny), a następnie rozwiń węzeł lokacji podrzędnych (na przykład **witryny zespołu**).  
  
4.  Sprawdź, czy kod w wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zatrzymuje punkt przerwania ustawionych wcześniej w `NodeChildrenRequested` metody, a następnie wybierz pozycję **F5** do kontynuowania debugowania projektu.  
  
5.  Eksperymentalne wystąpienie programu Visual Studio, sprawdź, czy nowy węzeł o nazwie **Galeria składników Web Part** pojawia się w węźle lokacji najwyższego poziomu, a następnie rozwiń **Galeria składników Web Part** węzła.  
  
6.  Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawionych wcześniej w `CreateWebPartNodes` metody, a następnie wybierz pozycję **F5** klawisz, aby kontynuować debugowanie projektu.  
  
7.  W eksperymentalne wystąpienie programu Visual Studio, sprawdź, czy wszystkie składniki Web Part na podłączonej lokacji są wyświetlane w obszarze **Galeria składników Web Part** w węźle **Eksploratora serwera**.  
  
8.  W **Eksploratora serwera**, otwórz menu skrótów dla jednej części sieci Web, a następnie wybierz **właściwości**.  
  
9. W wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugowanej, sprawdź, czy szczegóły części sieci Web są wyświetlane w **właściwości** okna.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstaluj rozszerzenie z programu Visual Studio
 Po zakończeniu testowania rozszerzenia, należy odinstalować rozszerzenia z programu Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenia  
  
1.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **rozszerzenia węzła galerii części sieci Web w Eksploratorze serwera**, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** przycisk, aby potwierdzić, że chcesz odinstalować rozszerzenia, a następnie wybierz pozycję **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.  
  
4.  Zamknij oba wystąpienia programu Visual Studio (eksperymentalne wystąpienie i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie WebPartNode).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Wskazówki: Wywołują modelu obiektów klienta programu SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)   
 [Tworzenie ikony lub innego obrazu &#40;edytor obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
