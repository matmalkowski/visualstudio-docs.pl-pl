---
title: Kontrola wersji TF
description: Łączenie się z Team Foundation Server lub Visual Studio Team Services z kontrolą wersji Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 51d066289809842cd50974cbb37a89bc7a73d5dc
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37438105"
---
# <a name="connecting-to-team-foundation-version-control"></a>Nawiązywanie połączenia z kontrolą wersji Team Foundation 

> [!NOTE]
> **Uwaga**: Obsługa kontroli wersji serwera Team Foundation jest obecnie w wersji zapoznawczej, a niektóre funkcje nie jeszcze w pełni działa. Chętnie poznamy opinii od Ciebie na wszelkie problemy w [społeczności deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html). Zmiany są nadal pochodzić!

Visual Studio Team Services (VSTS) i Team Foundation Server (TFS) zapewnia dwa modele kontroli wersji: Git, która jest rozłożona Kontrola wersji i Team Foundation Version kontroli (TFVC), czyli scentralizowany formant wersji. Ten artykuł zawiera omówienie oraz punkt początkowy dla przy użyciu Team Foundation Version Control za pomocą programu Visual Studio dla komputerów Mac.

## <a name="requirements"></a>Wymagania

* Visual Studio Community, Professional lub Enterprise dla komputerów Mac w wersji 7.5 lub nowszej.
* Visual Studio Team Services lub serwera Team Foundation Server 2013 lub nowszym.
* Projekt w programie Visual Studio Team Services lub Team Foundation Server skonfigurowany do używania kontroli wersji serwera Team Foundation.

## <a name="installation"></a>Instalacja

W programie Visual Studio dla komputerów Mac, wybierz **programu Visual Studio > rozszerzenia...**  z menu. W **galerii** zaznacz **kontroli wersji > kontroli wersji Team Foundation dla TFS i usługą VSTS** i kliknij przycisk **instalacji...** :

  ![Menedżer rozszerzeń](media/tfvc-install.png) 

Postępuj zgodnie z monitami, aby zainstalować rozszerzenie. Po zainstalowaniu, należy ponownie uruchomić środowisko IDE.

## <a name="updating-the-extension"></a>Trwa aktualizowanie rozszerzenia

Okresowo są wprowadzone aktualizacje z rozszerzeniem TFVC. Dostęp do aktualizacji, wybierz **programu Visual Studio > rozszerzenia...**  z menu i wybierzesz **aktualizacje** kartę. Zaznacz rozszerzenie na liście i naciśnij klawisz **aktualizacji** przycisku:

  ![Aktualizacja przedstawiający Menedżer rozszerzenia](media/tfvc-update.png) 

Naciśnij klawisz **zainstalować** w następnym oknie dialogowym odinstalowanie starego pakietu i instalacja nowego.

Aby uzyskać informacji na temat nowości w każdej wersji, zobacz [informacje o wersji](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Za pomocą dodatku

Po zainstalowaniu rozszerzenia wybierz **kontroli wersji > TFS/VSTS > Otwórz ze zdalnego repozytorium** elementu menu. 

Wybierz pozycję Visual Studio Team Services lub serwera Team Foundation Server, aby rozpocząć pracę, a następnie naciśnij klawisz **Kontynuuj**:

  ![Łączenie z serwerem](media/tfvc-choose-server-type.png)

### <a name="vsts-authentication"></a>Uwierzytelnianie usługi VSTS

Po wybraniu projektu, który znajduje się w usłudze VSTS, monit o podanie szczegółów konta Microsoft:

  ![Nawiązać połączenie z serwerem usługi VSTS](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Uwierzytelnianie serwera TFS

Aby połączyć z TFS, wprowadź szczegóły serwera i poświadczenia konta. Wprowadź domenę do użycia uwierzytelniania NTLM, w przeciwnym razie pozostaw puste, aby użyć uwierzytelniania podstawowego. Wybierz **Dodaj serwer**: 

![Zaloguj się do serwera TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Wybieranie projektu

Po użytkownik został pomyślnie uwierzytelniony, można wyświetlić listę repozytoriów, które są skojarzone z kontem w **Otwórz z kontroli źródła** okno dialogowe:

  ![Otwórz z dialogowe kontroli źródła z projektami wyświetlane](media/tfvc-vsts-projects.png)

To okno dialogowe jest zorganizowana przy użyciu następujących węzłów:

- Konto usługi VSTS lub kolekcji — spowoduje to wyświetlenie wszystkich kont, połączone konta Microsoft, w której użytkownik jest zalogowany przy użyciu
- Projekty zespołowe — w ramach każdej usługi VSTS, może mieć wiele projektów zespołowych. Projekt zespołowy jest hostujące kod źródłowy, elementy robocze i automatyczne kompilacje.

W tym momencie wyszukiwanie i filtrowanie według nazwy konta lub projektu.

### <a name="adding-a-new-server"></a>Dodawanie nowego serwera

Aby dodać nowy serwer do listy, naciśnij klawisze **Dodaj hosta** znajdujący się na **Otwórz z kontroli źródła** okno dialogowe:

![Wyróżnione Dodaj przycisk, aby dodać nowy serwer do listy](media/tfvc-add-new-server.png)

Wybierz dostawcę z listy, a następnie wprowadź swoje poświadczenia:

![Okno dialogowe z wyświetloną opcją dostawcy kontroli źródła](media/tfvc-add-new-creds.png)

## <a name="creating-a-new-workspace"></a>Tworzenie nowego obszaru roboczego

Aby rozpocząć pracę z projektem, musisz mieć _obszaru roboczego_. Jeśli nie masz jeszcze obszaru roboczego, możesz utworzyć je z **obszaru roboczego** combobox **Otwórz z kontroli źródła** okno dialogowe:

![Utwórz nową opcję combobox obszaru roboczego](media/tfvc-create-new-workspace.png)

Ustaw nazwę i ścieżkę lokalną dla nowego obszaru roboczego i wybierz **Utwórz obszar roboczy**:

![Wprowadź nazwę i ścieżkę lokalną dla nowego obszaru roboczego](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Za pomocą Eksploratora kodu źródłowego

Po utworzeniu obszaru roboczego i mapowany do projektu, możesz rozpocząć pracę z _Eksploratora kodu źródłowego_.

Aby otworzyć Eksploratora kodu źródłowego, zaznacz **kontroli wersji > TFS/VSTS > Eksploratorze kontroli źródła**:

![Element menu, aby otworzyć Eksploratora kodu źródłowego](media/tfvc-source-control-explorer.png)

Eksplorator kodu źródłowego umożliwia nawigowanie po wszystkich zamapowanych projektów, pliki i foldery. W tym obszarze można również wykonywać wszystkie akcje kontroli podstawowego źródła takie jak:

- Pobierz najnowszą wersję
- Pobieranie określonej wersji
- Ewidencjonowanie i wyewidencjonowywanie plików
- Blokowanie i odblokowywanie plików
- Dodawanie, usuwanie i Zmień nazwy plików
- Wyświetlić historię
- Porównaj zmiany.

Wiele z tych działań są dostępne za pośrednictwem kontekst akcji dla projektu:

![Akcje menu kontekstowe dla projektu](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Zarządzanie obszarami roboczymi

Jeśli nie jest jeszcze utworzyć obszar roboczy, zgodnie z opisem w [tworzenia obszaru roboczego](#creating-a-new-workspace) sekcji, można zauważyć, że Eksplorator kodu źródłowego jest puste:

![Źródło pusty Eksplorator kodu](media/tfvc-setup-empty-sce.png) 

Aby skonfigurować zdalne projektu za pomocą lokalnego obszaru roboczego, użyj następujących kroków:

1. Wybierz **serwera** z pola kombi.
1. Należy pamiętać, że nie ma "żadnych obszarów roboczych" i że ścieżka lokalna jest "Niezamapowany". Wybierz **niezamapowane** łącze, aby wyświetlić **Utwórz nowy obszar roboczy** okna dialogowego.
1. Podaj nazwę obszaru roboczego, a następnie kliknij przycisk **Dodaj Folder pracy** do mapowania projektu do folderu lokalnego na komputerze:
    
    ![Utwórz nowe okno dialogowe obszaru roboczego przedstawiający opcje domyślne](media/tfvc-workspace1.png) 

1. Wybierz folder "$" mapowanie wszystkich projektów zespołowych na serwerze do tego samego obszaru roboczego, lub wybierz pojedynczego projektu, a następnie kliknij przycisk **OK**:
    
    ![Przeglądaj w poszukiwaniu folderu okno dialogowe wyświetloną wszystkie projekty](media/tfvc-workspace2.png) 

1. Wybierz lokalizację na lokalnym komputerze ma projekty, do punktu zarządzania i kliknij **wybierz Folder**.
1. Potwierdź szczegóły nowego obszaru roboczego, naciskając klawisz **OK**
    
    ![Tworzenie okna dialogowego Nowy obszar roboczy za pomocą folderu roboczego dodano](media/tfvc-workspace3.png) 

Po skonfigurowaniu obszaru roboczego może można zmienić ani usunąć, klikając **zarządzanie obszarami roboczymi** przycisku w Eksploratorze kodu źródłowego.

![Zarządzanie obszarami roboczymi](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="problems-using-basic-authentication"></a>Problemów przy użyciu uwierzytelniania podstawowego

Następujące opcje może służyć do uwierzytelniania z serwerem:

- OAuth
- Podstawowy
- Uwierzytelnianie NTLM

Do korzystania z uwierzytelniania podstawowego jest niezbędne do włączenia **uwierzytelniania alternatywnych poświadczeń** w usłudze VSTS, wykonując poniższe kroki:

1. Zaloguj się jako właściciel konta do konta usługi VSTS (https://{youraccount}.visualstudio.com).
2. Z konto pasek narzędzi, wybierz ikonę koła zębatego, a następnie wybierz pozycję **zasad**:
    
    ![Wybrana opcja ustawień zasad](media/tfvc-auth2.png) 

3. Sprawdź ustawienia połączenia aplikacji. Zmień te ustawienia, w oparciu o zasady zabezpieczeń:
    
    ![Wybrana opcja ustawień zasad](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>Nie znajdziesz już niczego w TFVC

Aby ustawić się kontroli wersji Team Foundation (TFVC) na komputerze deweloperskim, możesz **musi** Utwórz obszar roboczy, zgodnie z opisem w [zarządzanie obszarami roboczymi](#managing-workspaces) sekcji.

W Eksploratorze kontroli źródła, naciśnij klawisz **zarządzanie obszarami roboczymi** przycisku. Wykonaj kroki, aby zmapowanie projektu zespołowego do folderu na komputerze deweloperskim.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Nie widzę żadnych / all moich projektów

Po uwierzytelnieniu powinien zostać wyświetlony listy projektów. Domyślnie wyświetlane są tylko projekty TFS do. Aby wyświetlić innych typów projektów, zaznacz pole "Zobacz wszystkich projektów".

Należy pamiętać, że projekty, które znajdują się na serwerze nie będą widoczne, jeśli nie masz poprawne uprawnienia.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Pojawia się błąd "nie można utworzyć obszaru roboczego. Spróbuj ponownie"

Podczas próby [Utwórz nowy obszar roboczy](#creating-a-new-workspace), należy się upewnić, są spełnione następujące warunki:

- Zakaz używania nieprawidłowe znaki w nazwie obszaru roboczego.
- Nazwa musi być krótsza niż 64 znaki.
- Nie można użyć ścieżki lokalnej przez innych obszarów roboczych.