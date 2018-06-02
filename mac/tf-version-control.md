---
title: Kontrola wersji TF
description: Połączenie z Team Foundation Server i Visual Studio Team Services z kontroli wersji Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693776"
---
# <a name="connecting-to-team-foundation-version-control"></a>Łączenie z kontroli wersji Team Foundation 

> [!NOTE]
> **Uwaga**: Team Foundation Version Control pomocy technicznej jest obecnie w przeglądzie, a niektóre funkcje nie jeszcze całkowicie działa. Chętnie poznamy opinie od Ciebie na wszelkie problemy w [społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html). Zmiany są nadal znaleziona!

Visual Studio Team Services (VSTS) i Team Foundation Server (TFS) zapewniają dwa modele kontroli wersji: Git, które jest udostępniane kontroli wersji i Team Foundation wersji formantu (TFVC), który jest scentralizowaną kontrolę wersji. Ten artykuł zawiera omówienie i punkt początkowy dla za pomocą Team Foundation Version Control za pomocą programu Visual Studio dla komputerów Mac.

## <a name="requirements"></a>Wymagania

* Program Visual Studio dla komputerów Mac w wersji 7.5 lub nowszej.
* Visual Studio Team Services lub program Team Foundation Server 2013 lub nowszym
* Projekt w Visual Studio Team Services lub Team Foundation Server skonfigurowany do używania kontroli wersji Team Foundation.

## <a name="installation"></a>Instalacja

W programie Visual Studio dla komputerów Mac, wybierz **Visual Studio > rozszerzeń...**  z menu. W **galerii** wybierz opcję **kontrolą wersji > kontroli wersji Team Foundation dla serwera TFS i programu VSTS** i kliknij przycisk **instalacji...** :

  ![Menedżer rozszerzeń](media/tfvc-install.png) 

Postępuj zgodnie z monitami, aby zainstalować rozszerzenie. Po zainstalowaniu, uruchom ponownie IDE.

## <a name="using-the-add-in"></a>Przy użyciu dodatku

Po zainstalowaniu rozszerzenia wybierz **kontroli wersji > TFS/VSTS > Połącz z Team Foundation Version Control...**  elementu menu. Kliknij przycisk **Dodaj** Aby dodać nowe konto: 

![Dodaj serwer programu TFVC](media/tfvc-add-remove-server.png)

Wybierz Visual Studio Team Services lub Team Foundation Server, aby rozpocząć:

![Połącz z serwerem programu TFVC](media/tfvc-choose-server-type.png)

Wprowadź swoje poświadczenia, a następnie kliknij przycisk **Zaloguj**: 

![Zaloguj się do serwera programu TFVC](media/tfvc-login.png)

Gdy użytkownik został pomyślnie zalogowany, wybierz projekty, które chcesz uzyskać dostęp, a następnie naciśnij klawisz **OK**: 

![Wybierz projekty](media/tfvc-choose-projects.png)

Wybierz **kontrolą wersji > TFS/VSTS > Eksploratora kontroli źródła** element menu, aby otworzyć Eksploratora kontroli źródła, co umożliwia przeglądanie źródła.

> [!IMPORTANT]
> **Znany problem**: W tej wersji zapoznawczej przy pierwszym otwarciu Eksploratora kontroli źródła, konieczne będzie [Utwórz nowy obszar roboczy](#creating-a-new-workspace).

![Eksplorator źródła](media/tfvc-source-explorer.png)

W Eksploratorze kodu źródłowego można wybrać kodu źródłowego na serwerze i wykonać następujące czynności:

- Zarządzanie obszary robocze (tworzenia, edytowania i usuwania).
- Przechodzenie między struktury projektu.
- Mapowanie projektów.
- Pobierz projektów.
- Blokowanie i odblokowywanie plików.
- Zmień nazwy plików.
- Usuń pliki.
- Dodaj nowy plik.
- Wymelduj się.
- Zamelduj się.
- Wyświetlanie historii zmian.
- Porównaj zmiany.

## <a name="creating-a-new-workspace"></a>Tworzenie nowego obszaru roboczego

W Eksploratorze kontroli źródła, wybierz polecenie **zarządzanie obszarami roboczymi** przycisku. 

![Zarządzanie obszarami roboczymi](media/tfvc-manage-workspaces.png)

Kliknij przycisk **Dodaj** przycisk, aby utworzyć nowy obszar roboczy.

![Tworzenie obszaru roboczego](media/tfvc-create-workspace.png)

Podaj nazwę dla obszaru roboczego, a następnie kliknij przycisk **Dodaj Folder pracy** do mapowania projektu do folderu lokalnego na komputerze.

Po zakończeniu kliknij **OK**, następnie zamknij okno dialogowe Zarządzanie obszarów roboczych. Teraz możesz pobrać pliki, choć Eksplorator kodu źródłowego i rozpocząć pracę.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="problems-using-basic-authentication"></a>Problemy z uwierzytelniania podstawowego

Istnieje wiele różnych opcji dostępnych do uwierzytelniania z serwerem:

- OAuth
- Podstawowy
- Uwierzytelnianie NTLM

Aby można było użyć uwierzytelniania podstawowego jest niezbędne w celu umożliwienia **poświadczenia alternatywne uwierzytelniania** w VSTS, wykonując następujące czynności:

1. Zaloguj się jako właściciela konta do swojego konta usługi VSTS (https://{youraccount}.visualstudio.com).
2. Z paska narzędzi konta, wybierz ikonę narzędzi i wybierz **zasad**: ![wybraną opcją ustawienia zasad](media/tfvc-auth2.png) 
3. Sprawdź ustawienia połączenia aplikacji. Zmiana tych ustawień w oparciu o zasady zabezpieczeń: ![wybraną opcją ustawienia zasad](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>Nie znajdziesz już niczego w TFVC

Można ustawić zapasowej kontroli wersji Team Foundation (TFVC) na komputerze deweloperskim możesz **musi** Tworzenie obszaru roboczego, zgodnie z opisem w [Tworzenie nowego obszaru roboczego](#creating-a-new-workspace) sekcji.

W Eksploratorze kontroli źródła, naciśnij klawisz **zarządzanie obszarami roboczymi** przycisku. Wykonaj kroki, aby mapować projektu zespołowego do folderu na komputerze deweloperskim.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Nie ma żadnych / all moich projektów

Po uwierzytelnieniu należy zapoznać się z listą projektów. Domyślnie wyświetlane są tylko projektów TFS do. Aby wyświetlić inne rodzaje projektów, zaznacz pole "Zobacz wszystkie projekty".

Należy pamiętać, że projekty znajdujące się na serwerze nie będą wyświetlane, jeśli nie masz poprawne uprawnienia.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Pojawia się błąd "nie można utworzyć obszaru roboczego. Spróbuj ponownie"

Podczas próby [Utwórz nowy obszar roboczy](#creating-a-new-workspace), należy się upewnić, są spełnione następujące warunki:

- Nie użycie nieprawidłowych znaków w nazwie obszaru roboczego.
- Nazwa musi być krótsza niż 64 znaki.
- Nie można użyć ścieżki lokalnej przez innych obszarów roboczych.