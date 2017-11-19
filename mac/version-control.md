---
title: Kontrola wersji | Dokumentacja firmy Microsoft
description: "Przy użyciu usługi Git i Podwersją w programie Visual Studio dla komputerów Mac."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 6e467cf6acda75948a189309b7648b1c4c085941
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="version-control"></a>Kontrola wersji

Kontroli wersji to system zarządzania plikami w wielu różnych wersji i — w oprogramowaniu development — jest zazwyczaj przyczyniły się do powstania przez wielu deweloperów. Głównym celem systemu kontroli wersji (_VC_) jest znalezienie rozwiązanie, które umożliwia wszystkim użytkownikom w tym samym czasie pracować bazowej kodu.

Stanowiącej podstawę żadnych kontroli wersji systemu jest _repozytorium_, który działa jako dane centralnego przechowywania dla wszystkich różnych plików — podobnie jak na serwerze plików. W przeciwieństwie do serwera plików, repozytorium zawiera całą historię projekt i wszystkie poprawki, które zostały wprowadzone.

Jeśli repozytorium magazynu danych centralnej, jest dla każdego użytkownika lokalnego magazynu danych, dzięki czemu mogą pracować nad nim. Ta metoda jest wywoływana _kopii roboczej_. W programie Visual Studio for Mac kopii roboczej pojawi się podobnie jak inne katalogu lokalnego na komputerze umożliwiając odczytywać i zapisywać do tych plików. Jednak ponieważ integracji systemu kontroli wersji programu Visual Studio for Mac, można wykorzystać możliwości Podwersją i Git bez opuszczania IDE.

Podwersją jest system kontroli wersji scentralizowane. Oznacza to, że ma pojedynczego serwera, który zawiera wszystkie pliki i wersje, z których użytkownicy można wyewidencjonować dowolna wersja dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium Podwersją, użytkownik otrzyma migawkę repozytorium w danym momencie.

Git to system kontroli wersji rozproszonej, który umożliwia zespołom jednocześnie pracować na tym samym dokumentów. Oznacza to, że może być pojedynczego serwera, który zawiera wszystkie pliki, ale zawsze, gdy repozytorium jest wyewidencjonowany z tego źródła centralnej, całe repozytorium został sklonowany lokalnie na komputerze.

# <a name="basic-concepts"></a>Koncepcje podstawowe 

Visual Studio for Mac zapewnia obsługę zarówno usługi Git i Podwersją systemów kontroli wersji. Przewodniki linki znajdują się poniżej Poznaj konfigurowania repozytoria Git i Podwersją przy użyciu programu Visual Studio for Mac, a także proste funkcje, takie jak przeglądanie, zatwierdzanie i wypychanie zmiany.

* [Konfigurowanie repozytorium Git](~/set-up-git-repository.md) 
* [Praca z usługą Git](~/working-with-git.md)
* [Konfigurowanie repozytorium Podwersją](~/set-up-subversion-repository.md)
* [Praca z Podwersją](~/working-with-subversion.md)