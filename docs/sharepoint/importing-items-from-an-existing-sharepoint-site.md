---
title: "Importowanie elementów z istniejącej witryny SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
ms.assetid: b1012eb8-5927-4522-9475-72f0ba55fcca
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6dbfc2fd214d11eac8a9615c95d3f3ec6e6f3efa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="importing-items-from-an-existing-sharepoint-site"></a>Importowanie elementów z istniejącej witryny SharePoint
  Importowanie pakietu rozwiązań SharePoint szablon projektu umożliwia ponowne użycie elementów, takich jak pola z istniejących witryn programu SharePoint i typy zawartości w ramach nowego [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązania programu SharePoint. Mimo że można uruchomić najbardziej importowanych rozwiązań bez żadnych modyfikacji, brak pewnych ograniczeń i zagadnień do uwzględnienia, zwłaszcza, jeśli można modyfikować po zaimportowaniu ich elementów.  
  
> [!NOTE]  
>  Aby zaimportować przepływy pracy wielokrotnego użytku, należy użyć szablonu projektu importowania przepływu pracy wielokrotnego użytku. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Wytyczne dotyczące importowania wielokrotnych przepływów danych](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Rozwiązań SharePoint obsługiwane  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]Importowanie rozwiązania utworzone w w pełni obsługuje [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]nie obsługuje importowania rozwiązań utworzonych w następujących aplikacji:  
  
-   [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
-   [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
-   [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
-   Microsoft SharePoint Designer 2007  
  
-   [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
 Mimo że można często pomyślnie zaimportować rozwiązania utworzone przez te aplikacje, funkcja jest nie przetestowane i nie jest obsługiwane.  
  
## <a name="item-import-restrictions"></a>Ograniczenia importu elementu  
 Mimo że większość SharePoint — elementy mogą zostać zaimportowane z istniejącego pliku wsp, następujące elementy nie są obsługiwane i mogą wymagać modyfikacji działał prawidłowo:  
  
-   Jednostki usługi łączności danych biznesowych  
  
-   Kod elementy skojarzenia przepływu pracy  
  
-   Przepływy pracy kodu  
  
-   Visual części sieci Web (.ascx)  
  
-   Usługi sieci Web (.asmx)  
  
-   Typ zawartości powiązania  
  
-   Odbiorcy zdarzeń  
  
-   Definicje list (szablonów)  
  
-   Definicje witryny  
  
 Podczas eksportowania rozwiązania z [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], te elementy są automatycznie usuwane z pliku wsp. Jednak inne pliki WSP wygenerowane z nieobsługiwaną narzędzi może zawierać tych elementów. (Wcześniej w tym temacie, zobacz "Obsługiwane rozwiązań programu SharePoint").  
  
## <a name="what-happens-when-you-import-a-solution"></a>Co się stanie po zaimportowaniu rozwiązania  
 Po zaimportowaniu rozwiązania przy użyciu szablonu Importowanie pakietu rozwiązania SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiuje całą zawartość pliku wsp i próbuje uzgodnienia i zachować tyle skojarzenia i odwołania między importowanych elementów i plików, jak to możliwe.  
  
 Kopiowanie wszystkich importowanych elementów do odpowiednich folderów w **Eksploratora rozwiązań**. Na przykład typy zawartości są wyświetlane w folderze **typy zawartości** i wystąpienia listy są wyświetlane w obszarze **listę wystąpień**. Pliki skojarzone z importowany element są również kopiowane do folderu elementu. Na przykład wystąpienie listy importowanych zawiera jego modułów, formularzy i strony ASPX.  
  
### <a name="dependent-items"></a>Elementy zależne  
 W przypadku wybrania elementu w Kreatorze Importowanie pakietu rozwiązań programu SharePoint, ale nie jej elementów zależnych okno komunikatu informujące o tym, że elementy zależne należy także wybrać przed zaimportowaniem.  
  
### <a name="what-are-features"></a>Jakie są funkcje?  
 Program SharePoint Designer użytkownicy mogą zobaczyć nieoczekiwany plikach o nazwie *funkcje*, pojawiają się w swoich rozwiązaniach importowanych w **Eksploratora rozwiązań.** Chociaż funkcje były dostępne w programie SharePoint Designer rozwiązania, zostały one ukrytych z widoku. Funkcje są teraz widoczne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Funkcje są kontenerami dla pozycji programu SharePoint. Każdej funkcji przechowuje odwołanie do każdego elementu, takie jak typy zawartości i definicje list, które zawiera. Po zaimportowaniu rozwiązania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] konfiguruje funkcji dla wszystkich importowanych elementów i próbuje zachować relacje element funkcji dla plików. Wszystkie pliki, których odwołania nie można rozpoznać są umieszczane **inne pliki zaimportowane** folderu.  
  
 Aby uzyskać więcej informacji o funkcjach, zobacz [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md) i [pracy z funkcjami](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handling-special-cases"></a>Obsługa szczególnych przypadkach.  
 W niektórych przypadkach program Visual Studio nie można uzgodnić element z jego plików zależnych. Wszelkie pliki [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie można rozpoznać pojawiają się w folderze **inne pliki zaimportowane**. Ponadto ich **DeploymentType** właściwości są ustawione na **NoDeployment** tak, aby nie są wdrażane z rozwiązaniem.  
  
 Na przykład po zaimportowaniu definicji listy ExpenseForms definicji listy o tej nazwie jest wyświetlany w obszarze **listy definicji** folderu w **Eksploratora rozwiązań** wraz z jego Elements.xml i Pliki Schema.XML. Jednak jego powiązanych formularzy ASPX, jak i HTML może być umieszczany w folderze o nazwie **ExpenseForms** w obszarze **inne pliki zaimportowane** folderu. Aby ukończyć importowania, przenosić tych plików w obszarze definicji listy ExpenseForms w **Eksploratora rozwiązań** i zmienić **DeploymentType** właściwości dla każdego pliku z **NoDeployment** do **ElementFile**.  
  
 Podczas importowania odbiorcy zdarzeń, plik Elements.xml jest kopiowany do poprawnej lokalizacji, ale należy ręcznie dołączyć zestawu w pakiecie rozwiązań, dzięki którym wdrażania z rozwiązaniem. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)]jak to zrobić, zobacz [porady: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Podczas importowania przepływy pracy, formularzy programu InfoPath są kopiowane do **inne pliki zaimportowane** folderu. Jeśli plik wsp zawiera szablon sieci Web, jest ona ustawiona jako strony początkowej w **Eksploratora rozwiązań**.  
  
## <a name="importing-fields-and-property-bags"></a>Importowanie pól i zbiory właściwości  
 Po zaimportowaniu rozwiązania, które ma wiele pól, wszystkie definicje oddzielne pola są scalane w pojedynczy plik Elements.xml w węźle **Eksploratora rozwiązań** o nazwie **pola**. Podobnie, wszystkie wpisy w zbiorze właściwości są scalane w pliku Elements.xml pod węzeł o nazwie **PropertyBags**.  
  
 Pola w programie SharePoint są kolumny typu określone dane, takie jak tekst, Boolean lub wyszukiwania. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: kolumny i typy pól](http://go.microsoft.com/fwlink/?LinkId=182304). Zbiory właściwości umożliwiają dodanie właściwości do obiektów w programie SharePoint, wszystkie elementy z listy w witrynie programu SharePoint do farmy. Zbiory właściwości są zaimplementowane jako tablicy skrótów nazw właściwości i wartości. Aby uzyskać więcej informacji, zobacz [Zarządzanie konfiguracją programu SharePoint](http://go.microsoft.com/fwlink/?LinkId=182296) lub [ustawienia w zbiorze właściwości SharePoint](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="deleting-items-in-the-project"></a>Usuwanie elementów projektu  
 Większość elementów rozwiązań SharePoint mieć jeden lub więcej elementów zależnych. Na przykład wystąpienia listy zależą od typów zawartości i typy zawartości są zależne od pól. Po zaimportowaniu rozwiązania programu SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie powiadamia użytkownika o wszystkich problemach odwołanie usunięcie elementu w rozwiązaniu, ale nie elementów zależnych, dopóki przystąpieniem do wdrożenia rozwiązania. Na przykład jeśli importowany rozwiązanie ma wystąpienia listy, która zależy od typu zawartości i usunąć tego typu zawartości, na wdrożenie może wystąpić błąd. Ten błąd występuje, jeśli elementu zależnego nie jest zainstalowana na serwerze programu SharePoint. Podobnie jeśli usunięty element ma również zbiór właściwości powiązane, następnie usunąć te wpisy w zbiorze właściwości z **PropertyBags** Elements.xml pliku. W związku z tym jeśli występują błędy wdrożenia należy usunąć wszystkie elementy z importowanych rozwiązania, sprawdź wszystkie elementy zależne muszą również zostaną usunięte.  
  
## <a name="restoring-missing-feature-attributes"></a>Przywracanie brakujące atrybuty funkcji  
 Podczas importowania rozwiązań, niektóre atrybuty opcjonalna funkcja zostały pominięte w manifeście importowanych funkcji. Jeśli chcesz przywrócić te atrybuty w nowym pliku funkcji, zidentyfikuj brakujące atrybuty porównując oryginalnego pliku funkcji do manifestu nowych funkcji i postępuj zgodnie z instrukcjami w temacie [porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Wykrywanie konfliktów wdrożenia nie jest wykonywana na wystąpienia listy wbudowanych  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]nie przeprowadza wykrywanie konfliktów wdrożenia wystąpienia listy wbudowanych (to znaczy domyślnego wystąpienia listy dostarczanych z programem SharePoint). Aby uniknąć zastępowania wystąpienia listy wbudowanych w programie SharePoint odbywa się nie wykonuje wykrywania konfliktów. Listę wbudowanych, którą wystąpienia są nadal wdrożonych aktualizacji, ale są nigdy nie usunięto lub zastąpione. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="importing-sharepoint-server-2010-workflows"></a>Importowanie przepływów pracy programu SharePoint Server 2010  
 W przypadku zaimportowania przepływ pracy utworzony w [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], nie będzie działał prawidłowo po jej wdrożeniu. Przepływ pracy nie działa poprawnie, ponieważ brakuje niektórych zestawów i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] przepływy pracy zawierają InfoPath forms, które nie są obecnie obsługiwane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązań przepływu pracy. Jednak zaimportować [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] przepływów pracy może również działać prawidłowo po zmianie niektóre elementy, takie jak dodanie odwołania do [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] zestawów i ponowne łączenie formularzy programu InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Importowanie przepływów pracy programu SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Za długa nazwa elementu  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ma limit 260 znaków całkowita dla projektu i nazw elementów projektu, łącznie ze ścieżką. Podczas importowania rozwiązanie, jeśli nazwa elementu przekracza ten limit, jest komunikat o błędzie:  
  
 **Określona ścieżka i nazwa pliku jest zbyt długa. W pełni kwalifikowanej nazwy pliku musi być mniejsza niż 260 znaków, a nazwa katalogu musi być mniejsza niż 248 znaków.**  
  
 Element nie jest tworzony, gdy ten błąd. Ten problem występuje najczęściej z zaimportowanych modułów. Aby uniknąć tego problemu, wykonaj następujące czynności:  
  
-   Użyj krótkie nazwy projektu, wprowadzając je w **Dodawanie nowego projektu** okno dialogowe.  
  
-   Tworzenie projektu w lokalizacji co bliski folderu głównego, jak to możliwe, aby skrócić ścieżkę.  
  
## <a name="the-sharepointproductversion-attribute"></a>Atrybut SharePointProductVersion  
 Po zaimportowaniu rozwiązania utworzone we wcześniejszej wersji programu SharePoint, takich jak [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], zmień wartość atrybutu SharePointProductVersion w manifeście pakietu na 12.0, albo Wstaw kontrolki Menedżera skryptów do wszystkich importowanych aplikacji sieci Web strony i pozostaw SharePointProductVersion ustawioną 14.0. W przeciwnym razie importowanych formularzy sieci Web nie będą wyświetlane w programie SharePoint.  
  
### <a name="background"></a>Tło  
 Rozwiązania w [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] obejmują atrybutu o nazwie SharePointProductVersion. SharePoint używa tego atrybutu w jego manifestach pakietu można ustalić wersji rozwiązanie jest przeznaczone dla programu SharePoint. Dwa prawidłowe wartości to 12.0 i 14.0. Wartość 12.0 wskazuje, że element jest przeznaczony dla [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; wartość 14.0 wskazuje, że element jest przeznaczony dla [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Aby zwiększyć bezpieczeństwo podczas renderowania strony ASPX [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] wymagają, aby wszystkie ASPX lub stron wzorcowych zawierał kontrolki Menedżera skryptów. Aby uzyskać więcej informacji o Menedżerze skryptu, zobacz [informacje o formancie ScriptManager](http://go.microsoft.com/fwlink/?LinkID=169399). Ponieważ kontrolki Menedżera skryptów nie jest dostępna w [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] i [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], jeden musi zostać dodany do dowolnego [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] strony, który jest uaktualniany do [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Strony ASPX, które używają standardowych strony wzorcowej nie wymagają kontrolki Menedżera skryptów, ponieważ jeden już została dodana do standardowej strony wzorcowej. Jednak ASPX stron, które nie korzystają z strony wzorcowej lub wykorzystujące niestandardowej strony wzorcowej należy dodać formantu skryptu do pracy [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Brak kontrolki Menedżera skryptów może to stanowić problem podczas importowania [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projektu do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], ponieważ atrybut SharePointProductVersion wszystkich nowych projektów ustawiono 14.0. W przypadku wdrożenia uaktualnionym projekcie zawierający formularz sieci Web bez Menedżer skryptów, formularz nie będą wyświetlane w programie SharePoint.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Wytyczne dotyczące importowania wielokrotnych przepływów danych](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [Wskazówki: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Instrukcje: Dodawanie istniejącego modelu BDC do projektu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
  
  