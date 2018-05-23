---
title: 'Wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0dfcf3166e3fe4aa5ce17f51d696187cc060639b
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Wskazówki: tworzenie kolumny witryny, typu zawartości oraz listy dla SharePoint
  Poniższe procedury pokazują, jak utworzyć niestandardowe kolumny witryny programu SharePoint — lub *pola*— oraz typu zawartości, który używa kolumny witryny. Ponadto sposobu tworzenia list, która używa nowego typu zawartości.  
  
 Ten instruktaż zawiera następujące zagadnienia:  
  
-   [Tworzenie kolumny witryny niestandardowej](#BKMK_CreatingCustSiteCols).  
  
-   [Tworzenie niestandardowego typu zawartości](#BKMK_CreateCustContType).  
  
-   [Tworzenie listy](#BKMK_CreateList).  
  
-   [Tworzenie listy](#BKMK_CreateList).  
  
-   [Testowanie aplikacji](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Tworzenie kolumny witryny niestandardowej  
 W tym przykładzie tworzy listę pacjentów w szpital Twoich zarządzania. Najpierw należy utworzyć projekt programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i Dodaj kolumny witryny, w następujący sposób.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **pliku** menu, wybierz **nowy**, **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, w obszarze albo **Visual C#** lub **Visual Basic**, rozwiń węzeł **programu SharePoint** węzeł, a następnie wybierz pozycję **2010**.  
  
3.  W **szablony** okienku wybierz **projektu programu SharePoint 2010**, Zmień nazwę projektu, aby **Clinic**, a następnie wybierz pozycję **OK** przycisk.  
  
     Szablon projektu programu SharePoint 2010 jest pusty projekt, który jest używany w tym przykładzie ma zawierać kolumny witryny i innych elementów projektu, które później zostaną dodane.  
  
4.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** strony, wprowadź adres URL lokalnej witryny programu SharePoint, do której chcesz dodać nowy element niestandardowego pola lub użyj domyślnej lokalizacji (`http://<`*SystemName* `>/)`.  
  
5.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** sekcji, użyj wartości domyślnej **Wdróż jako rozwiązanie w trybie piaskownicy**.  
  
     Aby uzyskać więcej informacji o trybie piaskownicy oraz rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Wybierz **Zakończ** przycisku. Projekt powinien być teraz wyświetlany w **Eksploratora rozwiązań**.  
  
#### <a name="to-add-site-columns"></a>Aby dodać kolumny witryny  
  
1.  Dodaj nową kolumnę witryny. Aby to zrobić, w **Eksploratora rozwiązań**, otwórz menu skrótów **Clinic**, a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
2.  W **Dodaj nowy element** okna dialogowego wybierz **kolumny witryny**, Zmień nazwę, aby **pacjenta nazwa**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
3.  W pliku Elements.xml kolumny witryny, należy pozostawić **typu** ustawienie jako **tekst**i zmień **grupy** ustawienie **kolumny witryny Clinic**. Po zakończeniu pliku Elements.xml kolumny witryny powinien wyglądać jak w następującym przykładzie.  
  
    ```xml  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Przy użyciu tej samej procedury, Dodaj dwie kolumny witryny do projektu: **pacjenta identyfikator** (typ = "Integer") i **nazwa lekarza** (typ = "Text"). Ustaw wartość ich grupy **kolumny witryny Clinic**.  
  
##  <a name="BKMK_CreateCustContType"></a> Tworzenie niestandardowego typu zawartości  
 Następnie należy utworzyć typu zawartości — na podstawie typu zawartości kontaktów — zawierającej kolumny witryny, które zostały utworzone w poprzedniej procedurze. Użycie typu zawartości na istniejący typ zawartości, można zaoszczędzić czas, ponieważ podstawowy typ zawartości zawiera kilka kolumn witryny do użycia w nowego typu zawartości.  
  
#### <a name="to-create-a-custom-content-type"></a>Aby utworzyć niestandardowy typ zawartości  
  
1.  Dodaj typ zawartości do projektu. Aby to zrobić, w **Eksploratora rozwiązań**, wybierz węzeł projektu  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
3.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  W **szablony** okienku wybierz **typu zawartości** szablonu, Zmień nazwę, aby **informacji pacjenta**, a następnie wybierz **Dodaj** przycisku.  
  
     **Kreator dostosowania programu SharePoint** otwiera.  
  
5.  W **które podstawowym typem zawartości powinien tego typu zawartości dziedziczyć** wybierz **skontaktuj się z** jako typu zawartości, w której ma zostać utworzony nowy typ zawartości, a następnie wybierz **Zakończ**przycisku.  
  
     W ten sposób umożliwia dostęp do innych lokacji potencjalnie przydatne kolumn skontaktuj się z typu zawartości, oprócz kolumny witryny, które wcześniej zdefiniowane.  
  
6.  Po typie zawartości projektanta występuje w **kolumn** , Dodaj trzy kolumny, które wcześniej zdefiniowane witryny: **nazwa pacjenta**, **identyfikator pacjenta**i **Nazwa lekarza**. Aby dodać te kolumny, wybierz pola pierwszego na liście kolumny witryny, w obszarze **Nazwa wyświetlana**, a następnie wybierz pozycję każdej kolumny witryny na liście, co w czasie.  
  
    > [!TIP]  
    >  Aby wybrać szybciej kolumny witryny, przefiltrować listę, wprowadzając pierwsze litery nazwę kolumny.  
  
7.  Oprócz trzy kolumny niestandardowej witryny, należy dodać **komentarze** kolumny witryny na liście kolumn witryny.  
  
8.  Wybierz **wymagane** pole wyboru dla **nazwa pacjenta** i **identyfikator pacjenta** kolumny witryny, aby były wymagane pola.  
  
9. Na **typu zawartości** i upewnij się, że nazwa typu zawartości jest **informacji pacjenta**, a następnie zmień opis, aby **karty informacyjnej pacjenta**.  
  
10. Zmień **Nazwa grupy** do **typy zawartości Clinic**i pozostawić innymi ustawieniami domyślnymi.  
  
11. Na pasku menu wybierz **pliku**, **Zapisz wszystko**, a następnie zamknij projektanta typu zawartości.  
  
##  <a name="BKMK_CreateList"></a> Tworzenie listy  
 Teraz Utwórz listę, która korzysta z nowej zawartości kolumny typu i witryny.  
  
#### <a name="to-create-a-list"></a>Aby utworzyć listę  
  
1.  Dodaj listę do projektu. Aby to zrobić, w **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
3.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  W **szablony** okienku wybierz **listy** szablonu, Zmień nazwę, aby **pacjentów**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
5.  Pozostaw **dostosować listę na podstawie** ustawienie jako **domyślne (pusta)**, a następnie wybierz pozycję **Zakończ** przycisku.  
  
6.  W Projektancie listy wybierz **typy zawartości** przycisk, aby wyświetlić **ustawienia typu zawartości** okno dialogowe.  
  
7.  Wybieranie nowego wiersza, **informacji pacjenta** zawartości typu na liście typów zawartości, a następnie wybierz pozycję **OK** przycisku.  
  
     W ten sposób dodaje wszystkie kolumny witryny **informacji pacjenta** typu na liście zawartości.  
  
8.  Usuń wszystkie kolumny witryny na liście, z wyjątkiem następujących czynności:  
  
    -   Identyfikator pacjenta  
  
    -   Nazwa pacjenta  
  
    -   Telefon domowy  
  
    -   Wiadomości e-Mail  
  
    -   Nazwa lekarza  
  
    -   Komentarze  
  
9. W obszarze **Nazwa wyświetlana kolumna**, wybierz pusty wiersz, Dodaj kolumnę niestandardowej listy i nadaj mu nazwę **szpital Twoich**. Pozostaw jego typu danych jako **pojedynczy wiersz tekstu**.  
  
     Kolumna listy niestandardowej ma zastosowanie tylko do tej listy. Po dodaniu niestandardowej listy kolumny do listy nowego typu zawartości listy, w tym wszystkie kolumny dodane do listy, jest utworzona i ustawiona jako domyślnej listy.  
  
    > [!TIP]  
    >  Jeśli wybierzesz kolumny z listy kolumn witryny istniejącej kolumny witryny jest używany. Jednak jeśli wprowadzisz wartość nazwy kolumny bez wybierania kolumn na liście, kolumny niestandardowej listy jest tworzony, nawet jeśli na liście istnieje już kolumna o tej samej nazwie.  
  
     Opcjonalnie, zamiast ustawienie typu danych dla kolumny listy niestandardowej **pojedynczy wiersz tekstu**, zamiast tego można ustawić typ danych dla tej kolumny do wyszukiwania i czy można pobrać wartości z tabeli lub innej listy. Dla informacji o kolumnach wyszukiwania, zobacz [listy relacji w programie SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) i [wyszukiwań i relacje listy](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Obok pozycji **identyfikator pacjenta** i **nazwa pacjenta** pola, wybierz opcję **wymagane** pole wyboru.  
  
11. Na **widoków** , wybierz pozycję pusty wiersz, aby utworzyć widok. Wprowadź **pacjenta szczegóły**.  
  
     Na **widoków** kartę, można określić kolumn, które mają być wyświetlane na liście programu SharePoint.  
  
12. Wybierz nowy **szczegóły pacjenta** wiersza, a następnie wybierz pozycję **Ustaw jako domyślny** przycisku.  
  
     Nowy widok jest teraz domyślny widok listy.  
  
13. Dodaj następujące kolumny do **wybrane kolumny** listy w następującej kolejności:  
  
    -   Identyfikator pacjenta  
  
    -   Nazwa pacjenta  
  
    -   Telefon domowy  
  
    -   Wiadomości e-Mail  
  
    -   Nazwa lekarza  
  
    -   Szpital Twoich  
  
    -   Komentarze  
  
14. W **właściwości** wybierz **sortowania i grupowania** właściwości, a następnie kliknij przycisk wielokropka ![ikoną wielokropka](../sharepoint/media/ellipsisicon.gif "ikoną wielokropka")do wyświetlenia **sortowania i grupowania** okno dialogowe.  
  
15. W **nazwa kolumny** wybierz **pacjenta nazwa**, upewnij się, że **sortowanie** kolumny ustawiono **rosnąco**, a następnie wybierz pozycję  **OK** przycisku.  
  
##  <a name="BKMK_TestApp"></a> Testowanie aplikacji  
 Teraz, gotowe kolumn niestandardowej witryny, typu zawartości i listy, wdrażania ich w programie SharePoint, a następnie uruchom aplikację do testowania.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Na pasku menu wybierz **pliku**, **Zapisz wszystko**.  
  
2.  Wybierz klawisz F5, aby uruchomić aplikację.  
  
     Aplikacja została skompilowana, a następnie jego funkcje są wdrożone w programie SharePoint i aktywowane.  
  
3.  Na pasku nawigacyjnym szybkie wybierz **pacjentów** łącze, aby wyświetlić **pacjentów** listy.  
  
     Nazwy kolumn na liście powinna być zgodna te, które zostały wprowadzone **widoków** karcie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Wybierz **Dodaj nowy element** łącze, aby utworzyć kartę pacjenta informacji.  
  
5.  Wprowadź informacje w polach, a następnie wybierz pozycję **zapisać** przycisku.  
  
     Nowy rekord zostanie wyświetlony na liście.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kolumn witryn, typów zawartości i list dla SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Porady: Tworzenie niestandardowego pola typu](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Typy zawartości](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [kolumny](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  