---
title: Za pomocą programu Microsoft Monitoring Agent | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e1a0bb0567b4ff76bd6dfac1c28fe1eccd7f48c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-microsoft-monitoring-agent"></a>Korzystanie z programu Microsoft Monitoring Agent
Aplikacje sieci web ASP.NET hostowanych przez usługi IIS i programu SharePoint 2010 lub 2013 aplikacji pod kątem błędów, problemy z wydajnością lub innych problemów można monitorować lokalnie za pomocą **programu Microsoft Monitoring Agent**. Zdarzenia diagnostyczne od agenta można zapisać do pliku dziennika (.iTrace) IntelliTrace. Następnie możesz otworzyć dziennika w Visual Studio Enterprise (ale nie w wersji Professional lub społeczności) do debugowania problemów z wszystkich narzędzi diagnostycznych programu Visual Studio. IntelliTrace danych diagnostycznych i danych metody może również zbierać, uruchamiając agenta **śledzenia** tryb. Microsoft Monitoring Agent można zintegrować z [usługi Application Insights](http://www.visualstudio.com/get-started/find-performance-problems-vs.aspx) i [System Center Operations Manager](http://technet.microsoft.com/library/hh205987.aspx). Po zainstalowaniu programu Microsoft Monitoring Agent polecenia alter środowiska systemu docelowego.  
  
> [!NOTE]
>  Może również zbierać dane diagnostyczne i metody IntelliTrace dla sieci web programu SharePoint, WPF i aplikacji formularzy systemu Windows na komputerach zdalnych, bez konieczności zmieniania środowiska docelowego przy użyciu **autonomiczny moduł zbierający IntelliTrace**. Autonomiczny moduł zbierający ma wpływ na wydajność większa niż uruchamianie programu Microsoft Monitoring Agent **Monitor** tryb. Zobacz [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 Jeśli używasz programu System Center 2012 za pomocą programu Microsoft Monitoring Agent programu Operations Manager do alerty dotyczące problemów i tworzenie elementów roboczych programu Team Foundation Server z łączami do zapisane dzienniki IntelliTrace. Następnie można przypisać tych elementów roboczych, aby inne osoby do dalszego debugowania. Zobacz [Integrowanie programu Operations Manager z procesami opracowywania oprogramowania](http://technet.microsoft.com/library/jj614609.aspx) i [monitorowania za pomocą programu Microsoft Monitoring Agent](http://technet.microsoft.com/en-us/library/dn465153.aspx).  
  
 Przed rozpoczęciem Sprawdź, czy są zgodne źródło i symboli dla kodu skompilowanego i wdrożone. Dzięki temu można przejść bezpośrednio do kodu aplikacji, podczas uruchamiania debugowania i przeglądanie zdarzeń diagnostycznych dziennika funkcji IntelliTrace. [Konfigurowanie kompilacji](../debugger/diagnose-problems-after-deployment.md) tak, aby Visual Studio mogą automatycznie znaleźć i otworzyć zgodnego źródła dla wdrożonych kodu.  
  
1.  [Krok 1: Konfigurowanie programu Microsoft Monitoring Agent](#SetUpMonitoring)  
  
2.  [Krok 2: Rozpocząć monitorowanie aplikacji](#MonitorEvents)  
  
3.  [Krok 3: Zapisz rejestrowane zdarzenia](#SaveEvents)  
  
##  <a name="SetUpMonitoring"></a> Krok 1: Konfigurowanie programu Microsoft Monitoring Agent  
 Skonfiguruj agenta autonomiczny, na serwerze sieci web, do przeprowadzenia monitorowania lokalnego bez zmieniania aplikacji. Jeśli używasz programu System Center 2012, zobacz [Instalowanie programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465156.aspx).  
  
###  <a name="SetUpStandaloneMMA"></a> Skonfiguruj agenta autonomiczny  
  
1.  Upewnij się, że:  
  
    -   Na serwerze sieci web jest uruchomiona [obsługiwane wersje programu Internetowe usługi informacyjne (IIS)](http://technet.microsoft.com/en-us/library/dn465154.aspx).  
  
    -   Serwer sieci web ma .NET Framework 3.5, 4 lub 4.5.  
  
    -   Serwer sieci web działa środowiska Windows PowerShell 3.0 lub nowszej. [Pytanie: co zrobić, jeśli na komputerze programu Windows PowerShell 2.0?](#PowerShell2)  
  
    -   Musisz mieć uprawnienia administratora na serwerze sieci web na potrzeby uruchomienia poleceń środowiska PowerShell i można odtworzyć puli aplikacji, po rozpoczęciu monitorowania.  
  
    -   Wszystkie wcześniejsze wersje programu Microsoft Monitoring Agent została odinstalowana.  
  
2.  [Pobierz bezpłatne Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384), wersja 32-bitowa **MMASetup-i386.exe** lub 64-bitowej wersji **MMASetup-AMD64.exe**, z Microsoft Download Center, aby sieci web serwer.  
  
3.  Uruchom pobrany plik wykonywalny, aby uruchomić Kreatora instalacji.  
  
4.  Tworzenie bezpiecznej katalogu na serwerze sieci web do przechowywania dzienników IntelliTrace, na przykład **C:\IntelliTraceLogs**.  
  
     Upewnij się, utworzyć ten katalog, przed rozpoczęciem monitorowania. Aby uniknąć spowolnieniem aplikacji, wybierz lokalizację na lokalnym dysku o dużej szybkości, który nie jest bardzo aktywny.  
  
    > [!IMPORTANT]
    >  Dzienniki IntelliTrace może zawierać dane osobiste i wielkość liter. Ogranicz ten katalog tylko tożsamości, które muszą pracować z plikami. Sprawdź zasady zachowania poufności informacji w firmie.  
  
5.  Uruchom szczegółowy, poziom funkcji monitorowania lub do monitorowania aplikacji programu SharePoint, należy udzielić tej puli aplikacji, który jest hostem sieci web aplikacji lub aplikacji SharePoint Odczyt i zapis do katalogu dziennika funkcji IntelliTrace. [Pytanie: jak skonfigurować uprawnienia dla puli aplikacji?](#FullPermissionsITLog)  
  
### <a name="q--a"></a>Pytania i odpowiedzi  
  
####  <a name="PowerShell2"></a> Pytanie: co zrobić, jeśli na komputerze programu Windows PowerShell 2.0?  
 **Odpowiedź:** zdecydowanie zalecane jest użycie programu PowerShell 3.0. W przeciwnym razie należy zaimportować polecenia cmdlet programu PowerShell agenta monitorowania firmy Microsoft każdorazowo po uruchomieniu programu PowerShell. Nie masz również dostęp do zawartości pomocy do pobrania.  
  
1.  Otwórz **programu Windows PowerShell** lub **programu Windows PowerShell ISE** okno wiersza polecenia z uprawnieniami administratora.  
  
2.  Zaimportuj moduł PowerShell agenta monitorowania firmy Microsoft z domyślnej lokalizacji instalacji:  
  
     **PS C: > Import-Module "C:\Program Files\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3.  [Można znaleźć w witrynie TechNet](http://technet.microsoft.com/systemcenter/default) można pobrać najnowszej zawartości pomocy.  
  
####  <a name="FullPermissionsITLog"></a> Pytanie: jak skonfigurować uprawnienia dla puli aplikacji?  
 **A:** użyć Windows **icacls** polecenie lub użyj Eksploratora Windows (lub Eksploratora plików). Na przykład:  
  
-   Aby skonfigurować uprawnienia z systemu Windows **icacls** polecenia:  
  
    -   Dla aplikacji sieci web w **DefaultAppPool** puli aplikacji:  
  
         `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
    -   Dla aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:  
  
         `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
     —lub—  
  
-   Aby skonfigurować uprawnienia z Eksploratora Windows (lub Eksploratora plików):  
  
    1.  Otwórz **właściwości** dla katalogu dziennika funkcji IntelliTrace.  
  
    2.  Na **zabezpieczeń** , wybierz pozycję **Edytuj**, **Dodaj**.  
  
    3.  Upewnij się, że **podmiotów zabezpieczeń** pojawia się w **wybierz ten typ obiektu** pole. Jeśli nie ma, wybierz **typy obiektów** ją dodać.  
  
    4.  Upewnij się, że komputera lokalnego jest wyświetlany w **z tej lokalizacji** pole. Jeśli nie ma, wybierz **lokalizacje** je zmienić.  
  
    5.  W **wprowadź nazwy obiektów do wybrania** pozycję Dodaj pulę aplikacji dla aplikacji sieci web lub aplikacji programu SharePoint.  
  
    6.  Wybierz **Sprawdź nazwy** do rozpoznania nazwy. Wybierz **OK**.  
  
    7.  Upewnij się, że pula aplikacji ma **odczytu & wykonać** uprawnienia.  
  
##  <a name="MonitorEvents"></a> Krok 2: Rozpocząć monitorowanie aplikacji  
 Za pomocą programu Windows PowerShell [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) polecenie, aby rozpocząć monitorowanie aplikacji. Jeśli używasz programu System Center 2012, zobacz [monitorowania aplikacji sieci Web za pomocą programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
1.  Na serwerze sieci web Otwórz **programu Windows PowerShell** lub **programu Windows PowerShell ISE** okno wiersza polecenia z uprawnieniami administratora.  
  
     ![Otwórz program Windows PowerShell jako administrator](../debugger/media/ffr_powershellrunadmin.png "FFR_PowerShellRunAdmin")  
  
2.  Uruchom [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) polecenie, aby rozpocząć monitorowanie aplikacji. Uruchom ponownie wszystkie aplikacje sieci web na serwerze sieci web.  
  
     Oto krótkie składni:  
  
     **Start-WebApplicationMonitoring** *"\<nazwa_aplikacji >"*  *\<monitoringMode >* *"\<outputPath >"*  *\<UInt32 >* *"\<collectionPlanPathAndFileName >"*  
  
     Oto przykład, który używa tylko nazwy aplikacji sieci web i lightweight **Monitor** tryb:  
  
     **PS C: > Start-WebApplicationMonitoring "FabrikamFabrikamFiber.Web" Monitorowanie "C:IntelliTraceLogs"**  
  
     Oto przykład, w którym korzysta z usług IIS, ścieżka i lightweight **Monitor** tryb:  
  
     **PS C: > Start-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web" Monitorowanie "C:IntelliTraceLogs"**  
  
     Po rozpoczęciu monitorowania, Wstrzymaj Microsoft Monitoring Agent może być widoczna podczas ponownego uruchomienia aplikacji.  
  
     ![Zacznij monitorowanie potwierdzenie MMA](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")  
  
    |||  
    |-|-|  
    |*"\<nazwa_aplikacji >"*|Określ ścieżkę do nazwy aplikacji sieci web i witryny sieci web w usługach IIS. Możesz również uwzględnić ścieżki IIS, jeśli wolisz.<br /><br /> *"\<IISWebsiteName >\\< IISWebAppName\>"*<br /><br /> —lub—<br /><br /> **"IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*<br /><br /> Tę ścieżkę można znaleźć w Menedżerze usług IIS. Na przykład:<br /><br /> ![Ścieżka do witryny sieci web usług IIS i aplikacji sieci web](../debugger/media/ffr_iismanager.png "FFR_IISManager")<br /><br /> Można również użyć [Get-WebSite](http://technet.microsoft.com/library/ee807832.aspx) i [uzyskać WebApplication](http://technet.microsoft.com/library/ee790554.aspx) poleceń.|  
    |*\<monitoringMode >*|Określ tryb monitorowania:<br /><br /> <ul><li>**Monitor**: rekord minimalnego szczegóły dotyczące zdarzeń wyjątków i zdarzeń wydajności. Ten tryb jest używany domyślny plan kolekcji.</li><li>**Śledzenia**: szczegóły na poziomie funkcji rejestrowania i monitorowania aplikacji SharePoint 2010 oraz SharePoint 2013 za pomocą określony plan zbierania. Ten tryb może uniemożliwić aplikacji wykonywania wolniej.<br /><br /> <ul><li>[Pytanie: jak skonfigurować uprawnienia dla puli aplikacji?](#FullPermissionsITLog)</li><li>[Pytanie: jak uzyskać większość danych bez spowolnieniem mojej aplikacji?](#Minimizing)</li></ul><br />     W tym przykładzie rejestruje zdarzenia aplikacji SharePoint hostowany w witrynie programu SharePoint:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" Trace "C:\Program Files\Microsoft Monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogs"**</li><li>**Niestandardowe**: zarejestrować niestandardowych informacji przy użyciu określonej kolekcji niestandardowych planu. Musisz ponownie uruchomić monitorowanie edycji planu kolekcji po monitorowania został już uruchomiony.</li></ul>|  
    |*"\<outputPath >"*|Określ pełną ścieżką do przechowywania dzienników IntelliTrace. Upewnij się, utworzyć ten katalog, przed rozpoczęciem monitorowania.|  
    |*\<UInt32 >*|Określ maksymalny rozmiar dziennika funkcji IntelliTrace. Domyślny maksymalny rozmiar dziennika IntelliTrace to 250 MB.<br /><br /> Gdy osiągnie ten limit, agent zastępuje najwcześniejszą wpisów do zapewnienia miejsca dla więcej wpisów. Aby zmienić ten limit, użyj **- wartość właściwości MaximumFileSizeInMegabytes** opcji lub edytować `MaximumLogFileSize` atrybutu w planie kolekcji.|  
    |*"\<collectionPlanPathAndFileName >"*|Określ pełną ścieżkę lub względną ścieżkę i nazwę pliku planu kolekcji. Ten plan jest plik XML, który konfiguruje ustawienia dla agenta.<br /><br /> Te plany są uwzględnione w agencie i korzystać z aplikacji sieci web i aplikacji programu SharePoint:<br /><br /> -   **collection_plan.asp.NET.default.XML**<br />     Zbiera tylko zdarzenia, takie jak wyjątki, zdarzeń wydajności wywołania bazy danych i żądań serwera sieci Web.<br />-   **collection_plan.asp.NET.trace.XML**<br />     Wywołania funkcji na poziomie zbiera oraz wszystkie dane w domyślny plan kolekcji. Ten plan jest dobry szczegółowych analiz, ale może to spowolnić aplikacji.<br /><br /> Zlokalizowane wersje te plany można znaleźć w podfolderach agenta. Możesz również [dostosować te plany lub utworzyć własne plany](http://go.microsoft.com/fwlink/?LinkId=227871) w celu uniknięcia spowolnieniem aplikacji. Umieść wszystkie niestandardowe plany w bezpiecznej lokalizacji na agenta.<br /><br /> [Pytanie: jak uzyskać większość danych bez spowolnieniem mojej aplikacji?](#Minimizing)|  
  
     Aby uzyskać więcej informacji o pełnej składni i inne przykłady, uruchom **get-help Start-WebApplicationMonitoring-szczegółowe** polecenia lub **get-help Start-WebApplicationMonitoring-przykłady** polecenie.  
  
3.  Aby sprawdzić stan wszystkich monitorowanych aplikacji sieci web, uruchom [Get-WebApplicationMonitoringStatus](http://go.microsoft.com/fwlink/?LinkID=313685) polecenia.  
  
### <a name="q--a"></a>Pytania i odpowiedzi  
  
####  <a name="Minimizing"></a> Pytanie: jak uzyskać większość danych bez spowolnieniem mojej aplikacji?  
 **Odpowiedź:** Microsoft Monitoring Agent może zbierać duże ilości danych i wpływa na wydajność aplikacji, w zależności od zbierania danych i sposobu zbierania. Oto niektóre sposoby uzyskania większość danych bez spowolnieniem aplikacji:  
  
-   Dla aplikacji sieci web i aplikacji programu SharePoint agent rejestruje dane dla każdej aplikacji, które współużytkują określoną pulę aplikacji. Może to spowolnić dowolnej aplikacji, który współużytkuje tej samej puli aplikacji, mimo że można ograniczyć kolekcji do modułów dla jednej aplikacji. Aby uniknąć spowolnieniem inne aplikacje, host każdej aplikacji w odrębnej puli aplikacji.  
  
-   Przejrzyj zdarzenia, dla których agent zbiera dane w planie kolekcji. Edycji planu kolekcji można wyłączyć zdarzenia, które nie są istotne lub nie Cię interesują. Może to poprawić wydajność uruchamiania i wydajność środowiska uruchomieniowego.  
  
     Aby wyłączyć zdarzenia, ustaw `enabled` atrybutu dla `<DiagnosticEventSpecification>` elementu `false`:  
  
     `<DiagnosticEventSpecification enabled="false">`  
  
     Jeśli `enabled` atrybut nie istnieje, zdarzenie jest aktywne.  
  
     Na przykład:  
  
    -   Wyłącz zdarzenia przepływu pracy systemu Windows dla aplikacji, które nie używają przepływu pracy systemu Windows.  
  
    -   Wyłącz zdarzenia rejestru dla aplikacji, które uzyskują dostęp do rejestru, ale nie pokazuj problemy z ustawień rejestru.  
  
-   Przejrzyj modułów, do których agent zbiera dane w planie kolekcji. Edycji planu kolekcji w celu uwzględnienia tylko moduły interesujące.  
  
     Zmniejsza to ilość informacji wywołania metody i innych danych Instrumentacji agenta zbierającego uruchamia i uruchomieniu aplikacji. Te dane ułatwiają krokowo kodu podczas debugujesz i przeglądanie wartości przekazany i zwracany z wywołania funkcji.  
  
    1.  Otwórz planu kolekcji. Znajdź `<ModuleList>` elementu.  
  
    2.  W `<ModuleList>`ustaw `isExclusionList` atrybutu `false`.  
  
    3.  Użyj `<Name>` elementu, aby określić poszczególnych modułów z jedną z następujących: Nazwa pliku, wartość ciągu, aby uwzględnić każdy moduł, którego nazwa zawiera ciąg lub klucza publicznego.  
  
     W tym przykładzie tworzy listę, która gromadzi dane tylko z Moduł główny aplikacji sieci web firmy Fabrikam Fiber:  
  
    ```xml  
    <ModuleList isExclusionList="false">  
       <Name>FabrikamFiber.Web.dll</Name>  
    </ModuleList>  
  
    ```  
  
     Aby zbierać dane z dowolnego modułu, którego nazwa zawiera "Fabrikam", należy utworzyć listę podobne do następującego:  
  
    ```xml  
    <ModuleList isExclusionList="false">  
       <Name>Fabrikam</Name>  
    </ModuleList>  
  
    ```  
  
     Aby zbierać dane z modułów, określając ich tokeny klucza publicznego, Utwórz listę podobne do następującego:  
  
    ```xml  
    <ModuleList isExclusionList="false">  
       <Name>PublicKeyToken:B77A5C561934E089</Name>  
       <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>  
       <Name>PublicKeyToken:31BF3856AD364E35</Name>  
       <Name>PublicKeyToken:89845DCD8080CC91</Name>  
       <Name>PublicKeyToken:71E9BCE111E9429C</Name>  
    </ModuleList>  
  
    ```  
  
     **Pytanie: Dlaczego tylko wyklucza modułów zamiast tego?**  
  
     **Odpowiedź:** domyślnie planów kolekcji wykluczyć moduły przez ustawienie `isExclusionList` atrybutu `true`. Jednak to może nadal zbierać dane z modułów, które nie spełniają kryteria listy lub które nie interesujące, takie jak moduły innych firm lub open source.  
  
#### <a name="q-what-values-does-the-agent-collect"></a>Pytanie: jakie wartości jest zbieranie agenta?  
 **Odpowiedź:** pozwoli to zmniejszyć wpływ na wydajność, agent zbiera tylko następujące wartości:  
  
-   Typy pierwotne danych, które są przekazywane do i zwrócony z metody  
  
-   Typy pierwotne danych w polach najwyższego poziomu obiektów przekazany i zwrócony z metody  
  
 Na przykład, załóżmy, że masz `AlterEmployee` podpis metody, który akceptuje całkowitą `id` i `Employee` obiektu `oldemployee`:  
  
 `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
 `Employee` Typ ma następujące atrybuty: `Id`, `Name`, i `HomeAddress`. Istnieje relacja skojarzenia między `Employee` i `Address` typu.  
  
 ![Relacja między pracowników i adres](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
 Agent rejestruje wartości `id`, `Employee.Id`, `Employee.Name` i `Employee` obiektu zwróconego z `AlterEmployee` metody. Jednak agent nie zapisuje informacje o `Address` innych obiektów niż czy miał wartość null lub nie. Agent również nie zapisuje dane dotyczące zmiennych lokalnych w `AlterEmployee` metody tylko innych metod tych zmiennych lokalnych jako parametry, w którym są rejestrowane jako parametry metody.  
  
##  <a name="SaveEvents"></a> Krok 3: Zapisz rejestrowane zdarzenia  
 Po znalezieniu błąd lub problem z wydajnością, zapisać zarejestrowane zdarzenia dziennika funkcji IntelliTrace. Agent tworzy dziennik tylko wtedy, gdy jest on rejestrowane zdarzenia. Jeśli używasz programu System Center 2012, zobacz [monitorowania aplikacji sieci Web za pomocą programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
### <a name="save-recorded-events-but-continue-monitoring"></a>Zapisz zdarzenia zarejestrowane, ale nadal monitorowania  
 Jeśli chcesz utworzyć dziennika IntelliTrace, ale nie chcesz uruchomić ponownie aplikację lub zatrzymać monitorowanie, wykonaj następujące kroki. Agent kontynuuje monitorowanie, nawet jeśli serwer lub aplikacja zostanie uruchomiony ponownie.  
  
1.  Na serwerze sieci web Otwórz okno wiersza polecenia programu Windows PowerShell jako administrator.  
  
2.  Uruchom [Checkpoint-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313684) polecenie, aby zapisać migawkę dziennika funkcji IntelliTrace:  
  
     **CheckPoint-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
     \- lub -  
  
     **CheckPoint-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
     Na przykład:  
  
     **PS C:\\> Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**  
  
     —lub—  
  
     **PS C: > Checkpoint-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web"**  
  
     Aby uzyskać więcej informacji, uruchom **get-help Checkpoint-WebApplicationMonitoring-szczegółowe** polecenia lub **get-help Checkpoint-WebApplicationMonitoring-przykłady** polecenia.  
  
3.  Skopiuj dziennika do bezpiecznego folderu udostępnionego, a następnie otwórz dziennik z komputera, który ma Visual Studio Enterprise (ale nie w wersji Professional lub społeczności).  
  
    > [!IMPORTANT]
    >  Należy zachować ostrożność podczas udostępniania dzienników IntelliTrace, ponieważ mogą zawierać dane osobiste i poufne. Upewnij się, że, kto może uzyskać dostępu do tych dzienników ma uprawnienia do przyjrzeć się dane. Sprawdź zasady zachowania poufności informacji w firmie.  
  
 **Następnie:** [Diagnozuj rejestrowane zdarzenia w Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### <a name="save-recorded-events-and-stop-monitoring"></a>Zapisz zarejestrowane zdarzenia i zatrzymać monitorowanie  
 Po prostu chcesz uzyskać informacje diagnostyczne podczas odtwarzania konkretnego problemu, wykonaj następujące kroki. Uruchom ponownie wszystkie aplikacje sieci web na serwerze sieci web.  
  
1.  Na serwerze sieci web Otwórz okno wiersza polecenia programu Windows PowerShell jako administrator.  
  
2.  Uruchom [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) polecenie, aby utworzyć dziennika funkcji IntelliTrace i zatrzymać monitorowanie aplikacji sieci web określonych:  
  
     **Stop-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
     \- lub -  
  
     **Stop-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
     Lub aby zatrzymać monitorowanie wszystkich aplikacji sieci web:  
  
     **Stop-WebApplicationMonitoring - wszystkie**  
  
     Na przykład:  
  
     **PS C:\\> Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**  
  
     \- lub -  
  
     **PS C:\\> Stop-WebApplicationMonitoring "IIS:\sites\Fabrikam\FabrikamFiber.Web"**  
  
     Aby uzyskać więcej informacji, uruchom **get-help Stop-WebApplicationMonitoring-szczegółowe** polecenia lub **get-help Stop-WebApplicationMonitoring-przykłady** polecenia.  
  
3.  Skopiuj dziennika do bezpiecznego folderu udostępnionego, a następnie otwórz dziennik z komputera, na którym jest Visual Studio Enterprise.  
  
 **Następnie:** [Diagnozuj rejestrowane zdarzenia w Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
### <a name="q-where-can-i-get-more-information"></a>Pytanie: gdzie można uzyskać więcej informacji?  
  
#### <a name="blogs"></a>Blogi  
 [Wprowadzenie do programu Microsoft Monitoring Agent](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/introducing-microsoft-monitoring-agent.aspx)  
  
 [Optymalizacja zbieranie danych IntelliTrace na serwerach produkcyjnych](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
#### <a name="forums"></a>Fora  
 [Diagnostyka programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)