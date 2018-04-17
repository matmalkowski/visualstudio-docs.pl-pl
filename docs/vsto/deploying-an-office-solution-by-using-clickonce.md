---
title: Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0b5e1b9437412f343874b8cca6513a551d9900d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-an-office-solution-by-using-clickonce"></a>Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce
  Jeśli korzystasz z technologii ClickOnce, można wdrożyć rozwiązania pakietu Office w mniejszej liczby kroków. Podczas publikowania aktualizacji rozwiązanie automatycznie je wykryje i zainstaluje. Niedogodność polega na tym, że w technologii ClickOnce rozwiązanie trzeba zainstalować osobno dla każdego użytkownika komputera. W związku z tym w sytuacjach, gdy na jednym komputerze rozwiązania będzie używało kilka osób, warto rozważyć użycie Instalatora Windows (pliku .msi).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Publikowanie rozwiązania](#Publish)  
  
-   [Zdecyduj, jak chcesz udzielić zaufania do rozwiązania](#Trust)  
  
-   [Pomaganie użytkownikom zainstalować rozwiązania](#Helping)  
  
-   [Umieścić dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowań na poziome dokumentu)](#Put)  
  
-   [Umieścić dokumentu rozwiązanie na serwerze, na którym działa program SharePoint (tylko dostosowań na poziome dokumentu)](#SharePoint)  
  
-   [Tworzenie niestandardowego Instalatora](#Custom)  
  
-   [Publikowanie aktualizacji](#Update)  
  
-   [Zmień lokalizację instalacji rozwiązania](#Location)  
  
-   [Wycofywanie rozwiązania do wcześniejszej wersji](#Roll)  
  
 Aby uzyskać więcej informacji na temat sposobu wdrażania rozwiązania do pakietu Office, tworząc plik Instalatora Windows, zobacz [wdrażania rozwiązania do pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Publish"></a> Publikowanie rozwiązania  
 Rozwiązania można opublikować za pomocą **Kreator publikowania** lub **projektanta projektu**. W tej procedurze użyjesz **projektanta projektu** ponieważ zapewnia pełny zestaw opcji publikowania. Zobacz [Kreator publikowania &#40;programowanie Office w Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  
  
#### <a name="to-publish-the-solution"></a>Aby opublikować rozwiązanie  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł, który ma nazwę projektu.  
  
2.  Na pasku menu wybierz **projektu**, *ProjectName* **właściwości**.  
  
3.  W **projektanta projektu**, wybierz **publikowania** kartę, która na poniższej ilustracji przedstawiono.  
  
     ![Karta publikowania w Projektancie projektu](../vsto/media/vsto-publishtab.png "karcie publikowania w Projektancie projektu")  
  
4.  W **lokalizację folderu publikowania (serwer ftp lub ścieżka pliku)** wprowadź ścieżkę do folderu, w którym ma **projektanta projektu** do skopiowania plików rozwiązania.  
  
     Możesz użyć dowolnego z następujących typów ścieżek.  
  
    -   Ścieżka lokalna (na przykład *C:\FolderName\FolderName*).  
  
    -   Ścieżkę Uniform Naming Convention (UNC) do folderu w sieci (na przykład  *\\\ServerName\FolderName*).  
  
    -   Ścieżka względna (na przykład *PublishFolder\\*, która jest folder, w którym domyślnie jest opublikowana projektu).  
  
5.  W **URL folderu instalacji** wprowadź w pełni kwalifikowaną ścieżkę lokalizacji, gdzie użytkownicy końcowi będą znaleźć rozwiązania.  
  
     Jeśli nie znasz jeszcze lokalizacji, nie wprowadzaj żadnych czynności w tym polu. Domyślnie funkcja ClickOnce szuka aktualizacji w folderze, z którego użytkownicy instalują rozwiązanie.  
  
6.  Wybierz **wymagania wstępne** przycisku.  
  
7.  W **wymagania wstępne** okna dialogowego Sprawdź, czy **Utwórz Instalatora, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.  
  
8.  W **wybierz wstępnie wymagane składniki do zainstalowania** zaznacz pola wyboru dla **Instalator Windows 4.5** i odpowiedniego pakietu .NET Framework.  
  
     Na przykład jeśli elementy docelowe rozwiązanie [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zaznacz pola wyboru dla **Instalator Windows 4.5** i **Microsoft .NET Framework 4.5 Full**.  
  
9. Po rozwiązaniu jest przeznaczony dla platformy .NET Framework 4.5, wybrać **Visual Studio 2010 Tools for Office Runtime** pole wyboru.  
  
    > [!NOTE]  
    >  Domyślnie to pole wyboru nie zostanie wyświetlone. Aby było widoczne, należy utworzyć pakiet programu inicjującego. Zobacz [utworzenie pakietu programu inicjującego dla dodatków pakietu Office 2013 VSTO programu Visual Studio 2012](http://blogs.msdn.com/b/vsto/archive/2012/12/21/creating-a-bootstrapper-package-for-an-office-2013-vsto-add-in-with-visual-studio-2012.aspx).  
  
10. W obszarze **Określ lokalizację instalacji wymagań wstępnych**, wybierz jedną z opcji, które są wyświetlane, a następnie wybierz pozycję **OK** przycisku.  
  
     W tabeli poniżej opisano wszystkie opcje.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |**Pobierz wstępnie wymagane składniki z witryny dostawcy składników**|Użytkownik jest monitowany o pobranie i zainstalowanie wstępnie wymaganych składników z witryny internetowej dostawcy.|  
    |**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co Moja aplikacja**|Wstępnie wymagane oprogramowanie jest instalowane razem z oprogramowaniem. W przypadku zaznaczenia tej opcji program Visual Studio automatycznie kopiuje wszystkie wstępnie wymagane pakiety do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|  
    |**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Visual Studio kopiuje wszystkie wstępnie wymagane pakiety do wskazanej lokalizacji i instaluje je razem z rozwiązaniem.|  
  
     Zobacz [wstępnie wymagane składniki — okno dialogowe](/visualstudio/ide/reference/prerequisites-dialog-box).  
  
11. Wybierz **aktualizacje** przycisku, określ, jak często ma poszczególnym użytkownikom końcowym dodatku VSTO lub dostosowania Wyszukaj aktualizacje, a następnie wybierz pozycję **OK** przycisku.  
  
    > [!NOTE]  
    >  Jeśli jest wdrażany przy użyciu dysku CD lub dysk wymienny, wybierz **nigdy nie sprawdzaj aktualizacji** przycisk opcji.  
  
     Aby uzyskać informacje o sposobie publikowania aktualizacji, zobacz [publikowania aktualizacji](#Update).  
  
12. Wybierz **opcje** przycisk, przejrzyj opcje dostępne w **opcje** okna dialogowego polu, a następnie wybierz pozycję **OK** przycisku.  
  
13. Wybierz **opublikować teraz** przycisku.  
  
     Program Visual Studio dodaje następujące foldery i pliki do folderu publikowania określonego wcześniej w tej procedurze.  
  
    -   **Pliki aplikacji** folderu.  
  
    -   Program instalacyjny.  
  
    -   Manifest wdrażania odwołujący się do manifestu wdrażania najnowszej wersji.  
  
     **Pliki aplikacji** folder zawiera podfolder dla każdej wersji, która została opublikowania. Każdy podfolder danej wersji zawiera następujące pliki.  
  
    -   Manifest aplikacji.  
  
    -   Manifest wdrażania.  
  
    -   Zestawy dostosowywania.  
  
     Na poniższej ilustracji przedstawiono struktury folderu publikowania dodatku VSTO dla programu Outlook.  
  
     ![Struktura folderu publikowania](../vsto/media/publishfolderstructure.png "publikowania struktury folderów")  
  
    > [!NOTE]  
    >  ClickOnce dołącza rozszerzenia .deploy zestawy tak, aby zabezpieczonych instalacji programu Internetowe usługi informacyjne (IIS) nie będzie blokować pliki z powodu niebezpiecznego rozszerzenia. Po zainstalowaniu rozwiązania rozszerzenie jest automatycznie usuwane.  
  
14. Skopiuj pliki rozwiązania do lokalizacji instalacji określonej wcześniej w tej procedurze.  
  
##  <a name="Trust"></a> Zdecyduj, jak chcesz udzielić zaufania do rozwiązania  
 Zanim rozwiązanie będzie można uruchomić na komputerach użytkowników, administrator musi udzielić zaufania albo użytkownicy muszą odpowiedzieć na monit o udzielenie zaufania podczas instalacjo rozwiązania. Aby administrator przyznał zaufanie rozwiązaniu, musi podpisać manifest za pomocą certyfikatu identyfikującego znanego i zaufanego wydawcę. Zobacz [ufające rozwiązania przez podpisywanie aplikacji i wdrażania manifesty](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
 Jeśli wdrażasz dostosowania poziomie dokumentu i chcesz umieścić dokument do folderu na komputerze użytkownika lub udostępnić dokument w witrynie programu SharePoint, upewnij się, że Office ufa lokalizację dokumentu. Zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
##  <a name="Helping"></a> Pomaganie użytkownikom zainstalować rozwiązania  
 Użytkownicy mogą zainstalować rozwiązanie przez uruchomienie programu instalacyjnego, otwarcie manifestu wdrażania lub — w przypadku dostosowania na poziomie dokumentu — bezpośrednie otwarcie dokumentu. Według najlepszych praktyk rozwiązanie należy instalować przy użyciu programu instalacyjnego. Dwa podejścia nie upewnij się, że wstępnie wymagane oprogramowanie zostało zainstalowane. Jeśli użytkownicy chcą otwierać dokument z lokalizacji instalacji, muszą ją dodać do listy zaufanych lokalizacji w Centrum zaufania w aplikacji pakietu Office.  
  
### <a name="opening-the-document-of-a-document-level-customization"></a>Otwieranie dokumentu z dostosowaniem na poziomie dokumentu  
 Użytkownicy mogą otwierać dokument zawierający dostosowanie na poziomie dokumentu bezpośrednio z lokalizacji instalacji albo przez skopiowanie go swoich lokalnych komputerów, a następnie otwarcie kopii.  
  
 Według najlepszych praktyk należy otwierać kopię dokumentu na swoim komputerze, tak aby wiele osób nie próbowało otworzyć jednocześnie tego samego wystąpienia. W celu wymuszenia tej praktyki można tak skonfigurować program instalacyjny, aby kopiował dokument na komputery użytkowników. Zobacz [umieścić dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowań na poziome dokumentu)](#Put).  
  
### <a name="installing-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instalowanie rozwiązania przez otwarcie manifestu wdrażania z witryny internetowej usług IIS  
 Użytkownicy mogą zainstalować rozwiązanie dla pakietu Office poprzez otwarcie manifestu wdrażania z Internetu. Jednak bezpieczna instalacja programu Internet Information Services (IIS) blokuje pliki z rozszerzeniami .vsto. Zanim będzie można wdrożyć rozwiązanie za pomocą usług IIS, w usługach musi być zdefiniowany typ MIME.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Aby dodać typ MIME .vsto do usług IIS 6.0  
  
1.  Na serwerze, na którym jest uruchomiony program IIS 6.0, wybierz **Start**, **wszystkie programy**, **narzędzia administracyjne**, **Internet Information Services (IIS) Manager**.  
  
2.  Wybierz nazwę komputera, **witryn sieci Web** folderu lub w przypadku konfigurowania witryny sieci web.  
  
3.  Na pasku menu wybierz **akcji**, **właściwości**.  
  
4.  Na **nagłówków HTTP** , wybierz pozycję **typy MIME** przycisku.  
  
5.  W **typy MIME** okna, wybierz **nowy** przycisku.  
  
6.  W **typ MIME** okna, wprowadź **.vsto** jako rozszerzenie, wprowadź **application/x-ms-vsto** jako MIME wpisz, a następnie zastosować nowe ustawienia.  
  
    > [!NOTE]  
    >  Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Należy następnie opróżnić pamięć podręczną dysku w przeglądarce i spróbować ponownie otworzyć plik .vsto.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Aby dodać typ MIME .vsto do usług IIS 7.0  
  
1.  Na serwerze, na którym uruchomiono usługi IIS 7.0, wybierz **Start**, **wszystkie programy**, **Akcesoria**.  
  
2.  Otwórz menu skrótów **wiersza polecenia**, a następnie wybierz pozycję **Uruchom jako administrator.**  
  
3.  W **Otwórz** wprowadź następującą ścieżkę, a następnie wybierz pozycję **OK** przycisku.  
  
    ```  
    %windir%\system32\inetsrv   
    ```  
  
4.  Wprowadź następujące polecenie, a następnie zastosuj nowe ustawienia.  
  
    ```  
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  
  
    > [!NOTE]  
    >  Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Należy następnie opróżnić pamięć podręczną dysku w przeglądarce i spróbować ponownie otworzyć plik .vsto.  
  
##  <a name="Put"></a> Umieścić dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowań na poziome dokumentu)  
 Możesz skopiować dokument rozwiązania na komputerze użytkownika końcowego dla nich przy tworzeniu akcji po wdrożeniu. Dzięki temu użytkownik nie musi ręcznie skopiować dokument z lokalizacji instalacji do komputera po zainstalowaniu rozwiązania. Należy utworzyć klasę, która definiuje akcję po wdrożeniu, tworzenie i publikowanie rozwiązania zmodyfikuj manifest aplikacji i ponowne podpisywanie manifestu aplikacji i wdrażania.  
  
 W poniższych procedurach założono, że nazwa projektu to **ExcelWorkbook** i opublikuj rozwiązania pod kątem **C:\publish** katalogu na komputerze.  
  
### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Tworzenie klasy definiującej akcję powdrożeniową  
  
1.  Na pasku menu wybierz **pliku**, **Dodaj**, **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego, **zainstalowane szablony** okienku wybierz **Windows** folderu.  
  
3.  W **szablony** okienku wybierz **biblioteki klas** szablonu.  
  
4.  W **nazwa** wprowadź **FileCopyPDA**, a następnie wybierz pozycję **OK** przycisku.  
  
5.  W **Eksploratora rozwiązań**, wybierz **FileCopyPDA** projektu.  
  
6.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
7.  Na **.NET** , dodaj odwołania do Microsoft.VisualStudio.Tools.Applications.Runtime i Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
8.  Zmień nazwę klasy, która ma `FileCopyPDA`, a następnie zastąp zawartość pliku z kodem. Kod będzie wykonywał następujące zadania:  
  
    -   Kopiowanie dokumentu do komputera użytkownika.  
  
    -   Zmienia _AssemblyLocation właściwość ścieżki względnej pełną ścieżkę dla manifest wdrażania.  
  
    -   Usunięcie pliku, jeśli użytkownik odinstaluje rozwiązanie.  
  
     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  
  
### <a name="build-and-publish-the-solution"></a>Kompilowanie i publikowanie rozwiązania  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **FileCopyPDA** projektu, a następnie wybierz pozycję **kompilacji**.  
  
2.  Otwórz menu skrótów **ExcelWorkbook** projektu, a następnie wybierz pozycję **kompilacji**.  
  
3.  Otwórz menu skrótów **ExcelWorkbook** projektu, a następnie wybierz pozycję **Dodaj odwołanie**.  
  
4.  W **Dodaj odwołanie** okna dialogowego wybierz **projekty** , wybierz pozycję **FileCopyPDA**, a następnie wybierz pozycję **OK** przycisku.  
  
5.  W **Eksploratora rozwiązań**, wybierz **ExcelWorkbook** projektu.  
  
6.  Na pasku menu wybierz **projektu**, **nowy Folder**.  
  
7.  Wprowadź **danych**, a następnie wybierz klawisz Enter.  
  
8.  W **Eksploratora rozwiązań**, wybierz **danych** folderu.  
  
9. Na pasku menu wybierz **projektu**, **Dodaj istniejący element**.  
  
10. W **Dodaj istniejący element** okno dialogowe, przejdź do katalogu wyjściowego dla **ExcelWorkbook** projektu, wybierz **ExcelWorkbook.xlsx** pliku, a następnie wybierz pozycję  **Dodaj** przycisku.  
  
11. W **Eksploratora rozwiązań** wybierz **ExcelWorkbook.xlsx** pliku.  
  
12. W **właściwości** Zmień **Akcja kompilacji** właściwości **zawartości** i **Kopiuj do katalogu wyjściowego** właściwości  **Kopiuj, jeśli nowszy**.  
  
     Po wykonaniu tych czynności projektu będzie podobny poniższej ilustracji.  
  
     ![Struktury projektu wdrożenia akcji post. ] (../vsto/media/vsto-postdeployment.png "Projektu struktury post akcji wdrażania.")  
  
13. Publikowanie **ExcelWorkbook** projektu.  
  
### <a name="modify-the-application-manifest"></a>Modyfikowanie manifestu aplikacji  
  
1.  Otwórz **c:\publish** katalogu przy użyciu **Eksploratora plików**.  
  
2.  Otwórz **pliki aplikacji** folder, a następnie otwórz folder, który odpowiada Najnowsza opublikowana wersja rozwiązania.  
  
3.  Otwórz **ExcelWorkbook.dll.manifest** plik w edytorze tekstu, takiego jak Notatnik.  
  
4.  Po `</vstav3:update>` elementu, Dodaj następujący kod. Dla atrybutu klasy `<vstav3:entryPoint>` element, należy użyć następującej składni: *NamespaceName.ClassName*. W poniższym przykładzie nazwy przestrzeni nazw i klasy są takie same, tak aby wynikowych nazwy punktu wejścia `FileCopyPDA.FileCopyPDA`.  
  
    ```  
    <vstav3:postActions>  
      <vstav3:postAction>  
        <vstav3:entryPoint  
          class="FileCopyPDA.FileCopyPDA">  
          <assemblyIdentity  
            name="FileCopyPDA"  
            version="1.0.0.0"  
            language="neutral"  
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:postActionData>  
        </vstav3:postActionData>  
      </vstav3:postAction>  
    </vstav3:postActions>  
    ```  
  
### <a name="re-sign-the-application-and-deployment-manifests"></a>Ponowne podpisywanie manifestów aplikacji i wdrażania  
  
1.  W **%USERPROFILE%\Documents\Visual 2013\Projects\ExcelWorkbook\ExcelWorkbook w Studio** folder, kopia **ExcelWorkbook_TemporaryKey.pfx** certyfikatu pliku, a następnie wklej go do  *PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ folderu.
  
2.  Otwórz wiersz polecenia programu Visual Studio, a następnie zmień katalogi na **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ folder (na przykład **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  
  
3.  Podpisz zmodyfikowany manifest aplikacji, wykonując następujące polecenie:  
  
    ```  
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  
  
     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.manifest został pomyślnie podpisany”.  
  
4.  Zmień na **c:\publish** folder, a następnie aktualizacji i zaloguj wdrożenia manifestu, uruchamiając następujące polecenie:  
  
    ```  
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  
  
    > [!NOTE]  
    >  W poprzednim przykładzie, Zamień MostRecentVersionNumber numer wersji wcześniej opublikowanej wersji rozwiązania (na przykład **1_0_0_4**).  
  
     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.vsto został pomyślnie podpisany”.  
  
5.  Skopiuj plik ExcelWorkbook.vsto **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ katalogu.  
  
##  <a name="SharePoint"></a> Umieścić dokumentu rozwiązanie na serwerze, na którym działa program SharePoint (tylko dostosowań na poziome dokumentu)  
 Dostosowanie na poziomie dokumentu można opublikować użytkownikom końcowym za pomocą programu SharePoint. Gdy użytkownicy przejdą do witryny programu SharePoint i otworzą dokument, środowisko uruchomieniowe automatycznie zainstaluje rozwiązanie z udostępnionego folderu sieciowego na komputerze lokalnym. Po lokalnym zainstalowaniu rozwiązania dostosowanie nadal będzie działać, nawet, jeśli dokument skopiowano w inne miejsce, na przykład na pulpit.  
  
#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Aby umieścić dokument na serwerze z programem SharePoint  
  
1.  Dodaj dokument z rozwiązania do biblioteki dokumentów w witrynie programu SharePoint.  
  
2.  Wykonaj czynności dla jednej z poniższych metod:  
  
    -   Za pomocą narzędzia konfiguracji pakietu Office dodaj serwer z programem do Centrum zaufania w programie Word lub Excel na komputerach wszystkich użytkowników.  
  
         Zobacz [zasady zabezpieczeń i ustawień w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  
  
    -   Upewnij się, że każdy użytkownik wykona następujące czynności.  
  
        1.  Na komputerze lokalnym, otwieranie Word czy Excel, wybierz **pliku** karcie, a następnie wybierz pozycję **opcje** przycisku.  
  
        2.  W **Centrum zaufania** oknie dialogowym wybierz **zaufanych lokalizacji** przycisku.  
  
        3.  Wybierz **Zezwalaj zaufanych lokalizacji w mojej sieci (niezalecane)** pole wyboru, a następnie wybierz pozycję **Dodaj nową lokalizację** przycisku.  
  
        4.  W **ścieżki** wprowadź adres URL biblioteki dokumentów programu SharePoint, która zawiera dokument, który został przekazany (na przykład *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  
  
             Nie dodawaj nazwę domyślnej strony sieci Web, takich jak default.aspx lub AllItems.aspx.  
  
        5.  Wybierz **podfoldery tej lokalizacji są także zaufane** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
             Gdy użytkownicy otwierają dokument z poziomu witryny programu SharePoint, następuje otwarcie dokumentu i zainstalowanie dostosowania. Użytkownicy mogą wtedy skopiować dokument na swoje komputery. Dostosowanie będzie nadal działać, ponieważ właściwości w dokumencie wskazują jego lokalizację sieciową.  
  
##  <a name="Custom"></a> Tworzenie niestandardowego Instalatora  
 Można utworzyć niestandardowego Instalatora dla rozwiązań pakietu Office, a nie za pomocą programu instalacyjnego, który jest tworzony podczas publikowania rozwiązania. W niestandardowym instalatorze instalacja może być inicjowana przez skrypt logowania albo plik wsadowy może instalować rozwiązanie bez udziału użytkownika. Scenariusze te działają najlepiej, jeśli na komputerach użytkowników końcowych są już zainstalowane wstępnie wymagane składniki.  
  
 W ramach procesu niestandardowej instalacji należy wywołać narzędzie instalatora rozwiązań dla pakietu Office (VSTOInstaller.exe), który domyślnie znajduje się w następującej lokalizacji:  
  
 %commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe  
  
 Jeśli narzędzia nie ma w tym folderze, poszukaj go w kluczu rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath.  
  
 Narzędzie VSTOinstaller.exe współpracuje z parametrami wymienionymi poniżej.  
  
|Parametr|Definicja|  
|---------------|----------------|  
|/Install lub /I|Instalowanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Można określić ścieżkę na komputerze lokalnym, universal naming convention (UNC) udziału plików. Można określić ścieżkę lokalną (*C:\FolderName\PublishFolder*), ścieżką względną (*publikowania\\*), lub w pełni kwalifikowaną lokalizacji (*\\\ServerName\ Nazwa folderu* lub http://*ServerName/nazwa folderu*).|  
|/Uninstall lub /U|Odinstalowywanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Można określić ścieżkę może być na komputerze lokalnym, udziałem pliku UNC. Można określić ścieżkę lokalną (*c:\FolderName\PublishFolder*), ścieżką względną (*publikowania\\*), lub w pełni kwalifikowaną lokalizacji (*\\\ServerName\ Nazwa folderu* lub http://*ServerName/nazwa folderu*).|  
|/Silent lub /S|Instalowanie lub odinstalowywanie bez monitowania użytkownika o wprowadzenie danych ani wyświetlania jakichkolwiek komunikatów. Jeśli wymagana jest wiersz zaufania, dostosowanie nie jest zainstalowane lub zaktualizowane.|  
|/Help lub /?|Wyświetlanie informacji Pomocy.|  
  
 W trakcie pracy narzędzia VSTOinstaller.exe mogą być wyświetlane różne kody błędów.  
  
|Kod błędu|Definicja|  
|----------------|----------------|  
|0|Rozwiązanie zostało pomyślnie zainstalowane lub odinstalowane albo została wyświetlona Pomoc narzędzia VSTOInstaller.|  
|-100|Co najmniej jedna opcja wiersza polecenia jest nieprawidłowa lub została użyta więcej niż raz. Aby uzyskać więcej informacji, wpisz "Instalator vstoinstaller /?" lub zobacz [tworzenie Instalator niestandardowe dla rozwiązań pakietu Office ClickOnce](http://msdn.microsoft.com/en-us/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Co najmniej jedna opcja wiersza polecenia jest nieprawidłowa. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|  
|-200|Manifest rozmieszczenia identyfikatora URI jest nieprawidłowy. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|  
|-201|Nie można zainstalować rozwiązania, ponieważ manifest rozmieszczenia jest nieprawidłowy. Zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|Nie można zainstalować rozwiązania, ponieważ Visual Studio Tools dla pakietu Office części manifest aplikacji jest nieprawidłowa. Zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).|  
|-203|Nie można zainstalować rozwiązania, ponieważ wystąpił błąd pobierania. Sprawdź identyfikator URI lub lokalizację pliku sieciowego manifestu wdrażania, a następnie ponów próbę.|  
|-300|Nie można zainstalować rozwiązania, ponieważ wystąpił wyjątek zabezpieczeń. Zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).|  
|-400|Nie można zainstalować rozwiązania.|  
|-401|Nie można odinstalować rozwiązanie.|  
|-500|Operacja została anulowana, ponieważ nie można zainstalować lub odinstalować rozwiązania albo nie można pobrać manifestu wdrażania.|  
  
##  <a name="Update"></a> Publikowanie aktualizacji  
 Aby zaktualizować rozwiązania, można go opublikować ponownie za pomocą **projektanta projektu** lub **Kreator publikowania**, a następnie skopiuj zaktualizowane rozwiązanie do lokalizacji instalacji. Podczas kopiowania plików do lokalizacji instalacji trzeba koniecznie zaznaczyć opcję zastąpienia poprzednich plików.  
  
 Przy następnym uruchomieniu sprawdza rozwiązania aktualizacji go zawarto a automatycznie ładować nowej wersji.  
  
##  <a name="Location"></a> Zmień lokalizację instalacji rozwiązania  
 Po opublikowaniu rozwiązania można dodać lub zmienić ścieżkę instalacji. Często powody takiej zmiany są następujące:  
  
-   Program instalacyjny został skompilowany przed ustaleniem ścieżki instalacji.  
  
-   Pliki rozwiązania skopiowano do innej lokalizacji.  
  
-   Serwer, na którym znajdują się pliki instalacyjne, ma nową nazwę lub lokalizację.  
  
 Aby zmienić ścieżkę instalacji rozwiązania, należy zaktualizować program instalacyjny, po czym użytkownicy muszą go uruchomić. W przypadku dostosowań na poziomie dokumentu użytkownicy muszą również w swoich dokumentach tak zaktualizować odnośną właściwość, aby wskazywała nową lokalizację.  
  
> [!NOTE]  
>  Jeśli nie chcesz Poproś użytkowników, aby zaktualizować ich właściwości dokumentu, mogą poprosić użytkowników o Pobierz zaktualizowany dokument z lokalizacji instalacji.  
  
#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Aby zmienić ścieżkę instalacji w programie instalacyjnym  
  
1.  Otwórz **wiersza polecenia** okna, a następnie zmień katalogi na folder instalacji.  
  
2.  Uruchom program instalacyjny i obejmują `/url` parametr, który przyjmuje nową ścieżkę instalacji w postaci ciągu.  
  
     Poniższy przykład pokazuje, jak zmienić ścieżkę instalacji na lokalizację w witrynie internetowej firmy Fabrikam; widoczny adres URL można zastąpić dowolną inną ścieżką:  
  
    ```  
    setup.exe /url="http://www.fabrikam.com/newlocation"  
    ```  
  
    > [!NOTE]  
    >  Jeśli pojawi się komunikat z informacją, że podpis pliku wykonywalnego zostanie unieważniony, certyfikat użyty do podpisania rozwiązania jest nieważny, a wydawca nieznany. W rezultacie przed zainstalowaniem rozwiązania użytkownicy będą musieli potwierdzić, że ufają jego źródłu.  
  
    > [!NOTE]  
    >  Aby wyświetlić bieżącą wartość adresu URL, należy uruchomić `setup.exe /url`.  
  
 Na poziomie dokumentu użytkownicy muszą otworzyć dokument, a następnie zaktualizuj jego _AssemblyLocation właściwość. Poniżej zamieszczono odpowiednią procedurę.  
  
#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Aby zaktualizować właściwość _AssemblyLocation w dokumencie  
  
1.  Na **pliku** , wybierz pozycję **informacji**, które na poniższej ilustracji przedstawiono.  
  
     ![Karta informacji w programie Excel](../vsto/media/vsto-infotab.png "kartę informacje w programie Excel")  
  
2.  W **właściwości** wybierz **właściwości zaawansowane**, które na poniższej ilustracji przedstawiono.  
  
     ![Zaawansowane właściwości w programie Excel. ] (../vsto/media/vsto-advanceddocumentproperties.png "Zaawansowane właściwości w programie Excel.")  
  
3.  Na **niestandardowy** karcie **właściwości** wybierz _AssemblyLocation, jak przedstawiono na poniższej ilustracji.  
  
     ![Właściwość AssemblyLocation. ] (../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation właściwości.")  
  
     **Wartość** pole zawiera identyfikator manifestu wdrożenia.  
  
4.  Przed identyfikatorem, wprowadź pełną ścieżkę dokumentu, a następnie pasek w formacie *ścieżki*|*identyfikator* (na przykład *File://ServerName/ Nazwa folderu/nazwa pliku | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.  
  
     Aby uzyskać więcej informacji na temat formatowania tego identyfikatora, wyświetlić [Przegląd właściwości niestandardowego dokumentu](../vsto/custom-document-properties-overview.md).  
  
5.  Wybierz **OK** przycisk, a następnie zapisz i zamknij dokument programu.  
  
6.  Uruchom program instalacyjny bez parametru /url. Rozwiązanie zostanie zainstalowane w podanej lokalizacji.  
  
##  <a name="Roll"></a> Wycofywanie rozwiązania do wcześniejszej wersji  
 Wycofanie rozwiązania powoduje, że użytkownicy wrócą do korzystania z jego starszej wersji.  
  
#### <a name="to-roll-back-a-solution"></a>Aby wycofać rozwiązanie  
  
1.  Otwórz lokalizację instalacji rozwiązania.  
  
2.  W folderze publikowania na najwyższym poziomie usuń manifest wdrażania (plik .vsto).  
  
3.  Znajdź podfolder wersji, do której chcesz wycofać rozwiązanie.  
  
4.  Skopiuj manifest wdrażania z tego podfolderu do folderu publikowania najwyższego poziomu.  
  
     Na przykład, aby wycofać rozwiązania, które jest wywołane **OutlookAddIn1** z 1.0.0.1 wersji na wersję 1.0.0.0, skopiuj plik **OutlookAddIn1.vsto** z **OutlookAddIn1_1_0_0_0** folderu. Wklej go do najwyższego poziomu publikowanie folderu, zastępując manifest wdrażania określonej wersji **OutlookAddIn1_1_0_0_1** który były już.  
  
     Na ilustracji poniżej widać strukturę folderu publikowania w opisywanym przykładzie.  
  
     ![Struktura folderu publikowania](../vsto/media/publishfolderstructure.png "publikowania struktury folderów")  
  
     Gdy użytkownik następnym razem otworzy aplikację lub dostosowany dokument, zostanie wykryta zmiana manifestu wdrażania. Starsza wersja rozwiązania dla pakietu Office jest uruchamiana z pamięci podręcznej funkcji ClickOnce.  
  
> [!NOTE]  
>  Dane lokalne są zapisywane tylko dla jednej poprzedniej wersji rozwiązania. Po wycofaniu dwie wersje dane lokalne nie jest zachowywane. Aby uzyskać więcej informacji na temat danych lokalnych, zobacz [dostęp do lokalnych i zdalnych danych w aplikacjach ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Publikowanie rozwiązań pakietu Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Porady: publikowanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Porady: Instalowanie rozwiązania pakietu Office ClickOnce](http://msdn.microsoft.com/en-us/14702f48-9161-4190-994c-78211fe18065)   
 [Porady: publikowanie rozwiązań Office na poziomie dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Tworzenie niestandardowego Instalatora dla rozwiązań pakietu Office ClickOnce](http://msdn.microsoft.com/en-us/3e5887ed-155f-485d-b8f6-3c02c074085e)  
  
  
