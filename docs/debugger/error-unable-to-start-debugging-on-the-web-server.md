---
title: 'Błąd: Nie można rozpocząć debugowania na serwerze sieci Web | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 05/23/2017
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 459df1ca9ffed246116c71adac8a38039b6602ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Błąd: Nie można rozpocząć debugowania na serwerze sieci Web

Podczas debugowania aplikacji ASP.NET uruchomionych na serwerze sieci Web, może wystąpić ten komunikat o błędzie: `Unable to start debugging on the Web server`.

Często ten błąd występuje, ponieważ zmiana konfiguracji lub błąd wystąpił, który wymaga zaktualizowania pul aplikacji i/lub resetowanie usług IIS. Usługi IIS można zresetować Otwieranie wiersza polecenia o podniesionych uprawnieniach i wpisując `iisreset`. 

## <a name="specificerrors"></a>Co to jest szczegółowy komunikat o błędzie?

`Unable to start debugging on the Web server` Wiadomości jest rodzajowy. Zazwyczaj bardziej szczegółowych komunikatów jest uwzględniona w parametrach błąd i zidentyfikować przyczynę problemu lub Wyszukaj bardziej dokładne poprawkę, mogą pomóc. Poniżej przedstawiono kilka częściej komunikaty o błędach, które są dołączane do głównego komunikat:

- [Usługi IIS nie wyświetlają odpowiadający uruchomienie witryny sieci Web adres url](#IISlist)
- [Serwer sieci web nie jest poprawnie skonfigurowany.](#web_server_config)
- [Nie można nawiązać połączenia z serwer sieci Web](#unabletoconnect)
- [Serwer sieci web nie odpowiedział w określonym czasie](#webservertimeout)
- [Microsoft visual studio zdalne debugowanie monitor(msvsmon.exe) nie ma być uruchomiona na komputerze zdalnym](#msvsmon)
- [Serwer zdalny zwrócił błąd](#server_error)
- [Nie można rozpocząć debugowania ASP.NET](#aspnet)
- [Debuger nie może połączyć się z komputerem zdalnym](#cannot_connect)
- [Zobacz Pomoc dla typowych błędów konfiguracji. Uruchamianie strony sieci Web poza debugerem może dostarczyć więcej informacji.](#see_help)

## <a name="IISlist"></a> Usługi IIS nie wyświetlają odpowiadający uruchomienie witryny sieci Web adres url

- Uruchom ponownie program Visual Studio jako Administrator, a następnie spróbuj ponownie debugowanie. (W niektórych scenariuszach debugowania ASP.NET wymaga podwyższonego poziomu uprawnień.)

    Można skonfigurować Visual Studio, aby zawsze uruchomić jako Administrator, klikając prawym przyciskiem myszy ikonę skrótu programu Visual Studio, wybierając **właściwości > Zaawansowane**i wybierając są zawsze uruchamiane z uprawnieniami administratora.

## <a name="web_server_config"></a> Serwer sieci web nie jest poprawnie skonfigurowany.

- Zobacz [błąd: serwer sieci web nie jest poprawnie skonfigurowany](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Nie można nawiązać połączenia z serwer sieci Web

- Czy na uruchamianie programu Visual Studio i serwera sieci Web na tym samym komputerze i debugowanie przy użyciu **F5** (zamiast **dołączyć do procesu**)? Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany do łączenia się z właściwym serwerem sieci Web i uruchamianie adresu URL. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** zależnie od typu projektu. W projekcie formularzy sieci Web otwórz **strony właściwości > opcje Start > serwera**.)

- W przeciwnym razie ponownie uruchom puli aplikacji, a następnie Zresetuj usługi IIS. Aby uzyskać więcej informacji, zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Serwer sieci web nie odpowiedział w określonym czasie

- Zresetuj usługi IIS, a następnie spróbuj ponownie debugowanie. Wiele wystąpień debugera może zostać dołączony do procesu IIS; Resetowanie kończy je. Aby uzyskać więcej informacji, zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Microsoft visual studio zdalne debugowanie monitor(msvsmon.exe) nie ma być uruchomiona na komputerze zdalnym

- Jeśli debugowania na zdalnym komputerze, upewnij się, masz [zainstalowane i działają zdalny debuger](../debugger/remote-debugging.md). Jeśli komunikat nazwa zapora, upewnij się, [Popraw portów w zaporze](../debugger/remote-debugger-port-assignments.md) są otwarte, zwłaszcza, jeśli używasz zapory innych firm.
- Jeśli korzystasz z pliku HOSTS, upewnij się, że został on poprawnie skonfigurowany. Na przykład, jeśli debugowanie przy użyciu **F5** (zamiast **dołączyć do procesu**), HOSTY pliku musi zawierać ten sam adres URL projektu, jak właściwości projektu, **właściwości > sieci Web > serwerów**  lub **właściwości > debugowanie**w zależności od typu projektu.

## <a name="server_error"></a> Serwer zdalny zwrócił błąd

Sprawdź Twojej [pliku dziennika usług IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) kody błędów podrzędne i dodatkowe informacje oraz tej usługi IIS 7 [wpis w blogu](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Ponadto poniżej przedstawiono niektóre często występujące kody błędów i kilka sugestii.
- (403) zabroniony. Istnieje wiele możliwych przyczyn tego błędu, dlatego należy sprawdzić plik dziennika i ustawienia zabezpieczeń programu IIS dla witryny sieci web. Upewnij się, że plik web.config zawiera `debug=true` w elemencie kompilacji. Upewnij się, że folder aplikacji sieci Web ma odpowiednie uprawnienia i czy w konfiguracji puli aplikacji jest poprawna, (mógł ulec zmianie hasła). Zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck). Jeśli te ustawienia są już prawidłowe, i debugowania lokalnie, Sprawdź również, że łączysz się z właściwym serwerem typu i adres URL (w **właściwości > sieci Web > serwery** lub **właściwości > debugowanie**, w zależności od typu projektu).
- (503) serwer jest niedostępny. Pula aplikacji może mieć została zatrzymana z powodu zmiany konfiguracji lub błąd. Ponowne uruchomienie puli aplikacji.
- (404) nie można odnaleźć. Upewnij się, że pula aplikacji jest skonfigurowana dla odpowiedniej wersji programu ASP.NET.

## <a name="aspnet"></a> Nie można rozpocząć debugowania ASP.NET

- Ponowne uruchomienie puli aplikacji i Zresetuj usługi IIS. Aby uzyskać więcej informacji, zobacz [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).
- Jeśli przeprowadzasz ponownie zapisuje adresu URL, test podstawowy plik web.config z nie modyfikacji oprogramowania adresu URL. Zobacz **Uwaga** o adresie URL przepisywania moduł w [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Debuger nie może połączyć się z komputerem zdalnym

Jeśli debugowanie lokalnie ten błąd może wystąpić, ponieważ program Visual Studio jest 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania aplikacji 64-bitowych. Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany do nawiązania połączenia prawidłowe serwera sieci Web i adres URL. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** zależnie od typu projektu.)

Jeśli korzystasz z pliku HOSTS, upewnij się, że został on poprawnie skonfigurowany. Na przykład hostów pliku musi zawierać ten sam adres URL projektu, jak właściwości projektu, **właściwości > sieci Web > serwery** lub **właściwości > debugowanie**w zależności od typu projektu.

## <a name="see_help"></a> Zobacz Pomoc dla typowych błędów konfiguracji. Uruchamianie strony sieci Web poza debugerem może dostarczyć więcej informacji.

- Używasz programu Visual Studio i serwera sieci Web na tym samym komputerze? Otwórz właściwości projektu i upewnij się, że projekt jest skonfigurowany do łączenia się z właściwym serwerem sieci Web i uruchamianie adresu URL. (Otwórz **właściwości > sieci Web > serwery** lub **właściwości > debugowanie** zależnie od typu projektu.)

- Jeśli to nie pomoże, lub debugowania zdalnie, wykonaj czynności opisane w [Sprawdź konfigurację usług IIS](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Sprawdź konfigurację usług IIS

Po wykonaniu kroków szczegółowe tutaj, aby rozwiązać ten problem, a przed podjęciem ponownej próby debugowania również może być konieczne zresetowanie usług IIS. Możesz to zrobić Otwieranie wiersza polecenia o podniesionych uprawnieniach i wpisując `iisreset`. 

* Zatrzymaj i uruchom ponownie pul aplikacji usług IIS, a następnie spróbuj ponownie. 

    Pula aplikacji może zatrzymano w wyniku błędu. Lub innego zmian konfiguracji przez użytkownika może wymagać zatrzymanie i ponowne uruchomienie puli aplikacji.
    
    > [!NOTE]
    > Śledzi Zatrzymywanie puli aplikacji, może być konieczne odinstalowanie moduł ponowne zapisywanie adresów URL w Panelu sterowania. Można ponownie zainstalować go za pomocą Instalatora platformy sieci Web (WebPI). Ten problem może wystąpić po uaktualnieniu znaczących systemu.

* Sprawdź konfigurację puli aplikacji, napraw go w razie potrzeby, a następnie spróbuj ponownie.

    Pula aplikacji może być skonfigurowany dla wersji platformy ASP.NET, która jest niezgodna z projektu programu Visual Studio. Zaktualizuj wersję platformy ASP.NET w puli aplikacji, a następnie uruchom go ponownie. Aby uzyskać szczegółowe informacje, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ponadto poświadczenia hasła zostały zmienione, należy zaktualizować je w puli aplikacji lub witryny sieci Web.  W puli aplikacji, zaktualizuj poświadczenia w **Zaawansowane ustawienia > Model procesu > tożsamości**. Witryny sieci Web, zaktualizuj poświadczenia w **podstawowe ustawienia > Połącz się jako...** . Ponowne uruchomienie puli aplikacji.
    
* Sprawdź, czy folder aplikacji sieci Web ma odpowiednie uprawnienia.

    Upewnij się, że zapewniają IIS_IUSRS, IUSR, lub określonego użytkownika skojarzony z [puli aplikacji](/iis/manage/configuring-security/application-pool-identities) Odczyt i wykonywanie uprawnień dla folderu aplikacji sieci Web. Usuń problem i ponownie uruchom pulę aplikacji.

* Upewnij się, zainstalowanie odpowiedniej wersji programu ASP.NET w usługach IIS.

    Niezgodne wersje platformy ASP.NET w usługach IIS i projektu programu Visual Studio może być przyczyną tego problemu. Konieczne może być ustawiona wersja programu w pliku web.config. Aby zainstalować program ASP.NET w usługach IIS, należy użyć [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Zobacz też [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub dla platformy ASP.NET Core [hosta w systemie Windows z programem IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Usuń błędy uwierzytelniania, jeśli używane są tylko dla adresu IP

     Domyślnie adresy IP są uważane za część Internetu, a uwierzytelnianie NTLM nie odbywa się za pośrednictwem Internetu. Skonfigurowanie witryny sieci web w usługach IIS, aby wymagać uwierzytelniania to uwierzytelnianie nie powiedzie się. Aby rozwiązać ten problem, należy określić nazwę komputera zdalnego, zamiast adresu IP.
     
## <a name="other-causes"></a>Inne przyczyny

Jeśli konfiguracji usług IIS nie jest przyczyną problemu, spróbuj wykonać następujące kroki:

- Uruchom ponownie program Visual Studio z uprawnieniami administratora i spróbuj ponownie.

    Sytuacje debugowania ASP.NET, takich jak za pomocą narzędzia Web Deploy wymaga podwyższonego poziomu uprawnień dla programu Visual Studio.
    
- Jeśli wiele wystąpień programu Visual Studio jest uruchomiony, ponownie otwórz projekt w jedno wystąpienie programu Visual Studio (z uprawnieniami administratora) i spróbuj ponownie.

- Jeśli używasz pliku HOSTS z adresów lokalnych, spróbuj użyć adres sprzężenia zwrotnego zamiast adresu IP na komputerze.

    Jeśli nie używasz adresów lokalnych, upewnij się, plik HOSTS zawiera ten sam adres URL projektu, jak właściwości projektu, **właściwości > sieci Web > serwerów** lub **właściwości > debugowania**, w zależności od Twojej Typ projektu.

## <a name="more-troubleshooting-steps"></a>Więcej kroki rozwiązywania problemów

* Przełącz stronę localhost w przeglądarce na serwerze.

     Jeśli usługi IIS nie jest poprawnie zainstalowany, należy pobrać błędy podczas wpisywania tekstu `http://localhost` w przeglądarce.
     
     Aby uzyskać więcej informacji na temat wdrażania usług IIS, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) i dla platformy ASP.NET Core [hosta w systemie Windows z programem IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Tworzenie podstawowej aplikacji ASP.NET na serwerze (lub przy użyciu pliku web.config podstawowe).

    Jeśli nie można pobrać aplikację do pracy z debugerem, spróbuj utworzyć podstawowej aplikacji ASP.NET lokalnie na serwerze, a następnie spróbuj do debugowania aplikacji basic. (Możesz użyć domyślnego szablonu platformy ASP.NET MVC.) Jeśli można debugować Podstawowa aplikacja, która może ułatwić identyfikację co różni się między dwie konfiguracje. Poszukaj różnice w ustawieniach w pliku web.config, takie jak reguły ponowne zapisywanie adresów URL.

## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)