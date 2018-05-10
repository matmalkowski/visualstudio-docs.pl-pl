---
title: Kontrola wersji
description: Przy użyciu usługi Git i Podwersją w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9d19edb4801ee8af6a18f3e458cd06d0499e0273
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="version-control"></a>Kontrola wersji

Kontroli wersji to system zarządzania plikami w wielu różnych wersji i — w oprogramowaniu development — jest zazwyczaj przyczyniły się do powstania przez wielu deweloperów. Głównym celem systemu kontroli wersji (_VC_) jest znalezienie rozwiązanie, które umożliwia wszystkim użytkownikom w tym samym czasie pracować bazowej kodu.

Stanowiącej podstawę żadnych kontroli wersji systemu jest _repozytorium_, który działa jako dane centralnego przechowywania dla wszystkich różnych plików — podobnie jak na serwerze plików. W przeciwieństwie do serwera plików, repozytorium zawiera całą historię projekt i wszystkie poprawki, które zostały wprowadzone.

Jeśli repozytorium magazynu danych centralnej, jest dla każdego użytkownika lokalnego magazynu danych, dzięki czemu mogą pracować nad nim. Ta metoda jest wywoływana _kopii roboczej_. W programie Visual Studio for Mac kopii roboczej pojawi się podobnie jak inne katalogu lokalnego na komputerze umożliwiając odczytywać i zapisywać do tych plików. Jednak ponieważ integracji systemu kontroli wersji programu Visual Studio for Mac, używając Podwersją i Git bez opuszczania IDE.

Podwersją jest system kontroli wersji scentralizowane, co oznacza, że istnieje pojedynczego serwera, który zawiera wszystkie pliki i wersje, z których użytkownicy można wyewidencjonować dowolna wersja dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium Podwersją, użytkownik pobiera migawkę repozytorium w danym momencie.

Git to system kontroli wersji rozproszonej, który umożliwia zespołom jednocześnie pracować na tym samym dokumentów. Za pomocą narzędzia Git może być pojedynczego serwera, który zawiera wszystkie pliki, ale cały repozytorium został sklonowany lokalnie na komputerze w każdym przypadku, gdy repozytorium jest wyewidencjonowany z tego źródła centralnej.

# <a name="basic-concepts"></a>Koncepcje podstawowe 

Visual Studio for Mac zapewnia obsługę zarówno usługi Git i Podwersją systemów kontroli wersji. Następujące artykuły Poznaj konfigurowania repozytoria Git i Podwersją przy użyciu programu Visual Studio for Mac, a także proste funkcje, takie jak przeglądanie, zatwierdzanie i wypychanie zmiany.

* [Konfigurowanie repozytorium Git](~/set-up-git-repository.md) 
* [Praca z usługą Git](~/working-with-git.md)
* [Konfigurowanie repozytorium podwersji](~/set-up-subversion-repository.md)
* [Praca z podwersją](~/working-with-subversion.md)