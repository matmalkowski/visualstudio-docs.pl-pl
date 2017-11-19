---
title: "Praca z Podwersją | Dokumentacja firmy Microsoft"
description: "Przy użyciu Podwersją w programie Visual Studio dla komputerów Mac."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 026e3625b4ee2d6582ce5539e5cab68c945f09c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-subversion"></a>Praca z Podwersją

Jak wspomniano wcześniej w tym artykule, Podwersją jest system kontroli wersji scentralizowane, umożliwiający zapoznaj się z jednej kopii głównej scentralizowane danych. W przeciwieństwie do narzędzia Git wyewidencjonowywanie repozytorium Podwersją nie Klonuj repozytorium całego, jedynie tworzy migawkę w danym momencie.

Podwersją wykorzystuje model kopii zmodyfikować scalanie umożliwiają użytkownikom pracę na tym samym repozytorium jednocześnie. Oznacza to, że każdy użytkownik tworzy kopię lokalnych lub pracy, scentralizowane danych, który można następnie działają na niezależnie. Zmiany dla użytkowników pracujących kopie są scalane w sposób chronologicznym.

Na przykład załóżmy, że użytkownik A i B użytkownika zapoznaj się kopiowania z repozytorium zdalnym i poszczególnych plików Modyfikuj. Użytkownik A zakończeniu modyfikacji i zatwierdza je zdalnie. Zanim użytkownik B przeprowadzonych zatwierdzeń służbowym, należy je zaktualizować ich kopii roboczej zmianami od elementu zdalnego, w tym samym scalania zmian przez użytkownika A.

W sekcjach poniżej przeanalizujemy, jak Podwersją może służyć do kontroli wersji w programie Visual Studio dla komputerów Mac.

Na poniższym obrazie przedstawiono opcje podał przez element menu kontroli wersji programu Visual Studio dla komputerów Mac:

![Elementy menu kontroli wersji](media/version-control-svnVersionControlMenu.png)

W poniższych rozdziałach objaśnia każdej opcji bardziej szczegółowo.

## <a name="checkout"></a>Wyewidencjonowanie...

Przed rozpoczęciem korzystania z repozytorium zdalnego Podwersją, należy sprawdzić repozytorium, aby utworzyć kopię tego katalogu lokalnego lub pracy, na komputerze lokalnym.

Aby uzyskać informacje o użyciu **wyewidencjonowania** funkcji w programie Visual Studio dla komputerów Mac, postępuj zgodnie z instrukcjami [Konfigurowanie repozytorium Podwersją](~/set-up-subversion-repository.md) sekcji.

## <a name="update-solution"></a>Rozwiązanie aktualizacji

Przy użyciu zdalnego repozytorium, to trzeba pamiętać, że inni użytkownicy modyfikuje plików, tworzenie kopii roboczej przestarzałe. W oczekiwaniu to zaleca zawsze pobierać wszystkie zmiany z repozytorium w ramach rozwiązania przed rozpoczęciem pracy i przed zatwierdzeniem. Aby to zrobić, wybierz *kontrolą wersji > rozwiązanie aktualizacji* elementu menu.

## <a name="review-solution-and-commit"></a>Rozwiązanie przeglądu i zatwierdzania

O przegląd zmian dokonanych w plikach, użyj zmiany, winy, dziennika i scal kart na każdy dokument, jak przedstawiono poniżej:

![Wersja formantu karty](media/version-control-vcTabs.png)

Aby wyświetlić wszystkie zmiany w projekcie, przeglądanie **kontroli wersji > rozwiązanie przeglądu i zatwierdzania** element menu:

![Przejrzyj rozwiązania](media/version-control-vcStatus.png)

To umożliwia wyświetlanie wszystkich zmian w każdym pliku projektu z opcją Przywróć, Utwórz poprawki lub czy zatwierdzić.

Można przekazać pliku do zdalnego repozytorium,... Naciśnij klawisz zatwierdzania, wpisz wiadomość, zatwierdzenia i Potwierdź u przycisk Zatwierdź:


![Zatwierdzanie pliku](media/version-control-svnCommit.png)

Spowoduje to wysłanie zmiany do repozytorium, w których one utworzone nowa poprawka wszystkie modyfikacje.
