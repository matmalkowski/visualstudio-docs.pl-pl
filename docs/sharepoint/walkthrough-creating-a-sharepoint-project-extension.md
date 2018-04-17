---
title: 'Wskazówki: Tworzenie rozszerzenia projektu SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17722233c5215858dce59a0d85a05f668de85446
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>Wskazówki: tworzenie rozszerzenia projektu SharePoint
  W tym przewodniku ilustruje sposób tworzenia rozszerzeń dla projektów programu SharePoint. Aby odpowiedzieć na poziomie projektu zdarzenia, takie jak po projektu jest dodany, usunięty lub zmieniono jego nazwę, można użyć rozszerzenia projektu. Można również dodać niestandardowe właściwości lub reagować, gdy wartość właściwości zostanie zmieniona. W przeciwieństwie do rozszerzenia elementu projektu rozszerzenia projektu nie może być skojarzony z określonym typem projektu programu SharePoint. Podczas tworzenia rozszerzenia projektu rozszerzenia ładuje po otwarciu dowolnego rodzaju projektu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 W tym przewodniku spowoduje utworzenie niestandardowej właściwości typu Boolean, który jest dodawany do każdego projektu SharePoint utworzone w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Jeśli wartość **True**, nową właściwość dodaje lub mapy obrazów folder zasobów do projektu. Jeśli wartość **False**, folderu Obrazy zostanie usunięty, jeśli istnieje. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie folderów mapowane](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia dla projektów programu SharePoint, która wykonuje następujące czynności:  
  
    -   Dodaje właściwość projektu niestandardowych do okna właściwości. Właściwość ma zastosowanie do każdego projektu programu SharePoint.  
  
    -   Używa modelu obiektów programu SharePoint projektu do dodania zamapowany folder do projektu.  
  
    -   Używa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modelu obiektu automatyzacji (DTE), aby usunąć zamapowany folder z projektu.  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) do wdrożenia zestawu rozszerzenia właściwości projektu.  
  
-   Debugowanie i testowanie właściwości projektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze dewelopera w tym przewodniku:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym przewodniku zastosowano **projektu VSIX** szablonu w [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] do utworzenia pakietu VSIX, aby wdrożyć rozszerzenie właściwości projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
 W tym przewodniku, należy utworzyć dwa projekty:  
  
-   VSIX projekt do utworzenia pakietu VSIX, aby wdrożyć rozszerzenie projektu.  
  
-   Projektu biblioteki klas, który implementuje rozszerzenia projektu.  
  
 Uruchom przewodnika tworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Do tworzenia projektu VSIX  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  Ten węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne wcześniej w tym temacie.  
  
4.  W górnej części okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework, a następnie wybierz pozycję **projektu VSIX** szablonu.  
  
5.  W **nazwa** wprowadź **ProjectExtensionPackage**, a następnie wybierz pozycję **OK** przycisku.  
  
     **ProjectExtensionPackage** projekt jest wyświetlany w **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **Visual Basic** węzłów, a następnie wybierz pozycję **Windows**.  
  
3.  U góry okna dialogowego, wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework, a następnie wybierz pozycję **biblioteki klas** szablon projektu.  
  
4.  W **nazwa** wprowadź **ProjectExtension**, a następnie wybierz pozycję **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ProjectExtension** projektu do rozwiązania i otwarcie pliku kodu Class1 domyślne.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configuring-the-project"></a>Konfigurowanie projektu  
 Przed przystąpieniem do napisania kodu do Tworzenie rozszerzenia projektu, należy dodać pliki kodu i odwołania do zestawów w projekcie rozszerzenia.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  Dodaj plik kodu o nazwie **właściwości niestandardowej** do projektu ProjectExtension.  
  
2.  Otwórz menu skrótów **ProjectExtension** projektu, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
3.  W **odwołania Manager — właściwości niestandardowej** oknie dialogowym wybierz **Framework** węzeł, a następnie zaznacz pole wyboru obok System.ComponentModel.Composition i System.Windows.Forms zestawów.  
  
4.  Wybierz **rozszerzenia** węzła, zaznacz pole wyboru obok Zestawy Microsoft.VisualStudio.SharePoint i EnvDTE, a następnie wybierz **OK** przycisku.  
  
5.  W **Eksploratora rozwiązań**w obszarze **odwołania** folder **ProjectExtension** projektu, wybierz **EnvDTE**.  
  
6.  W **właściwości** Zmień **Osadź typy międzyoperacyjne** właściwości **False**.  
  
## <a name="defining-the-new-sharepoint-project-property"></a>Definiowanie nowych właściwości projektu SharePoint  
 Utwórz klasę, która definiuje rozszerzenia projektu i zachowanie nowej właściwości projektu. Aby zdefiniować nowe rozszerzenie projektu implementuje klasy <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu. Zawsze, gdy chcesz zdefiniować rozszerzenia projektu SharePoint, należy zaimplementować ten interfejs. Ponadto Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy. Ten atrybut umożliwia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aby odnaleźć i załadować Twojego <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> typu konstruktora atrybutu.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Do definiowania nowych właściwości projektu SharePoint  
  
1.  Wklej następujący kod do pliku kodu właściwości niestandardowej.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>Tworzenie rozwiązania  
 Następnie Skompiluj rozwiązanie w celu upewnij się, że skompilowany bez błędów.  
  
#### <a name="to-build-the-solution"></a>Tworzenie rozwiązania  
  
1.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>Tworzenie pakietu VSIX, aby wdrożyć rozszerzenie właściwości projektu  
 Aby wdrożyć rozszerzenia projektu, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX, modyfikując plik Source.Extension.vsixmanifest,a, który jest dołączony do projektu VSIX. Następnie utwórz pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i tworzenia pakietu VSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera plik w Projektancie manifestu. Informacje wyświetlane w **metadanych** karta jest także wyświetlany w **rozszerzenia i aktualizacje**. Wszystkie pakiety VSIX wymaga pliku extension.vsixmanifest. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **właściwości projektu niestandardowej**.  
  
3.  W **autora** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **właściwość niestandardowa projektu programu SharePoint, która włącza lub wyłącza mapowanie folderu zasobów obrazy do projektu**.  
  
5.  Wybierz **zasoby** karcie, a następnie wybierz pozycję **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MEFComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu** przycisk opcji.  
  
8.  W **projektu** wybierz **ProjectExtension**.  
  
     Ta wartość Określa nazwę zestawu, który tworzysz w projekcie.  
  
9. Wybierz **OK** zamknąć **Dodaj nowy element zawartości** okno dialogowe.  
  
10. Na pasku menu wybierz **pliku**, **Zapisz wszystko** gdy zakończenie, a następnie zamknij projektanta manifestu.  
  
11. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt skompiluje się bez błędów.  
  
12. W **Eksploratora rozwiązań**, otwórz menu skrótów **ProjectExtensionPackage** projekt i wybierz pozycję **Otwórz Folder w Eksploratorze plików** przycisku.  
  
13. W **Eksploratora plików**, otwórz folder wyjściowy kompilacji projektu ProjectExtensionPackage, a następnie sprawdź, czy folder zawiera plik o nazwie ProjectExtensionPackage.vsix.  
  
     Domyślnie jest folder wyjściowy kompilacji... folder \bin\Debug folder zawierający plik projektu.  
  
## <a name="testing-the-project-property"></a>Testowanie właściwości projektu  
 Teraz możesz przetestować właściwości niestandardowe projektu. Najłatwiej do debugowania i testowania nowego rozszerzenia właściwości projektu w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. To wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jest tworzona po uruchomieniu VSIX lub inny projekt rozszerzalności. Po debugowania projektu można zainstalować rozszerzenia w systemie, a następnie przejdź do debugowania i testowania go w regularnych wystąpienia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Do debugowania i testowania rozszerzenia w eksperymentalne wystąpienie programu Visual Studio  
  
1.  Uruchom ponownie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie ProjectExtensionPackage.  
  
2.  Uruchom kompilację debugowania projektu przez wybranie **F5** klucza lub, w menu pasek wybierania **debugowania**, **Rozpocznij debugowanie**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 projektu i rozpoczyna eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt rozwiązania farmy programu SharePoint i użyć wartości domyślnych dla innych wartości w kreatorze.  
  
    1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
    2.  W górnej części **nowy projekt** oknie dialogowym wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.  
  
         Rozszerzeń narzędzi SharePoint wymagają funkcji w tej wersji programu [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  W obszarze **szablony** węzła, rozwiń węzeł **Visual C#** lub **Visual Basic** węzła, wybierz **programu SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.  
  
    4.  Wybierz **projektu programu SharePoint 2010** szablonu, a następnie wprowadź **ModuleTest** z nazwą projektu.  
  
4.  W **Eksploratora rozwiązań**, wybierz **ModuleTest** węzła projektu.  
  
     Nowej właściwości niestandardowej **folderu Obrazy mapy** pojawia się w **właściwości** okno z wartością domyślną **False**.  
  
5.  Zmiana wartości tej właściwości **True**.  
  
     Folderu zasobów obrazy zostanie dodany do projektu programu SharePoint.  
  
6.  Zmiana wartości tej właściwości z powrotem do **False**.  
  
     Jeśli wybierzesz **tak** przycisk **Usuń folder obrazów?** okno dialogowe, obrazy, folder zasób zostanie usunięty z projektu programu SharePoint.  
  
7.  Zamknij eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  