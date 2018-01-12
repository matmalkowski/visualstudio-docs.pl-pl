---
title: "Wskazówki: Importowanie elementów z istniejącej witryny SharePoint | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b9d1bcc72bd22e7c528b2a3d8752d15b7005fea5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Wskazówki: importowanie elementów z istniejącej witryny SharePoint
  W tym przewodniku pokazano sposób importowania elementów z istniejącej witryny SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Dostosowywanie witryny programu SharePoint, dodając kolumnę niestandardowej witryny (znanej także jako *pola*.  
  
-   Eksportowanie witryny programu SharePoint do pliku wsp.  
  
-   Importowanie plików .wsp do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programu SharePoint przy użyciu WSP Importowanie projektu.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje programu [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
## <a name="customizing-a-sharepoint-site"></a>Dostosowywanie witryny programu SharePoint  
 Na przykład można będzie tworzyć i dostosowywać podwitryny programu SharePoint, dodając do niej nowej kolumny witryny i tworząc inną witrynę do użycia w przyszłości. Później będzie wyeksportować pierwszej witryny podrzędnej w pliku wsp i zaimportowanie kolumny niestandardową witrynę do drugiej witryny podrzędnej przy użyciu WSP Importowanie projektu.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Tworzenie i dostosowywanie witryny programu SharePoint  
  
1.  Otwórz witrynę programu SharePoint przy użyciu przeglądarki sieci Web, takich jak http://*Nazwa systemowa*/SitePages/Home.aspx.  
  
2.  Tworzenie podwitryny poza głównym witryny programu SharePoint, otwierając **Akcje witryny** menu, a następnie wybierając **nowej lokacji**.  
  
3.  W tej witrynie **Utwórz** oknie dialogowym wybierz **pusta witryna** typu.  
  
4.  W **tytuł** wprowadź **lokacji kolumny Test 1**; na liście **nazwa adresu URL** wprowadź **columntest1**; pozostaw inne ustawienia domyślne wartości. a następnie wybierz **Utwórz** przycisku.  
  
5.  Po utworzeniu witryny, przejdź w przeglądarce do głównej witryny http://*Nazwa systemowa*/SitePages/Home.aspx.  
  
6.  Ponownie Utwórz podwitrynę pustą wylogowuje głównej witryny programu SharePoint, otwierając **Akcje witryny** menu, wybierając **nowej lokacji**, a następnie wybierając **pusta witryna** typu.  
  
7.  W **tytuł** wprowadź **lokacji kolumny Test 2**; na liście **nazwa adresu URL** wprowadź **columntest2**; pozostaw inne ustawienia domyślne wartości. a następnie wybierz **Utwórz** przycisku.  
  
8.  Przejdź z powrotem do pierwszej witryny podrzędnej, http://*SystemName*/columntest1/default.aspx.  
  
9. Na **Akcje witryny** menu, wybierz **ustawienia lokacji** do wyświetlenia strony ustawień lokacji.  
  
10. W **galerie** wybierz **kolumny witryny** łącza.  
  
11. W górnej części **Galeria kolumn witryny** wybierz pozycję **Utwórz** przycisku.  
  
12. W **nazwa kolumny** wprowadź **kolumny testu**, Zachowaj wartości domyślne, a następnie wybierz pozycję **OK** przycisku.  
  
13. **Kolumny testu** kolumna jest wyświetlana w kolumnach niestandardowy nagłówek w galerii kolumny.  
  
## <a name="exporting-the-sharepoint-site"></a>Eksportowanie witryny programu SharePoint  
 Następnie uzyskaj plik Instalatora (wsp) programu SharePoint, który zawiera elementy programu SharePoint i elementy, które mają zostać zaimportowane do programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint. Jeśli nie masz już plik wsp, następnie należy utworzyć jeden z istniejącej witryny SharePoint. W tym przykładzie będzie eksportować domyślnej witryny programu SharePoint, w pliku wsp.  
  
> [!IMPORTANT]  
>  Jeśli wystąpi błąd wykonania wykonaniem tej procedury należy wykonać procedury na komputerze, który ma dostęp do witryny programu SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Aby wyeksportować istniejącej witryny SharePoint  
  
1.  W witrynie programu SharePoint, wybierz **ustawienia lokacji** na **Akcje witryny** kartę, aby wyświetlić stronę ustawień lokacji.  
  
2.  W **Akcje witryny** sekcji strony Ustawienia lokacji, wybierz **lokacji Zapisz jako szablon** łącza.  
  
3.  W **nazwę pliku** wprowadź **ExampleSite**, a następnie w **nazwy szablonu** wprowadź **przykład witryny**.  
  
4.  W tym przykładzie należy pozostawić **dołączanie zawartości** wyczyść pole wyboru.  
  
     Jeśli zaznaczysz to pole [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zapisuje wszystkich list i bibliotek dokumentów i ich zawartość w pliku wsp. Chociaż jest to przydatne w pewnych okolicznościach, nie jest wymagana w tym przykładzie.  
  
5.  Po pomyślnym zakończeniu operacji wybierz **galerii rozwiązań** łącze, aby wyświetlić plik wsp.  
  
     Aby wyświetlić stronę galerii rozwiązań nowszy, otwórz **Akcje witryny** menu, wybierz **ustawienia lokacji**, wybierz **przejdź do ustawień lokacji najwyższego poziomu** łącze w  **Administracja zbiorem lokacji** sekcji, a następnie wybierz pozycję **rozwiązań** łącze w **galerie** sekcji.  
  
6.  W galerii rozwiązań wybierz **ExampleSite** łącza.  
  
7.  W **pobieranie pliku** oknie dialogowym wybierz **zapisać** przycisk, aby zapisać plik w systemie lokalnym domyślnie w folderze pobrane.  
  
## <a name="importing-the-wsp-file"></a>Importowanie plików .wsp  
 Teraz, gdy masz plik wsp, który zawiera element, który chcesz użyć ponownie (niestandardowej witryny kolumnie testu kolumna), zaimportuj plik wsp do niego dostęp.  
  
#### <a name="to-import-a-wsp-file"></a>Aby zaimportować plik .wsp  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **pliku**, **nowy**, **projektu** do wyświetlenia **nowy projekt** okno dialogowe. Jeśli środowiskiem IDE ustawiono użyć ustawienia środowiska deweloperskiego Visual Basic, na pasku menu, wybierz **pliku**, **nowy projekt**.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  Wybierz **Importowanie pakietu rozwiązań 2010 SharePoint** szablonu w **szablony** okienka, pozostaw nazwę projektu jako WspImportProject1, a następnie wybierz **OK** przycisk.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
4.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** wprowadź [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla drugiej witryny programu SharePoint podrzędnej, utworzony wcześniej. Spowoduje dodanie nowego niestandardowego pola elementu, http://*Nazwa systemowa*/columntest2 do danej podwitryny.  
  
5.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** sekcji, należy pozostawić wybór jako **Wdróż jako rozwiązanie w trybie piaskownicy**.  
  
6.  W **określ nowe źródło projektu** strony, przejdź do lokalizacji w systemie, w którym zapisano plik wsp wcześniej, a następnie wybierz pozycję **dalej** przycisku.  
  
    > [!NOTE]  
    >  Jeśli wybierzesz **Zakończ** przycisk na tej stronie, wszystkie dostępne elementy w pliku wsp zostaną zaimportowane.  
  
7.  W **wybierz elementy do zaimportowania** polu, wyczyść wszystkie pola wyboru na liście, z wyjątkiem **kolumny testu**, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     Ponieważ listy zawiera wiele pozycji, można wybrać klawisze Ctrl + aby wybrać wszystkie elementy na liście, wybierz klawisz spacji, aby wyczyścić wszystkie pola wyboru, a następnie zaznacz pole wyboru obok **kolumny testu** elementu.  
  
     Po zakończeniu operacji importowania nowego projektu o nazwie **WspImportProject1** utworzeniu zawiera folder o nazwie **pola**. W tym folderze to kolumna niestandardową witrynę **kolumny testu** i jego pliku definicji Elements.xml.  
  
## <a name="deploying-the-project"></a>Wdrażanie projektu  
 Ponadto wdrożyć **WspImportProject1** do drugiego programu SharePoint podwitryny utworzony wcześniej, aby wyświetlić kolumny niestandardowej witryny.  
  
#### <a name="to-deploy-the-project"></a>Aby wdrożyć projekt  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wybierz klawisz F5, aby wdrożyć i uruchomić projekt importu WSP.  
  
2.  W witrynie programu SharePoint, należy otworzyć **Akcje witryny** menu, a następnie wybierz pozycję **ustawienia lokacji** do wyświetlenia strony ustawień lokacji.  
  
3.  W **galerie** wybierz **kolumny witryny** łącza.  
  
4.  Przewiń w dół do **kolumny niestandardowe** sekcji.  
  
     Zwróć uwagę, że kolumna niestandardowej witryny importowany z pierwszej lokacji programu SharePoint zostanie wyświetlony na liście.  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Tworzenie kontrolek wielokrotnego użytku dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  