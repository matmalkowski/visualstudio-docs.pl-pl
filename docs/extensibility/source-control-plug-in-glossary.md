---
title: Słownik wtyczkę kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ccfd4cbbbca86d3b6e93d9998410c5dea117328d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139029"
---
# <a name="source-control-plug-in-glossary"></a>Słownik wtyczkę kontroli źródła
Poniższe terminy przydatne i definicje odnoszą się do dokumentacji zestawu SDK dodatku typu Plug-in kontroli źródła.  
  
## <a name="definitions"></a>Definicje  
 Ewidencjonowanie  
 Gdy użytkownik wprowadzi zmiany do kopii roboczej, użytkownik musi wysłać zmiany z kopii roboczej do repozytorium kontroli źródła centralnej. Spowoduje to utworzenie nowej wersji pliku, która jest dostępna dla innych użytkowników. Ten proces jest nazywany zaewidencjonowania.  
  
 Wyewidencjonowanie  
 Czynność żądanie kopii roboczej z repozytorium informowania repozytorium zamiaru go zmodyfikować. Kopia robocza odzwierciedla stan projektu, począwszy od tej chwili jest wyewidencjonowany.  
  
 Klient  
 Program, który korzysta z systemu kontroli kodu źródłowego. Na potrzeby tej dokumentacji jest środowiska IDE programu Visual Studio.  
  
 Komentarz  
 Komunikat opisujący zmiany, które użytkownika można dołączyć do poprawki, gdy jest wykonywana operacja kontroli źródła.  
  
 Konflikt  
 Sytuacja, gdy dwóch użytkowników próbuje Zaewidencjonuj zmiany w tym samym regionie, w tym samym pliku. Zwykle odbywa się przez scalenie.  
  
 Katalog  
 Folder lokalny po stronie klienta jest określone jako katalog. To jest kopia w której użytkownik faktycznie dokonuje zmian. Może istnieć wiele kopie robocze danego projektu; Zazwyczaj każdy Deweloper ma swój własny kopiowania.  
  
 Pobierz  
 Operacja get łączy użytkownika kopii roboczej na bieżąco z kopią repozytorium. W przeciwieństwie do wyewidencjonowania get jest wykonywane, gdy użytkownik po prostu musi kopii najnowszej wersji, ale zamierza nie wprowadzisz zmian.  
  
 Historia  
 Zwykle jest podsumowanie wszystkich wyewidencjonowania, zaewidencjonowania aktualizacje, znaczników i wersji w repozytorium kontroli źródła.  
  
 IDE  
 Zazwyczaj odwołuje się do programu Visual Studio zintegrowane środowisko deweloperskie. Jednak można również znaleźć do innych środowisk klienckich, które rozpoznają API dodatku typu Plug-in kontroli źródła.  
  
 Scal  
 Proces podczas źródłem dwóch lub więcej plików kodu połączone tworzą nowy plik, który zawiera wszystkie funkcje z poprzednich plików. To pojęcie jest niezbędne w kontroli wersji, której deweloperzy dwóch lub więcej pracować z plikami jednocześnie.  
  
 Projekt  
 Folder kontroli źródła jest często określone jako projekt. To nie ma żadnych relacji z projektami i rozwiązaniami w programie Visual Studio.  
  
 wtyczki  
 Biblioteki DLL, która udostępnia funkcje kontroli źródła zaimplementowanie interfejsu API dodatku typu Plug-in kontroli źródła.  
  
 Repozytorium  
 Kopii głównej, gdy system kontroli źródła przechowuje historię poprawek pełne projektu. Każdy projekt ma dokładnie jednego repozytorium.  
  
 Poprawki  
 Zatwierdzone zmiany w historii pliku lub zestawu plików. Zmiana jest jednym migawki w projekcie stale zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)