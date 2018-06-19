---
title: 'Obszar testu 6: Usuń | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97fc6ab9746e7ef2188c78dc77ec357f7d415a42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140232"
---
# <a name="test-area-6-delete"></a>Testowanie obszaru 6: usuwanie
Ten obszar testu wtyczkę kontroli źródła obejmuje akcje usuwania.  
  
 Odpowiada usunąć akcje w kontroli źródła **Eksploratora rozwiązań**.  
  
 Poniżej znajduje się lista elementów, które mogą zostać usunięte:  
  
-   Pliki  
  
-   Foldery  
  
-   Projekt  
  
 W zależności od typu projektu może mieć możliwość **Usuń** projektu (pozostawia pliki na dysku) lub **usunąć** projektu (spowoduje usunięcie plików na dysku). Każda akcja usuwa projektów lub elementów z **Eksploratora rozwiązań**.  
  
## <a name="expected-behavior"></a>Oczekiwane zachowanie  
 Oczekiwane zachowanie dla przypadków testowych w obszarze testu delete jest:  
  
-   Usunięty element nie jest już widoczna w **Eksploratora rozwiązań**.  
  
-   Usunięto projektu lub elementu nadrzędnego jest wyewidencjonowany, zgodnie z potrzebami (prawdopodobnie z wierszem.)  
  
-   Po usunięciu wyewidencjonowany lub dodać elementu, nie ma w **oczekujących zaewidencjonowań** okna.  
  
-   Element nadal istnieje w magazynie kontroli źródła, nawet po usunięciu i musi ręcznie przeczyścić.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Usuwanie projektu klienta|1.  Utwórz projekt klienta.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Usuń cały projekt z rozwiązania|Typowe oczekiwane zachowanie.|  
|Usuń pusty plik|1.  Utwórz projekt klienta.<br />2.  Dodaj plik zero bajtów do projektu.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Wybierz plik, usuń go.|Typowe oczekiwane zachowanie.|  
|Usuwanie folderu z plikami|1.  Tworzenie rozwiązania pojedynczego projektu.<br />2.  Dodaj folder.<br />3.  Dodaj jeden plik do folderu.<br />4.  Dodaj rozwiązanie do kontroli źródła.<br />5.  Zapoznaj się z projektu, aby uniknąć monitów.<br />6.  Usuń folder.|Typowe oczekiwane zachowanie.|  
|Usuwanie projektu sieci Web systemu plików|1.  Utwórz projekt sieci Web systemu plików (Użyj przycisk Przeglądaj, aby określić ścieżkę UNC).<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Usuń cały projekt z rozwiązania.<br />4.  Powtórz kroki od 1 do 3 dla lokalnych projektu sieci Web (wykonuje różne ścieżki do kodu, ale ma tego samego interfejsu zewnętrznego i zachowanie).|Typowe oczekiwane zachowanie.|  
|Usuń plik z projektu sieci Web systemu plików|1.  Utwórz projekt sieci Web systemu plików.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Usuń plik z projektu.<br />4.  Powtórz kroki od 1 do 3 dla lokalnych projektu sieci Web (wykonuje różne ścieżki do kodu, ale ma tego samego interfejsu zewnętrznego i zachowanie).|Typowe oczekiwane zachowanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)