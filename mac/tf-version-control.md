---
title: Kontrola wersji TF
description: Połączenie z Team Foundation Server i Visual Studio Team Services z kontroli wersji Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Łączenie z kontroli wersji Team Foundation 

Visual Studio Team Services (VSTS) i Team Foundation Server (TFS) zapewniają dwa modele kontroli wersji: Git, które jest udostępniane kontroli wersji i Team Foundation wersji formantu (TFVC), który jest scentralizowaną kontrolę wersji. Ten artykuł zawiera omówienie i punkt początkowy dla za pomocą Team Foundation Version Control za pomocą programu Visual Studio dla komputerów Mac.

> [!NOTE]
> **Uwaga**: Team Foundation Version Control pomocy technicznej jest obecnie w przeglądzie, a niektóre funkcje nie jeszcze całkowicie działa. Nadal dalszych zmian do trybu!

## <a name="requirements"></a>Wymagania

* Program Visual Studio dla komputerów Mac w wersji 7.5 lub nowszej.
* Visual Studio Team serwerów lub serwera Team Foundation Server 2013 lub nowszym
* Projekt w Visual Studio Team Services lub Team Foundation Server skonfigurowany do używania kontroli wersji Team Foundation.

## <a name="installation"></a>Instalacja

Z poziomu programu Visual Studio dla komputerów Mac, wybierz **Visual Studio > rozszerzeń...**  menu. Wyszukaj "TF kontroli wersji" i zainstaluj **Team Foundation Version Control** rozszerzenia. Uruchom ponownie IDE po wyświetleniu monitu.

## <a name="using-the-add-in"></a>Przy użyciu dodatku

Po zainstalowaniu rozszerzenia wybierz **kontroli wersji > TFS/VSTS > Połącz z Team Foundation Version Control...**  menu. 

![Dodaj serwer programu TFVC](media/tfvc-add-remove-server.png)


Wybierz Visual Studio Team Services lub Team Foundation Server, aby rozpocząć:

![Połącz z serwerem programu TFVC](media/tfvc-choose-server-type.png)

Wprowadź poświadczenia: 

![Zaloguj się do serwera programu TFVC](media/tfvc-login.png)

Następnie wybierz projekty, które mają dostęp do: 

![Wybierz projekty](media/tfvc-choose-projects.png)

Aby kontynuować, zamknij okna dialogowe, a następnie użyć **kontrolą wersji > TFS/VSTS > Eksploratora kontroli źródła** menu do przeglądania źródła.

> [!WARNING]
> **Znany problem**: W tej wersji zapoznawczej przy pierwszym otwarciu Eksploratora kontroli źródła, konieczne będzie utworzenie nowego obszaru roboczego.

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

Polecenie **Dodaj** do utworzenia nowego obszaru roboczego.

![Tworzenie obszaru roboczego](media/tfvc-create-workspace.png)

Podaj nazwę dla obszaru roboczego, a następnie kliknij przycisk **Dodaj Folder pracy** do mapowania projektu do folderu lokalnego na komputerze.

Po zakończeniu kliknij **OK**, następnie zamknij okno dialogowe Zarządzanie obszarów roboczych. Teraz możesz pobrać pliki, choć Eksplorator kodu źródłowego i rozpocząć pracę.