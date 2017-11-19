---
title: "Wskazówki: Rozszerzanie typu elementu projektu SharePoint | Dokumentacja firmy Microsoft"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8afe8ed1d59f8daec34a99b1479079a69a1bc740
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>Wskazówki: rozszerzanie typu elementu projektu SharePoint
  Można użyć **modelu łączności danych biznesowych** element projektu do tworzenia modelu usługi łączności danych biznesowych (BDC) w programie SharePoint. Domyślnie podczas tworzenia modelu przy użyciu tego elementu projektu w modelu danych jest on wyświetlany użytkownikom. Należy także utworzyć listy zewnętrznej w programie SharePoint, aby umożliwić użytkownikom na wyświetlanie danych.  
  
 W tym przewodniku utworzy to rozszerzenie **modelu łączności danych biznesowych** elementu projektu. Deweloperzy mogą używać rozszerzenia do tworzenia listy zewnętrznej w ich projektu, który wyświetla dane w modelu usługi łączności danych biznesowych. W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie rozszerzenia programu Visual Studio, który wykonuje dwie główne zadania:  
  
    -   Generuje on listy zewnętrznej, który wyświetla dane w modelu usługi łączności danych biznesowych. Rozszerzenia używa model obiektów dla systemu projektu SharePoint, aby wygenerować plik Elements.xml, który definiuje listy. Dodane również plik do projektu, aby wraz z modelu BDC jest wdrożona.  
  
    -   Dodaje element menu skrótów do **modelu łączności danych biznesowych** projektu elementów w **Eksploratora rozwiązań**. Deweloperzy mogą kliknij ten element menu, aby wygenerować listy zewnętrznej dla modelu usługi łączności danych biznesowych.  
  
-   Tworzenie pakietu rozszerzenia serwera Visual Studio (VSIX) w celu wdrożenia zestawu rozszerzenia.  
  
-   Testowanie rozszerzenia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje systemu Microsoft Windows, SharePoint i Visual Studio. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym przewodniku zastosowano **projektu VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrażania elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Znajomość następujące pojęcia jest przydatna, ale nie jest to wymagane, aby ukończyć przewodnika:  
  
-   Usługa BDC w [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Aby uzyskać więcej informacji, zobacz [architektura BDC](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   Schemat XML dla modeli usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [infrastruktury modelu BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
 W tym przewodniku, należy utworzyć dwa projekty:  
  
-   Projektu VSIX, aby utworzyć pakiet VSIX do rozszerzenia elementu projektu wdrożenia.  
  
-   Projektu biblioteki klas, który implementuje rozszerzenia elementu projektu.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
4.  Na liście w górnej części **nowy projekt** oknie dialogowym wybierz **.NET Framework 4.5**.  
  
     Rozszerzeń narzędzi SharePoint wymagają funkcji w tej wersji programu .NET Framework.  
  
5.  Wybierz **projektu VSIX** szablonu.  
  
6.  W **nazwa** wprowadź **GenerateExternalDataLists**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **GenerateExternalDataLists** projektu do **Eksploratora rozwiązań**.  
  
7.  Jeśli plik Source.Extension.vsixmanifest,a nie zostanie automatycznie otwarte, otwórz menu skrótów w projekcie GenerateExternalDataLists, a następnie wybierz **Otwórz**  
  
8.  Sprawdź, czy plik Source.Extension.vsixmanifest,a ma wpis niepustych (wprowadź firmy Contoso) dla pól, autora, Zapisz plik, a następnie zamknij go.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **GenerateExternalDataLists** węzła rozwiązania, wybierz **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **Windows** węzła.  
  
3.  Na liście w górnej części okna dialogowego wybierz **.NET Framework 4.5**.  
  
4.  Na liście szablony projektów, wybierz **biblioteki klas**.  
  
5.  W **nazwa** wprowadź **BdcProjectItemExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dodaje **BdcProjectItemExtension** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
6.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configuring-the-extension-project"></a>Konfigurowanie projekt rozszerzenia  
 Przed przystąpieniem do napisania kod w celu utworzenia rozszerzenia elementu projektu, należy dodać pliki kodu i odwołania do zestawów w projekcie rozszerzenia.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  W projekcie BdcProjectItemExtension Dodaj dwa pliki kodu, które mają następujące nazwy:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Wybierz projekt BdcProjectItemExtension, a następnie na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
3.  W obszarze **zestawy** węzła, wybierz **Framework** węzeł, a następnie zaznacz pole wyboru dla każdej z następujących zestawów:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  W obszarze **zestawy** węzła, wybierz **rozszerzenia** węzeł, a następnie zaznacz pole wyboru dla następującego zestawu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Wybierz **OK** przycisku.  
  
## <a name="defining-the-project-item-extension"></a>Definiowanie rozszerzenia elementu projektu  
 Utwórz klasę, która definiuje rozszerzenie **modelu łączności danych biznesowych** elementu projektu. Aby zdefiniować rozszerzenia implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu. Zawsze, gdy chcesz rozszerzyć istniejącego typu elementu projektu, należy zaimplementować ten interfejs.  
  
#### <a name="to-define-the-project-item-extension"></a>Aby zdefiniować rozszerzenia elementu projektu  
  
1.  Wklej następujący kod do pliku kodu ProjectItemExtension.  
  
    > [!NOTE]  
    >  Po dodaniu tego kodu projektu ma błędy kompilacji. Te błędy zniknie po dodaniu kod w kolejnych krokach.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>Tworzenie list danych zewnętrznych  
 Dodaj częściową definicją `GenerateExternalDataListsExtension` klasy, która tworzy listę danych zewnętrznych dla każdej jednostki w modelu usługi łączności danych biznesowych. Aby utworzyć listę danych zewnętrznych, ten kod odczytuje danych jednostki w modelu BDC najpierw za analizowanie danych XML w pliku modelu BDC. Następnie tworzy wystąpienie listy, który jest oparty na modelu BDC i dodaje do projektu tego wystąpienia listy.  
  
#### <a name="to-create-the-external-data-lists"></a>Aby utworzyć listę danych zewnętrznych  
  
1.  Wklej następujący kod do pliku kodu GenerateExternalDataLists.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w prezentacji, całego kodu dla rozszerzenia elementu projektu jest teraz w projekcie. Tworzenie rozwiązania, aby upewnić się, że projekt skompiluje się bez błędów.  
  
#### <a name="to-build-the-solution"></a>Tworzenie rozwiązania  
  
1.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>Tworzenie pakietu VSIX, aby wdrożyć rozszerzenia elementu projektu  
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX, modyfikując plik Source.Extension.vsixmanifest,a, który jest dołączony do projektu VSIX. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i tworzenia pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku source.extension.vsixmanifest w projekcie GenerateExternalDataLists, a następnie wybierz **Otwórz**.  
  
     Visual Studio otwiera plik w edytorze manifestu. Plik Source.Extension.vsixmanifest,a jest podstawą dla pliku extension.vsixmanifest jest wymagany przez wszystkie pakiety VSIX. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **Generator listy danych zewnętrznych**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **rozszerzenie dla elementów projektu modelu łączności danych biznesowych, które mogą służyć do generowania danych zewnętrznych list**.  
  
5.  Na **zasoby** karta edytora, wybierz **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **BdcProjectItemExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
9. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
10. Upewnij się, że projekt kompiluje i tworzy bez błędów.  
  
11. Upewnij się, że folder wyjściowy kompilacji projektu GenerateExternalDataLists zawiera teraz GenerateExternalDataLists.vsix pliku.  
  
     Domyślnie jest folder wyjściowy kompilacji... folder \bin\Debug folder zawierający plik projektu.  
  
## <a name="testing-the-project-item-extension"></a>Testowanie rozszerzenia elementu projektu  
 Teraz można przystąpić do testowania rozszerzenia elementu projektu. Najpierw należy uruchomić debugowanie projektu rozszerzenia w eksperymentalne wystąpienie programu Visual Studio. Następnie można wygenerować listy zewnętrznej dla modelu BDC za pomocą rozszerzenia w eksperymentalne wystąpienie programu Visual Studio. Na koniec Otwórz listy zewnętrznej w witrynie programu SharePoint, aby sprawdzić, czy działa zgodnie z oczekiwaniami.  
  
#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia  
  
1.  Jeśli to konieczne, uruchom ponownie program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie GenerateExternalDataLists.  
  
2.  W projekcie BdcProjectItemExtension, otwórz plik kodu ProjectItemExtension, a następnie Dodaj punkt przerwania do wiersza kodu w `Initialize` metody.  
  
3.  Otwórz plik kodu GenerateExternalDataLists, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `GenerateExternalDataLists_Execute` metody.  
  
4.  Rozpocznij debugowanie, wybierając klawisz F5 lub na pasku menu, wybierając **debugowania**, **Rozpocznij debugowanie**.  
  
     Visual Studio instaluje rozszerzenia %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Generator\1.0 listy danych i rozpoczyna się eksperymentalne wystąpienie programu Visual Studio. Element projektu przetestuje w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Aby przetestować rozszerzenia  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **szablony** węzła, rozwiń węzeł **Visual C#** węzła, rozwiń węzeł **SharePoint** węzeł, a następnie Wybierz **2010**.  
  
3.  Upewnij się, że na liście w górnej części okna dialogowego **.NET Framework 3.5** jest zaznaczone. Projekty dla [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] wymagają tej wersji programu .NET Framework.  
  
4.  Na liście szablony projektów, wybierz **projektu programu SharePoint 2010**.  
  
5.  W **nazwa** wprowadź **SharePointProjectTestBDC**, a następnie wybierz pozycję **OK** przycisku.  
  
6.  W Kreatorze dostosowania programu SharePoint, wprowadź adres URL witryny, która ma być używany na potrzeby debugowania, wybierz **Wdróż jako rozwiązanie farmy**, a następnie wybierz pozycję **Zakończ**przycisku.  
  
7.  Otwórz menu skrótów projektu SharePointProjectTestBDC, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
8.  W **dodać NewItem - SharePointProjectTestBDC** okna dialogowego rozwiń węzeł zainstalowany język, rozwijając **SharePoint** węzła.  
  
9. Wybierz **2010** węzeł, a następnie wybierz pozycję **modelu łączności danych biznesowych (tylko rozwiązanie farmy)** szablonu.  
  
10. W **nazwa** wprowadź **TestBDCModel**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
11. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawiony w `Initialize` metody ProjectItemExtension pliku kodu.  
  
12. Zatrzymano wystąpienie programu Visual Studio, wybierz **F5** klucza, lub na pasku menu wybierz **debugowania**, **Kontynuuj** do kontynuowania debugowania projektu.  
  
13. Eksperymentalne wystąpienie programu Visual Studio, wybierz **F5** klucza, lub na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do tworzenia, wdrażania, a następnie uruchom  **TestBDCModel** projektu.  
  
     Przeglądarki sieci web zostanie otwarty na domyślną stronę witryny programu SharePoint, określony dla debugowania.  
  
14. Sprawdź, czy **wymieniono** sekcji w obszarze Szybkie uruchamianie jeszcze nie zawiera listę, która jest oparta na domyślny model usługi łączności danych biznesowych w projekcie. Należy najpierw utworzyć listę danych zewnętrznych przy użyciu interfejsu użytkownika programu SharePoint lub za pomocą rozszerzenia elementu projektu.  
  
15. Zamknij przeglądarkę sieci web.  
  
16. W wystąpieniu programu Visual Studio, która ma TestBDCModel Otwórz projekt, otwórz menu skrótów **TestBDCModel** w węźle **Eksploratora rozwiązań**, a następnie wybierz pozycję **generowania danych zewnętrznych Lista**.  
  
17. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkt przerwania ustawiony w `GenerateExternalDataLists_Execute` metody. Wybierz **F5** klucza, lub na pasku menu wybierz **debugowania**, **Kontynuuj** do kontynuowania debugowania projektu.  
  
18. Eksperymentalne wystąpienie programu Visual Studio dodaje wystąpienia listy, o nazwie **Entity1DataList** do TestBDCModel projektu i wystąpienie generowany jest również funkcja o nazwie **Feature2** listy wystąpienie.  
  
19. Wybierz **F5** klucza, lub na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do tworzenia, wdrażania i uruchomić projekt TestBDCModel.  
  
     Przeglądarki sieci web zostanie otwarty na domyślną stronę witryny programu SharePoint, która jest używana do debugowania.  
  
20. W **wymieniono** sekcji obszaru Szybkie uruchamianie wybierz **Entity1DataList** listy.  
  
21. Sprawdź, czy lista zawiera kolumny o nazwach Identifier1 i wiadomości, oprócz jednego elementu, który ma wartość 0 Identifier1 i wartość wiadomość Hello World.  
  
     **Modelu łączności danych biznesowych** szablonu projektu generuje domyślny model usługi łączności danych biznesowych, zapewniająca wszystkich tych danych.  
  
22. Zamknij przeglądarkę sieci web.  
  
## <a name="cleaning-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim  
 Po zakończeniu testowania rozszerzenia elementu projektu, Usuń z listy zewnętrznej i model usługi łączności danych biznesowych z witryny programu SharePoint i Usuń rozszerzenia elementu projektu w programie Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Aby usunąć listę dane zewnętrzne z witryny programu SharePoint  
  
1.  W obszarze Szybkie uruchamianie witryny programu SharePoint, wybierz **Entity1DataList** listy.  
  
2.  Na Wstążce w witrynie programu SharePoint, wybierz **listy** kartę.  
  
3.  Na **listy** karcie **ustawienia** grupy, wybierz **ustawień listy**.  
  
4.  W obszarze **uprawnienia i zarządzanie**, wybierz **Usuń tę listę**, a następnie wybierz pozycję **OK** potwierdzenie Wysyłanie listy do Kosza.  
  
5.  Zamknij przeglądarkę sieci web.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Aby usunąć modelu usługi łączności danych biznesowych z witryny programu SharePoint  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **kompilacji**, **Wycofaj**.  
  
     Visual Studio usuwa modelu usługi łączności danych biznesowych z witryny programu SharePoint.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Aby usunąć rozszerzenia elementu projektu w programie Visual Studio  
  
1.  Eksperymentalne wystąpienie programu Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń, wybierz **Generator listy danych zewnętrznych**, a następnie wybierz pozycję **Odinstaluj** przycisku.  
  
3.  W oknie dialogowym wybierz **tak** aby upewnić się, że chcesz odinstalować rozszerzenia.  
  
4.  Wybierz **Uruchom ponownie teraz** aby ukończyć dezinstalację.  
  
5.  Zamknij oba wystąpienia programu Visual Studio (eksperymentalne wystąpienie i wystąpienia, w którym jest otwarte rozwiązanie GenerateExternalDataLists).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  