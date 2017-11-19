---
title: "Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 40c679811f137e77909395042d91d0458c874d90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce
W tym temacie opisano następujące typowe błędy, które mogą wystąpić podczas wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i zawiera kroki umożliwiające rozwiązanie problemu.  
  
## <a name="general-errors"></a>Ogólne błędy  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Podczas lokalizowania pliku .application nic się nie dzieje, XML renderuje w programie Internet Explorer lub pojawi się okno dialogowe Run lub Zapisz jako  
 Typy zawartości (znanej także jako typy MIME) nie jest poprawnie zarejestrowany na serwerze lub klienta prawdopodobnie przyczyną tego błędu.  
  
 Najpierw upewnij się, że serwer jest skonfigurowany do skojarzenia z rozszerzeniem .application z typem zawartości "application/x-ms aplikacji".  
  
 Jeśli serwer jest skonfigurowany prawidłowo, upewnij się, że [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] jest zainstalowany na tym komputerze. Jeśli [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] jest zainstalowana, i są nadal występuje ten problem, spróbuj odinstalować i ponownie zainstalować [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] Aby ponownie zarejestrować typ zawartości na kliencie.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Komunikat o błędzie jest wyświetlany komunikat "nie można pobrać aplikacji. Pliki Brak we wdrożeniu"lub"pobrania aplikacji zostało przerwane, sprawdź, czy błędy sieciowe i spróbuj ponownie później "  
 Ten komunikat oznacza, że jeden lub więcej plików, do których odwołuje się [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów nie można pobrać. Najprostszym sposobem debugowania tego błędu jest próba pobrania adresu URL który [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mówi, nie można go pobrać. Poniżej przedstawiono niektóre możliwe przyczyny:  
  
-   Jeśli plik dziennika mówi "(403) zabroniony" lub "(404) nie znaleziono" Sprawdź, czy serwer sieci Web jest skonfigurowany tak, aby pobrać ten plik nie są blokowane. Aby uzyskać więcej informacji, zobacz [serwera i klienta problemów z konfiguracją we wdrożeniach ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Jeśli plik .config jest blokowana przez serwer, zobacz sekcję "Pobierz błąd podczas próby zainstalowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z pliku .config" dalszej części tego tematu.  
  
-   Określenia, czy wystąpiły ponieważ `deploymentProvider` wskazuje adres URL w manifeście rozmieszczenia w innej lokalizacji niż adres URL używany do aktywacji.  
  
-   Upewnij się, że wszystkie pliki znajdują się na serwerze; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dziennika powinien informujące, plik, który nie został znaleziony.  
  
-   Czy istnieją problemy z łącznością sieciową; Ten komunikat może odbierać, jeśli komputer kliencki przejścia w tryb offline podczas pobierania.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Błąd pobierania podczas próby zainstalowania aplikacji ClickOnce, z pliku .config  
 Domyślnie aplikacja systemu Windows w języku Visual Basic obejmuje pliku App.config. Będą występować problem, gdy użytkownik próbuje zainstalować z serwera sieci Web, który korzysta z systemu Windows Server 2003, ponieważ ten system operacyjny blokuje instalację plikach .config ze względów bezpieczeństwa. Aby włączyć pliku .config do zainstalowania, kliknij **rozszerzeniem ".deploy"** w **opcji publikowania** okno dialogowe.  
  
 Należy również ustawić typy zawartości (znanej także jako typy MIME) odpowiednio dla .application, manifest i .deploy plików. Aby uzyskać więcej informacji zobacz dokumentację serwera sieci Web.  
  
 Aby uzyskać więcej informacji, zobacz "Typy systemu Windows Server 2003: stref zawartości" w [serwera i klienta problemów z konfiguracją we wdrożeniach ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Komunikat o błędzie: "Aplikacja jest niewłaściwie sformatowana;" Plik dziennika zawiera "podpis XML jest nieprawidłowy"  
 Sprawdź, czy zaktualizować plik manifestu i ponownie podpisana. Ponownie opublikować aplikację przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub zaloguj się ponownie aplikację za pomocą obraz.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Zaktualizowano aplikację na serwerze, ale klient nie pobiera aktualizacji  
 Ten problem można rozwiązać, wykonując jedną z następujących czynności:  
  
-   Sprawdź `deploymentProvider` adres URL w manifeście rozmieszczenia. Upewnij się, czy aktualizujesz bitów w tej samej lokalizacji który `deploymentProvider` wskazuje.  
  
-   Sprawdź interwał aktualizacji w manifeście rozmieszczenia. Jeśli tego interwału wynosi interwału, takich jak jeden raz co sześć godzin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie będą skanować aktualizacji, dopóki ten interwał minął. Możesz zmienić manifestu do skanowania w poszukiwaniu aktualizacji każdym uruchomieniu aplikacji. Zmiana interwału aktualizacji jest to wygodny sposób w czasie tworzenia, aby sprawdzić aktualizacje są instalowane, ale jego spowalnia aktywacji aplikacji.  
  
-   Spróbuj ponownie uruchomić aplikację w Start menu. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]może wykryć aktualizacji w tle, ale zostanie monit o zainstalowanie usługi bits dalej aktywacji.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Podczas aktualizacji wystąpi błąd, który ma następujący wpis dziennika: "odwołanie w rozmieszczeniu nie pasuje do tożsamości zdefiniowanej w manifeście aplikacji"  
 Ten błąd może wystąpić, ponieważ ręcznej edycji manifesty wdrażania i aplikacji, a spowodował opis tożsamość zestawu w manifeście jeden zostać zsynchronizowany z innych. Tożsamość zestawu składa się z jego nazwę, wersję, kulturę i token klucza publicznego. Sprawdź opisy tożsamości w manifestach sieci i rozwiąż wszystkie problemy dotyczące różnic.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Po raz pierwszy aktywacji z dysku CD-ROM lub na dysku lokalnym zakończy się pomyślnie, ale nie powiedzie się kolejne aktywacji z Start Menu  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]używa adres URL dostawcy wdrożenia do otrzymywania aktualizacji dla aplikacji. Sprawdź, czy lokalizacji, która wskazuje adres URL jest poprawny.  
  
#### <a name="error-cannot-start-the-application"></a>Błąd: "nie można uruchomić aplikacji"  
 Ten komunikat o błędzie zwykle wskazuje, że występuje problem instalację tej aplikacji do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowywania. Aplikacja zawiera błąd lub magazyn jest uszkodzony. Plik dziennika może stwierdzić, którym wystąpił błąd.  
  
 Należy wykonać następujące czynności:  
  
-   Sprawdź, czy tożsamość manifestu rozmieszczenia, tożsamość w manifeście aplikacji i tożsamości aplikacji głównej EXE są unikatowe.  
  
-   Sprawdź czy ścieżki do pliku nie może przekraczać 100 znaków. Jeśli aplikacja zawiera ścieżki do plików, które są zbyt długie, może przekroczyć ograniczenia maksymalną ścieżkę, którą można przechowywać. Spróbuj skrócić ścieżki i ponownie zainstalować.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>PrivatePath w pliku konfiguracyjnym aplikacji nie są one honorowane  
 Aby użyć PrivatePath (Fusion sondowania ścieżek), aplikacja musi żądać uprawnienia pełnego zaufania. Spróbuj zmienić manifest aplikacji do żądania pełnego zaufania, a następnie spróbuj ponownie.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Podczas odinstalowywania pojawi się komunikat, "Nie udało się odinstalować aplikację"  
 Zazwyczaj ten komunikat oznacza, że aplikacja została już usunięta lub magazyn jest uszkodzony. Po kliknięciu **OK**, **Dodaj/Usuń programy** wpis zostanie usunięty.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Podczas instalacji pojawi się komunikat z informacją, że nie są zainstalowane zależności platformy  
 Brak wstępnie wymaganego w GAC (Globalna pamięć podręczna zestawów) aplikacja wymaga, aby uruchomić.  
  
## <a name="publishing-with-visual-studio"></a>Publikowanie za pomocą programu Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Publikowanie w programie Visual Studio nie powiedzie się  
 Upewnij się, że użytkownik ma prawo do publikowania na serwerze, który ma być przeznaczona dla. Na przykład jeśli użytkownik jest zalogowany na komputerze serwera terminali jako zwykłego użytkownika, nie jako administrator, prawdopodobnie będzie nie masz uprawnienia wymagane do publikowania na lokalnym serwerze sieci Web.  
  
 W przypadku publikowania przy użyciu adresu URL, upewnij się, że komputer docelowy ma włączonych rozszerzeń serwera FrontPage.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Komunikat o błędzie: Nie można utworzyć witryny sieci Web "\<lokacji >'. Składniki komunikacji z rozszerzeń serwera FrontPage nie są zainstalowane.  
 Upewnij się, że masz Microsoft Visual Studio Web tworzenia składnika zainstalowany na komputerze, który jest publikowana z. W przypadku użytkowników Express ten składnik nie jest zainstalowany domyślnie. Aby uzyskać więcej informacji, zobacz [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Komunikat o błędzie: Nie można odnaleźć pliku "Microsoft.Windows.Common — formanty, wersja 6.0.0.0, Culture = = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, typ = win32"  
 Ten komunikat o błędzie pojawia się podczas próby opublikowania aplikacji WPF przy włączonej funkcji stylów wizualnych. Aby rozwiązać ten problem, zobacz [porady: publikowanie aplikacji WPF z włączoną Visual Style](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Przy użyciu obraz  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Próbowano zalogować się przy użyciu certyfikatu w magazynie certyfikatów i odebranego komunikatu puste pola  
 W **podpisywanie** okno dialogowe, musi:  
  
-   Wybierz **Zaloguj się przy użyciu certyfikatu przechowywanej**, i  
  
-   Wybierz certyfikat z listy; pierwszy certyfikat nie jest ustawieniem domyślnym.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Kliknięcie przycisku "Znak nie" powoduje zgłoszenie wyjątku  
 Ten problem jest znaną usterką. Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty są wymagane do podpisania. Po prostu wybierz jedną z opcji podpisywania, a następnie kliknij przycisk **OK**.  
  
## <a name="additional-errors"></a>Dodatkowe błędy  
 W poniższej tabeli przedstawiono niektóre typowe komunikaty o błędach, które użytkownik komputera klienckiego może zostać wyświetlony, gdy użytkownik instaluje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Każdy komunikat o błędzie jest wyświetlana obok opis najbardziej prawdopodobną przyczyną tego błędu.  
  
|Komunikat o błędzie|Opis|  
|-------------------|-----------------|  
|Nie można uruchomić aplikacji. Skontaktuj się z wydawcą aplikacji.<br /><br /> Nie można uruchomić aplikacji. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji.|Są to ogólne komunikaty o błędach występujących, gdy nie można uruchomić aplikacji, a nie inne przyczyny można znaleźć. Często oznacza to, że aplikacja jakiś sposób jest uszkodzony lub że [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] magazyn jest uszkodzony.|  
|Nie można kontynuować. Aplikacja jest nieprawidłowo sformatowana. Aby uzyskać pomoc, skontaktuj się z wydawcą aplikacji.<br /><br /> Sprawdzenie poprawności aplikacji nie powiodła się. Nie można kontynuować.<br /><br /> Nie można pobrać plików aplikacji. Nastąpiło uszkodzenie plików podczas wdrażania.|Jeden z plików manifestu we wdrożeniu składnia jest nieprawidłowa lub zawiera wartość skrótu, która nie może zostać uzgodnione z odpowiedniego pliku. Ten błąd może również wskazywać, że manifest osadzone wewnątrz zestawu jest uszkodzony. Utwórz ponownie wdrożenia i ponownie skompilować aplikację, lub Znajdź, a ręcznie usuń błędy w manifestach użytkownika.|  
|Nie można pobrać aplikacji. Błąd uwierzytelniania.<br /><br /> Instalacja aplikacji nie powiodła się. Nie można zlokalizować plików aplikacji na serwerze. Aby uzyskać pomoc, skontaktuj się z wydawcą aplikacji lub administratorem.|Nie można pobrać co najmniej jeden plik we wdrożeniu, ponieważ nie masz uprawnień dostępu do nich. Może to być spowodowane błędem 403 Zabroniony zwracanych przez serwer sieci Web, które mogą wystąpić, jeśli jeden z plików w danym wdrożeniu kończy się rozszerzeniem sprawia, że serwer sieci Web traktować go jako plik chroniony. Ponadto katalogu, który zawiera jeden lub więcej plików aplikacji może wymagać nazwy użytkownika i hasła w celu uzyskania dostępu.|  
|Nie można pobrać aplikacji. Brak wymaganych plików. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji lub administratorem systemu.|Nie można odnaleźć jednego lub więcej pliki wymienione w manifeście aplikacji na serwerze. Sprawdź, czy zostały przekazane pliki zależne wszystkie wdrożenia i spróbuj ponownie.|  
|Pobranie aplikacji nie powiodła się. Sprawdź połączenie sieciowe, lub skontaktuj się z administratorem systemu lub usługodawcą sieciowym.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Nie można ustanowić połączenia sieciowego z serwerem. Sprawdź dostępność serwera i stan sieci.|  
|URLDownloadToCacheFile nie powiodło się z HRESULT "\<liczba >". Wystąpił błąd podczas próby pobrania "\<pliku >".|Jeśli użytkownik ustawił opcji zaawansowanych zabezpieczeń programu Internet Explorer "Ostrzegaj przy zmianie i nie tryb bezpieczny" na komputerze docelowym wdrożenia, a Instalator adres URL aplikacji ClickOnce, instalowana jest przekierowywany od niezabezpieczonego do zabezpieczenia witryny (lub odwrotnie), instalacja zakończy się niepowodzeniem ponieważ ostrzeżenie programu Internet Explorer przerywa go.<br /><br /> Aby rozwiązać ten problem, wykonaj jedną z następujących czynności:<br /><br /> — Usuń zaznaczenie opcji zabezpieczeń.<br />— Upewnić się, że adres URL instalacji nie zostanie przekierowana w taki sposób, który zmienia trybów.<br />-Przekierowywanie całkowicie usunąć, a następnie wskaż adresu URL instalacji.|  
|Wystąpił błąd podczas zapisu na dysku twardym. Mogą być niewystarczające miejsce dostępne na dysku. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji lub administratorem systemu.|Może to wskazywać na dysku jest za mało miejsca do przechowywania aplikacji, ale również może wskazywać bardziej ogólne błąd We/Wy podczas próby zapisywania plików aplikacji na dysku.|  
|Nie można uruchomić aplikacji. Na dysku nie jest za mało dostępnego miejsca.|Dysk twardy jest zapełniony. Wyczyść poza miejsca i spróbuj ponownie uruchomić aplikację.|  
|Za dużo wdrożonej nastąpiła próba załadowania jednocześnie.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ogranicza liczbę różnych aplikacji, które można uruchomić w tym samym czasie. Jest to przede wszystkim do ochrony przed złośliwymi próbami podżegały ataków typu "odmowa usługi" na lokalny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usługi; użytkowników, którzy spróbuj uruchomić tej samej aplikacji, w krótkim przedziale czasu, spowoduje tylko utworzenie jednego wystąpienia aplikacja.|  
|Skróty nie można uaktywnić za pośrednictwem sieci.|Skróty do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację można uruchomić tylko na lokalnym dysku twardym. Ich nie można uruchomić, otwierając adres URL, który wskazuje plik skrótu, na serwerze zdalnym.|  
|Aplikacja jest zbyt duży, aby uruchomić w trybie online w częściowej relacji zaufania. Aby uzyskać pomoc, skontaktuj się z dostawcą aplikacji lub administratorem systemu.|Aplikację, która działa w częściowej relacji zaufania nie może być większa niż połowy rozmiaru przydziału aplikacji online, której wartością domyślną jest 250 MB.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)