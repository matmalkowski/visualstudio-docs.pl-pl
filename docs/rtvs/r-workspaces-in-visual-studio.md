---
title: Obszary robocze, R Tools for Visual Studio | Dokumentacja firmy Microsoft
description: "Jak kontrolować, gdy kod języka R jest uruchamiana za pomocą obszarów roboczych w programie Visual Studio."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: c3e31fcd0011b01352da49a419e903158cd2792a
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="controlling-where-r-code-runs-with-workspaces"></a>Kontrolowanie, których R kod jest uruchamiany z obszarami roboczymi

Obszar roboczy R narzędzi dla programu Visual Studio (RTVS) umożliwia skonfigurowanie, którym sesji R jest uruchomiona, która może się zdarzyć na komputerach lokalnych i zdalnych. Celem jest umożliwienie użytkownikom pracy na za pomocą środowiska użytkownika można porównywać pod względem daje możliwość zalet potencjalnie wydajniejsze komputery oparte na chmurze.

Aby otworzyć **obszarów roboczych** okna, użyj **narzędzia R > Windows > obszary robocze** polecenie lub naciśnij klawisze Ctrl + 9.

![Okno obszarów roboczych w R Tools for Visual Studio (VS2017)](media/workspaces-window.png)

W tym oknie zielonym znacznikiem wyboru wskazuje aktywnego obszaru roboczego, z którym powiązany jest RTVS. Zaznaczenie niebieską strzałką ustawia aktywnego obszaru roboczego. Ikona ustawień (koło zębate) po prawej stronie w każdym obszarze roboczym umożliwia zmianę jego nazwy, lokalizacji i argumenty wiersza polecenia. Czerwony znak X usuwa dodane ręcznie obszaru roboczego.

W tym temacie:

- [Zapisywanie i zresetowanie obszaru roboczego](#saving-and-resetting-a-workspace)
- [Lokalne obszary robocze](#local-workspaces)
- [Zdalnych obszarów roboczych](#remote-workspaces)
- [Logowania zdalnego obszaru roboczego](#remote-workspace-logon)
- [Przełączanie między obszarami roboczymi](#switching-between-workspaces)
- [Katalogi na komputerach lokalnych i zdalnych](#directories-on-local-and-remote-computers)
- [Kopiowanie plików projektu na zdalnych obszarów roboczych](#copying-project-files-to-remote-workspaces)
- [Kopiowanie plików ze zdalnego obszaru roboczego](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Zapisywanie i zresetowanie obszaru roboczego

Domyślnie RTVS nie zostanie zapisany stan obszaru roboczego po zamknięciu i ponownie otwórz projekt. Możesz zmienić to zachowanie, jednak za pomocą [Opcje obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

**Narzędzia R > sesji > Resetuj** polecenia i resetowania przycisku paska narzędzi w oknie interaktywnym w dowolnej chwili również przywrócić stan obszaru roboczego. Z zdalnych obszarów roboczych resetowania usuwa utworzenia najpierw nawiązywania połączenia z serwerem zdalnym skutecznie usuwa wszystkie pliki, które współdzielenia profilu użytkownika.

## <a name="local-workspaces"></a>Lokalne obszary robocze

Na liście lokalnych obszarach roboczych zostaną wyświetlone wszystkie tłumaczy R zainstalowanych na komputerze. 

Po uruchomieniu programu Visual Studio spróbuje automatycznie wykrywa wszystkie wersje R zainstalowanego przeglądając `HKEY_LOCAL_MACHINE\Software\R-Core\` klucza rejestru. Ponieważ ten test jest wykonywana tylko podczas uruchamiania, musisz ponownie uruchomić program Visual Studio po zainstalowaniu nowego interpreter języka R.

RTVS może nie wykrywać interpreter języka R zainstalowanego w niestandardowy sposób (na przykład, gdy po prostu kopiowanie plików do folderu zamiast uruchamiania Instalatora). W takim przypadku ręcznie utworzyć nowego lokalnego obszaru roboczego R w następujący sposób:

1. Wybierz **Dodaj** przycisk w oknie obszarów roboczych.
1. Wprowadź nazwę dla nowego obszaru roboczego.
1. Wprowadź ścieżkę do folderu głównego R, który zawiera `bin` folder o interpreter, oraz opcjonalne argumenty wiersza polecenia, które zostaną przekazane do interpretera po jej uruchomieniu przez RTVS.
1. Wybierz **zapisać** po zakończeniu.

![Dodawanie nowego obszaru roboczego](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Zdalnych obszarów roboczych

Zdalnych obszarów roboczych pozwalają połączyć się z sesją R na komputerze zdalnym. (Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md) dotyczące sposobu konfigurowania komputera do tego celu.)

Visual Studio nie jest wykrywany zdalnych obszarów roboczych, dlatego należy dodać je ręcznie przy użyciu **Dodaj** przycisk w oknie obszarów roboczych, zgodnie z opisem w poprzedniej sekcji. W takim przypadku wprowadź identyfikator URI na komputerze zdalnym, a nie ścieżką lokalną.

> [!Important]
> Zdalnych obszarów roboczych są identyfikowane przez identyfikator URI który *musi używać protokołu HTTPS* do zapewnienia prywatności i integralności komunikacji z komputerem zdalnym. Program Visual Studio nie może połączyć się z komputerem zdalnym, który nie obsługuje protokołu HTTPS.

> [!Note]
> Zdalnych obszarów roboczych są efektywne w wersji zapoznawczej. Firma Microsoft pracuje nad lepszej realizacji problemu synchronizacji plików w przyszłości i Witamy pomysły i opinii.

## <a name="remote-workspace-logon"></a>Logowania zdalnego obszaru roboczego

Możesz korzystać nazwę użytkownika i hasło do logowania do zdalnego obszaru roboczego.

### <a name="logon-to-windows-workspace"></a>Zaloguj się do obszaru roboczego systemu Windows

Jeśli komputer zdalny jest skonfigurowana do używania konta domeny, można użyć logowania domeny do dostępu zdalnego obszaru roboczego. Jeśli nie, to należy użyć `machine-name\username` format, aby zalogować się przy użyciu konta komputera na komputerze zdalnym.

### <a name="logon-to-linux-workspace"></a>Zaloguj się do obszaru roboczego systemu Linux

Do logowania się do użycia konta linux `<<unix>>\username` format. Na przykład, jeśli masz konto o nazwie `ruser`, a następnie wpisz użytkownika jako `<<unix>>\ruser`.

## <a name="switching-between-workspaces"></a>Przełączanie między obszarami roboczymi

RTVS jest powiązany z tylko jednego obszaru roboczego w czasie. Powiązane obszaru roboczego jest określane przez małe zielonym znacznikiem wyboru w oknie obszarów roboczych. Domyślnie RTVS wiąże się z ostatnim Otwórz lokalnego obszaru roboczego w poprzedniej sesji.

Aby zmienić aktywnego obszaru roboczego, wybierz niebieską strzałką obok żądanego obszaru roboczego. W ten sposób wyświetli monit o zapisanie sesję, kończy bieżący obszar roboczy, a następnie przełącza na nową.

> [!Tip]
> Aby wyłączyć zapisywanie monitu, wybierz pozycję **R Narzędzia > Opcje** polecenia i ustaw **Pokaż okno dialogowe potwierdzenia przed przełączeniem obszarów roboczych** opcji w celu `No`. Zobacz [Opcje obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

Jeśli spróbujesz przełączyć się do lokalnego obszaru roboczego, który został odinstalowany, lub do zdalnego obszaru roboczego, który jest niedostępny, RTVS może być powiązana z dowolnym obszarze roboczym. W związku z tym zostanie wyświetlony błąd, po wprowadzeniu kodu w oknie interaktywnym lub spróbuj uruchomić kod, w przeciwnym razie:

![Błąd podczas roboczym nie jest powiązany z RTVS](media/workspaces-disconnected-interactive-window.png)

Aby rozwiązać ten problem, przejdź do innego obszaru roboczego w oknie obszarów roboczych. Jeśli brak obszarów roboczych są dostępne, musisz zainstalować interpreter języka R. Można też spróbować ponownego uruchamiania programu Visual Studio, jeśli po zainstalowaniu tłumacza podczas pracy programu Visual Studio.

### <a name="switching-to-a-remote-workspace"></a>Przełączanie do zdalnego obszaru roboczego

RTVS monit o poświadczenia podczas pierwszego połączenia zdalnego obszaru roboczego, a następnie buforuje tych poświadczeń (przy użyciu bezpiecznego skrytka na poświadczenia systemu Windows) dla nowszej sesji. Komunikacja z serwerem zdalnym następnie odbywa się bezpiecznie za pośrednictwem protokołu HTTPS (co jest wymagane).

W zależności od konfiguracji serwera zobaczysz ostrzeżenie podczas łączenia z tym odczyty certyfikatu "certyfikat zabezpieczeń przedstawiony przez usługi zdalnej R nie Zezwalaj firmie Microsoft w celu potwierdzenia, że w rzeczywistości łączysz się z komputera (nazwa)".

![Ostrzeżenie certyfikatu z podpisem własnym podczas nawiązywania połączenia zdalnego obszaru roboczego](media/workspaces-remote-self-signed-certificate-warning.png)

Certyfikat jest dokumentem przedstawione RTVS przez komputera, na którym próbujesz nawiązać połączenie. Certyfikat zawiera pole, które identyfikuje identyfikator URI tego komputera. Ostrzeżenie jest wyświetlane, gdy RTVS wykryje niezgodność między identyfikator URI w certyfikat i identyfikator URI używany do łączenia się z komputerem wskazująca, że serwera zabezpieczeń mogły zostać złamane.

Jednak to ostrzeżenie pojawia się również czy *certyfikatu z podpisem własnym* użyto, aby włączyć protokół HTTPS na komputerze zdalnym, zamiast korzystać z zaufanego dostawcę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Katalogi na komputerach lokalnych i zdalnych

Domyślnie po uruchomieniu nowego interpreter języka R w lokalnym obszarze roboczym bieżący katalog roboczy jest `%userprofile%\Documents`. Można zmienić katalogu w dowolnej chwili za pomocą **narzędzia R > katalog roboczy** polecenia, lub przez kliknięcie prawym przyciskiem myszy projekt w Eksploratorze rozwiązań w usłudze Visual Studio i wybraniu poleceń, takich jak **ustawić pracy katalogu tutaj**.

Po pierwsze połączenia z komputerem zdalnym RTVS automatycznie tworzy profil użytkownika oparte na poświadczenia, który określa katalog roboczy do `Documents` folderu przy użyciu tego profilu. Ten folder jest używany dla wszystkich kolejnych sesji zdalnych, które używają tych samych poświadczeń. 

W związku z tym dokładnej lokalizacji, w którym jest uruchamiany kod może się różnić między lokalnych i zdalnych obszarów roboczych. W kodzie następnie należy zawsze używać względnych ścieżek do plików danych i takie tak, aby kod przenośny między obszarami roboczymi.

Należy pamiętać, że z zdalnych obszarów roboczych, wszystkie pliki w katalogu roboczym pozostają bez zmian we wszystkich sesjach dla tego samego profilu użytkownika. Jak wspomniano wcześniej, należy usunąć te pliki, za pomocą **narzędzia R > sesji > Resetuj** polecenia (lub przycisk reset w oknie interaktywnym) podczas korzystania ze zdalnego obszaru roboczego. To polecenie usuwa ponownie profilu użytkownika na serwerze, co jest tworzona ponownie po ponownym.

## <a name="copying-project-files-to-remote-workspaces"></a>Kopiowanie plików projektu na zdalnych obszarów roboczych

Podczas pracy z projektami R w programie Visual Studio, komputer lokalny zawsze zawiera najnowsze pliki projektu nawet wtedy, gdy używasz zdalnego obszaru roboczego. Oznacza to po otwarciu projektu w programie Visual Studio (która zazwyczaj oznacza to, otwierając rozwiązanie zawierające projekt) RTVS zakłada projektu zawartości znajdują się na komputerze lokalnym całkowicie. Zdalnego obszaru roboczego jest włączona, po prostu tymczasowego hosta dla plików projektu i wszystkie dane wyjściowe z kodu. Oznacza to, na przykład, że podczas ładowania pliku przy użyciu `source` w oknie interaktywnym ten plik już należy na komputerze zdalnym w ścieżce podasz lub musi być w bieżącym katalogu roboczym zdalnego interpretera R (zestaw z `setwd()`</c2>funkcji).

Pliki są kopiowane do zdalnego serwera:

- Aby pracować z plikami zdalnie za pośrednictwem okno interaktywne, należy najpierw skopiować je ręcznie prawym przyciskiem myszy tych plików (lub projekt) w Eksploratorze rozwiązań i wybierając ** wybrane źródło **. Dla poszczególnych plików są kopiowane do katalogu roboczego na serwerze; Podczas kopiowania projektu, RTVS tworzy folder dla projektu.

- Pliki można również skopiować, następnie zaznaczając w Eksploratorze rozwiązań i wybierając **źródła wybrane pliki (s)**. Ta akcja ładuje je do okna interaktywnego i ich działa. Jeśli sesja jest połączony z komputerem zdalnym, pliki są kopiowane najpierw.

- Gdy RTVS jest powiązany z zdalnego obszaru roboczego, a następnie naciśnij klawisz F5, wybierz **Debuguj > Rozpocznij debugowanie**, lub, w przeciwnym razie uruchamianie kodu, RTVS domyślnie kopiuje plik projektu do obszaru roboczego zdalnego automatycznie (zobacz poniżej sposobu kontroli tego zachowania).

- Wszystkie pliki, które już istnieją na serwerze zostaną zastąpione.

> [!Note]
> Ponieważ RTVS niezawodnie nie można przechwycić wszystkie wywołania funkcji R, wywoływanie funkcji takich jak `source()` lub `runApp()` (dla aplikacji obiektowi błyszczący) do interaktywnego okna jest *nie* skopiuj pliki do zdalnego obszaru roboczego.

[Właściwości projektu](r-projects-in-visual-studio.md#project-properties) kontroli czy RTVS kopiuje pliki, gdy projekt jest uruchamiania i dokładnie pliki, które są kopiowane. Aby otworzyć tę stronę, wybierz **projektu > właściwości (nazwa)...**  polecenie menu, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz **właściwości...** .

![Właściwości projektu kartę z transfer plików ustawienia uruchomienia](media/workspaces-remote-file-transfer-filter-settings.png)

W tym miejscu **przesyłać pliki przy uruchomieniu** właściwość określa, czy RTVS automatycznie kopiuje pliki projektu. **Plików do transferu** wartość następnie filtry dokładnie pliki, które są przenoszone. Wartość domyślna to można skopiować tylko `.R`, `.Rmd`, `.sql`, `.md`, i `.cpp` plików. To zachowanie zapobiega przypadkowo kopiowania dużych plików danych na serwer z każdym uruchomiony. 

## <a name="copying-files-from-a-remote-workspace"></a>Kopiowanie plików ze zdalnego obszaru roboczego

Jeśli skrypt R generuje pliki na serwerze, można skopiować te pliki do klienta przy użyciu `rtvs::fetch_file` funkcji. Ta funkcja akceptuje minimum, zdalna ścieżka do pliku, który chcesz skopiować na komputer i opcjonalnie ścieżkę docelową na komputerze. Jeśli ścieżka nie zostanie określona, plik jest kopiowany do Twojej `%userprofile%\Downloads` folderu.
