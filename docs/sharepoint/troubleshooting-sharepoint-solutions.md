---
title: "Rozwiązywanie problemów z rozwiązaniami SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f03f8fd1fd5609f93d4fae22a7a694e61b1c80c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-sharepoint-solutions"></a>Rozwiązywanie problemów z rozwiązaniami SharePoint
  Następujące problemy lub alertów może wystąpić, gdy debugowanie rozwiązań SharePoint przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera. Aby uzyskać więcej informacji, zobacz [debugowanie rozwiązania przepływu pracy programu SharePoint 2007](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Ograniczenia tokenu w trybie piaskownicy programu Visual Web Part  
 Części sieci web Visual w rozwiązań w trybie piaskownicy nie może przetworzyć tokenów standardowe, takie jak $SPUrl, który obsługuje środowisko uruchomieniowe programu SharePoint. W związku z tym adres URL nie zostanie rozwiązany i nie można wyświetlić podglądu zawartości w widoku Projekt w Projektancie wizualny składnik web part, jeśli użytkownik odwołuje się do niego bezpośrednio w elemencie skryptów, takich jak w poniższym przykładzie:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Aby obejść to ograniczenie i rozpoznać tokenu, odwołuje się do niego przy użyciu literałów:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Ograniczenia dotyczące znaków w nazwach projektów i elementów projektu  
 Nazwy projektów i elementów projektu mogą zawierać tylko znaki, które są dozwolone w ścieżce wdrożenia w programie SharePoint 2010. Inne znaki są niedozwolone.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Komunikat o błędzie "Nieprawidłowe znaki".  
  
### <a name="resolution"></a>Rozwiązanie  
 Nazwy projektów programu SharePoint i elementy projektu można użyć tylko następujące znaki:  
  
-   Alfanumeryczne znaki ASCII  
  
-   Miejsce  
  
-   Kropka (.)  
  
-   Przecinek (,)  
  
-   Znak podkreślenia (_)  
  
-   Łączniki (-)  
  
-   Ukośnik odwrotny (\\)  
  
 Gdy projekt jest dostarczana, reguły walidacji sprawdza, czy właściwość ścieżka wdrożenia dla każdego pliku, który jest wdrażany zawiera tylko te prawidłowe znaki.  
  
## <a name="errors-when-creating-custom-fields"></a>Błędy podczas tworzenia niestandardowego pola  
 W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], pól niestandardowych zdefiniowanych w pliku XML. Mogą wystąpić błędy, jeśli pole nie jest zdefiniowany lub odwołuje się przy użyciu określonego formatu.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 "Nieprawidłowy znak" komunikat o błędzie w czasie tworzenia pakietów.  
  
### <a name="resolution"></a>Rozwiązanie  
 Identyfikator definicji pola musi być identyfikatorem GUID ujęte w nawiasy klamrowe, jak przedstawiono na poniższym przykładzie:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Jak pokazano na poniższym przykładzie, odwołanie do pola typu zawartości musi być zdefiniowana przy użyciu formatu pusty element (\<FieldRef / >), nie za pomocą elementów rozpoczęcia/zakończenia (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Jeśli źródło XML pole jest nieprawidłowo sformułowany, nie jest prawidłowym plikiem XML lub wykazuje inny problem, występuje błąd "nie może przeanalizować pliku".  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nowe definicje witryny innej niż angielska nie są wyświetlane na stronie tworzenia lokacji po wdrożeniu  
 Po utworzeniu i wdrażanie definicji witryny przy użyciu innej niż angielska wersji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (oznacza to, że wersja ustawienia regionalne [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] niż 1033), **dostosowań SharePoint** karta nie pojawia się w **Wybieranie szablonu** pole i nowy szablon witryny nie jest wyświetlane w **nową witrynę programu SharePoint** strony.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Brak.  
  
### <a name="resolution"></a>Rozwiązanie  
 Ten problem występuje z powodu nieprawidłowej wartości w **ścieżki** właściwość webtemp plik definicji witryny konfiguracji, takich jak webtemp_SiteDefinitionProject1.xml. W **ścieżki** właściwości pliku webtemp, znajduje się w obszarze **lokalizacja wdrożenia**, zmień odpowiednie ustawienia regionalne 1033 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Na przykład aby użyć japońskich ustawień regionalnych zmień wartość 1041. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych identyfikatory przypisane przez firmę Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) w witrynie MSDN.  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Błąd jest wyświetlany, gdy projekt przepływu pracy jest wdrażana na czystego systemu  
 Ten problem występuje w przypadku wdrożenia na projekt przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na czystego systemu. Oczyść system to komputer, który ma nowa instalacja [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu SharePoint, ale żadne projekty wdrożonej przepływu pracy.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Nie można znaleźć listy programu SharePoint: historii przepływu pracy.  
  
### <a name="resolution"></a>Rozwiązanie  
 Ten błąd występuje z powodu brakujących listy historii przepływu pracy. Ponieważ środowisko projektowe jest czysty system, przepływów pracy są wdrażane i listy historii przepływu pracy jeszcze nie istnieje. Aby rozwiązać ten problem, uruchom ponownie kreatora przepływu pracy, co powoduje, że na liście historii przepływu pracy do utworzenia.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>Aby ponownie wprowadzić kreatora przepływu pracy  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł przepływu pracy.  
  
2.  W **właściwości** okna, kliknij przycisk wielokropka (...) na dowolnej właściwości, która znajduje się przycisk wielokropka.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Użytkownik należy odświeżyć strony aplikacji w przeglądarce podczas debugowania na widok aktualizacji obrazu  
 Jeśli debugujesz rozwiązania programu SharePoint, które zawiera strony aplikacji z kontrolkę wyświetlającą obraz, takich jak [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] formantu obrazu, należy odświeżyć stronę w przeglądarce, aby wyświetlić wszystkie zmiany wprowadzone do obrazu.  
  
## <a name="error-the-site-location-is-not-valid"></a>Błąd: Lokalizacji lokacji jest nieprawidłowy  
 Ten problem może wystąpić, jeśli [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] nie jest zainstalowany. Może również wystąpić, jeśli nie masz uprawnień dostępu administratora do witryny sieci Web programu SharePoint, określonego w **Kreator dostosowania programu SharePoint**.  
  
### <a name="error-message"></a>Komunikat o błędzie  
  
-   Lokalizacja witryny programu SharePoint jest nieprawidłowy.  
  
### <a name="resolution"></a>Rozwiązanie  
  
-   Zainstaluj [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Upewnij się, że masz dostęp administratora do witryny sieci Web programu SharePoint. Aby uzyskać więcej informacji, zobacz [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] Online artykułu [udzielić dostępu do witryny portalu](http://go.microsoft.com/fwlink/?LinkId=98310).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Zdarzeń sieci Web usunięcia witryny nie występuje w projekcie odbiorcy zdarzeń  
 Podczas tworzenia projektu odbiorcy zdarzeń i wybierz określonych zdarzeń sieci Web, takich jak "lokacji jest usuwany", zdarzenie nie występuje.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Brak.  
  
### <a name="resolution"></a>Rozwiązanie  
 Ten problem występuje, ponieważ zakres funkcji "Witryna" do obsługi zdarzenia na poziomie witryny, a musi być domyślny zakres funkcji dla projektów odbiornik zdarzeń jest "Web". Dostępne są następujące zdarzenia sieci Web, których dotyczy problem:  
  
-   Lokacji są usuwane (WebDeleting)  
  
-   Usunięto lokacji (WebDeleted)  
  
-   Jest witryną przenieść (WebMoving)  
  
-   Została przeniesiona lokacji (WebMoved)  
  
 Aby rozwiązać ten problem, zmień zakres funkcji odbiornika zdarzeń w następujący sposób.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Aby zmienić zakres funkcji odbiorcy zdarzeń  
  
1.  W **Eksploratora rozwiązań**, otwórz plik .feature odbiornika zdarzeń w **projektanta funkcji** przez dwukrotne kliknięcie pliku lub otwierania jego menu skrótów, a następnie wybierając **Otwórz**.  
  
2.  Wybierz strzałkę obok pozycji **zakres**, a następnie wybierz pozycję **lokacji** na liście.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Błąd wdrażania pojawia się po zmianie nazwy identyfikatora w projekcie modelu łączności danych biznesowych  
 Ten problem występuje, gdy zmiana nazwy identyfikatora jednostki w modelu łączności danych biznesowych (BDC), a następnie spróbuj wdrożyć rozwiązanie.  
  
### <a name="error-messages"></a>komunikaty o błędach  
  
-   \<*Nazwa modelu*> zawiera następujące błędy aktywacji typu zawartości zewnętrznej...  
  
-   IMetadataObject o nazwie "\<*Nazwa modelu*>" ma wartość w pole "Nazwa" zduplikowanych...  
  
### <a name="resolution"></a>Rozwiązanie  
 Aby rozwiązać ten problem, Usuń ręcznie modelu, a następnie wykonaj ponowne wdrożenie rozwiązania.  Można usunąć modelu przy użyciu jednej z następujących narzędzi:  
  
-   Administracja centralna programu SharePoint 2010. Aby uzyskać więcej informacji, zobacz [zarządzania modelu BDC](http://go.microsoft.com/fwlink/?LinkID=181472) w witrynie Microsoft TechNet Web.  
  
-   Windows PowerShell. Można usunąć modelu, wpisując polecenie w wierszu polecenia: **SPBusinessDataCatalogModel Usuń**. Aby uzyskać więcej informacji, zobacz [ogólne polecenia cmdlet (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) w witrynie Microsoft TechNet Web.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Pojawia się błąd podczas próby wyświetlenia wizualny składnik Web Part w programie SharePoint  
 Ten problem występuje, gdy **ścieżki** właściwości kontrolki użytkownika nie zaczyna się od ciągu "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>komunikaty o błędach  
  
-   Plik "/_CONTROLTEMPLATES/*\<Nazwa projektu >*/*\<Nazwa części sieci Web >*/*\<kontrolki użytkownika nazwa >*.ascx "nie istnieje.  
  
-   Błąd serwera w "/" aplikacji.  
  
### <a name="resolution"></a>Rozwiązanie  
  
##### <a name="to-resolve-this-issue"></a>Aby rozwiązać ten problem  
  
1.  W **Eksploratora rozwiązań**, wybierz plik kontrolki użytkownika, którego rozszerzenie nazwy pliku jest .ascx.  
  
2.  Na pasku menu wybierz **widoku**, **okna właściwości**.  
  
3.  W **właściwości** okna, rozwiń węzeł **lokalizacja wdrożenia** węzła.  
  
4.  Upewnij się, że wartość **ścieżki** właściwości rozpoczyna się od ciągu "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Błąd pojawia się po uruchomieniu importowanych przepływu pracy wielokrotnego użytku zawierający pole formularza zadania  
 Ten problem występuje, jeśli importowania przepływu pracy, który zawiera z polem formularza zadania, a następnie uruchom nowy przepływ pracy, w tym samym systemie, w którym można zaimportować.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Wystąpił błąd podczas kroku wdrożenia "Aktywacja funkcji": pole o identyfikatorze [*Guid*] zdefiniowany w funkcji [*Guid*] został znaleziony w bieżącej kolekcji lokacji lub w podwitrynie.  
  
### <a name="resolution"></a>Rozwiązanie  
 Ten błąd jest wynikiem kolizji Identyfikatora pola, które występują, ponieważ projekt przepływu pracy wielokrotnego użytku importowania w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie zmienia identyfikatory pól formularza zadania. Jeśli wdrożono importowanych przepływu pracy na tym samym serwerze, który zawiera oryginalny przepływ pracy, wystąpić kolizji Identyfikatora pola.  
  
 Aby rozwiązać ten problem, należy użyć funkcji Znajdź i Zamień, aby zmienić wartości atrybutu Identyfikatora pola we wszystkich plikach importowanych przepływu pracy.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Błąd jest wyświetlany, gdy zmieniono zaimportowane wykonywania wystąpienia listy  
 Ten problem występuje w przypadku zmiany nazwy wystąpienia listy zaimportowane, a następnie uruchom go [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Błąd kompilacji: Wystąpił błąd podczas kroku wdrożenia "Aktywacja funkcji": plik Template\Features\\[*zaimportować projekt**funkcji**nazwa*] \Files\Lists \\[*starego**Nazwa listy*] \Schema.xml nie istnieje.  
  
### <a name="resolution"></a>Rozwiązanie  
 Po zaimportowaniu wystąpienia listy atrybut o nazwie CustomSchema jest dodane do pliku Elements.xml wystąpienia listy. Elements.XML zawiera ścieżkę niestandardowego pliku schema.xml dla wystąpienia listy. Jeśli zmienisz nazwę wystąpienia listy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ścieżkę wdrażania dla niestandardowego pliku schema.xml zmian, ale wartość atrybutu CustomSchema ścieżki nie jest aktualizowana. W związku z tym wystąpienia listy nie można odnaleźć pliku schema.xml w starej ścieżki, który jest określony przez atrybut CustomSchema, gdy funkcja jest aktywna.  
  
 Aby rozwiązać ten problem, należy zaktualizować ścieżki lokalizacji wdrożenia pliku schema.xml w atrybucie CustomSchema.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Programu SharePoint został przerwany przez usługi IIS sesji debugowania  
 Ten problem występuje, gdy Ustaw punkt przerwania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązania programu SharePoint, wybierz klawisz F5, aby uruchomić go, a następnie zachować w punkcie przerwania dłużej niż 90 sekund.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Debugowany proces serwera sieci Web został zakończony przez Internet Information Services (IIS). Ten problem można uniknąć przez skonfigurowanie ustawień polecenia ping dla puli aplikacji w usługach IIS. Zobacz Pomoc, aby uzyskać dodatkowe szczegóły.  
  
### <a name="resolution"></a>Rozwiązanie  
 Domyślnie pula aplikacji usług IIS oczekuje 90 sekund dla aplikacji, aby odpowiadać przed jego zamknięciem aplikacji. Ten proces jest nazywany "ping" aplikacji. Aby rozwiązać ten problem, można zwiększyć czas oczekiwania lub wyłączenie aplikacji całkowicie polecenie ping.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>Uzyskać dostęp do ustawień puli aplikacji usług IIS  
  
1.  Otwórz Menedżera usług IIS.  
  
2.  W **połączeń** okienku rozwiń węzeł serwera programu SharePoint, a następnie wybierz **pul aplikacji** węzła.  
  
3.  Na **pul aplikacji** puli aplikacji programu SharePoint (zazwyczaj "SharePoint — 80"), wybierz pozycję, a następnie w **akcje** okienku wybierz **Zaawansowane ustawienia** łącze.  
  
4.  Aby zwiększyć czas oczekiwania przed upływem limitu czasu usług IIS, należy zmienić wartość **maksymalny czas odpowiedzi polecenia Ping (sekundy)** na wartość większą niż 90 sekund.  
  
5.  Aby wyłączyć IIS polecenie ping, ustaw **włączone Ping** do **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Automatycznie wycofać pozostawia wystąpienie listy oddzielone w programie SharePoint  
 Ten problem występuje, gdy należy wykonać następujące kroki.  
  
1.  Utwórz definicję listy, która zawiera wystąpienie listy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wybierz klawisz F5, aby uruchomić rozwiązanie.  
  
3.  Zatrzymaj debugowanie lub zamknąć witrynę programu SharePoint.  
  
4.  Otwórz witrynę programu SharePoint, a następnie otwórz wystąpienie listy.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Błąd serwera w "/" aplikacji.  
  
### <a name="resolution"></a>Rozwiązanie  
 Dzieje się tak, ponieważ po zamknięciu sesji debugowania rozwiązania programu SharePoint, wycofać automatycznie funkcji wycofuje rozwiązania. Wycofania usuwa definicji listy z programu SharePoint, ale nie powoduje usunięcia wystąpienia listy. Podstawowej definicji listy jest wymagany przez wystąpienie listy.  
  
 Aby rozwiązać ten problem, należy wdrożyć rozwiązanie, z menu, wybierając **kompilacji**, **Wdróż**. (Nie debugowania rozwiązania, wybierając klawisz F5.) Następnie należy usunąć wystąpienia listy w programie SharePoint.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Oryginalny rozwiązania SharePoint zastępuje wyeksportowane wersji  
 Podczas eksportowania rozwiązania programu SharePoint, należy zaimportować rozwiązania do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], a następnie wdrożyć rozwiązanie tej samej lokacji, z którego został wyeksportowany, zastępuje w oryginalnym rozwiązaniu programu SharePoint. Ten problem nie występuje, jeśli wdrożyć rozwiązanie do serwera, który nie ma oryginalnym rozwiązaniu aktywowany na nim.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Brak.  
  
### <a name="resolution"></a>Rozwiązanie  
 Aby uniknąć zastąpienia rozwiązania w lokacji, z którego zostały wyeksportowane, zmień identyfikatory GUID SolutionID i identyfikatorów wszystkich importowanych funkcji w funkcji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu.  
  
## <a name="error-appears-when-debugging-starts"></a>Błąd jest wyświetlany, gdy debugowanie się rozpocznie  
 Po rozpoczęciu debugowania rozwiązania SharePoint w Visual Studio, błąd wskazuje, że Visual Studio nie może załadować pliku Web.config, ponieważ podany klucz nie został w słowniku.  
  
### <a name="error-message"></a>Komunikat o błędzie  
 Nie można załadować pliku konfiguracji Web.config. Sprawdź wszystkie uszkodzone elementy XML w pliku i spróbuj ponownie. Wystąpił następujący błąd: podany klucz nie był obecny w słowniku.  
  
### <a name="resolution"></a>Rozwiązanie  
 Aby rozwiązać ten problem, upewnij się, że wartość właściwości adresu URL witryny projektu programu SharePoint w Visual Studio odpowiada adresowi URL, przypisane do strefy domyślnej dla mapowań dostępu alternatywnego aplikacji sieci web. Nie można rozpoznać błędu przy użyciu innej strefy, takich jak Intranet, dla adresu URL. Lokacji adres URL projektu i adres URL w strefa domyślna musi być zgodna. Aby uzyskać dostęp do mapowań dostępu alternatywnego, Otwórz narzędzie Administracja centralna programu SharePoint 2010, wybierz polecenie **Zarządzanie aplikacjami** łącza, a następnie w obszarze **aplikacji sieci Web**, wybierz  **Konfigurowanie mapowań dostępu alternatywnego** łącza. Aby uzyskać więcej informacji, zobacz [tworzenie stref dla aplikacji sieci Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
