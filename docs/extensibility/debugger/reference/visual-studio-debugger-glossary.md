---
title: "Słownik debugera programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cc1e668f1d78bc6a1db66b6fd4dfebf77b0f6ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-debugger-glossary"></a>Słownik debugera programu Visual Studio
Poniżej przedstawiono terminów używanych w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowanie zestawu SDK.  
  
## <a name="terms"></a>Warunki  
 powiązania punktu przerwania  
 Ustawianie abstrakcję dla punktu przerwania w kodzie. Jest relacją między powiązania punktu przerwania i instrukcję punktu przerwania w strumieniu kodu. Gdy kod zwalnia, powiązane punkty przerwania nie może usunąć powiązania.  
  
 przyczynowości  
 Umożliwia śledzenie logicznego wątku do wykonania w wielu wątków fizycznych, procesów i maszyn i odtworzenie stos wywołań logicznej wątek na dowolnym etapie w okresie istnienia tego wątku.  
  
 kontekst kodu  
 Udostępnia abstrakcję pozycji w kodzie znane aparat debugowania. Dla większości architektur środowiska wykonawczego kontekst kodu jest adresem w strumieniu instrukcji programu. Nietradycyjnych języków, w których kodu nie może być reprezentowany przez instrukcje, kontekst kodu mogą być reprezentowane w inny sposób.  
  
 Ścieżka kodu  
 Reprezentuje punkt wykonywania w kodzie, w którym odgałęzienia lub wywołanie funkcji. Ślad stosu jest zasadniczo lista ścieżek kodu wywołania funkcji.  
  
 Aparat debugowania (DE)  
 Składnik, który pozwala na debugowanie architektury środowiska wykonawczego. Aparat debugowania działa w połączeniu z interpreter lub systemu operacyjnego i zapewnia debugowania usług, takich jak wykonanie oceny kontroli, punkty przerwania i wyrażenie.  
  
 kontekstu dokumentu  
 Udostępnia abstrakcję do pozycji w dokumencie pliku źródłowym znane aparat debugowania. W przypadku większości języków kontekstu dokumentu jest pozycji w pliku źródłowym. Nietradycyjnych języków, dla których plik źródłowy nie może być tekstu, kontekstu dokumentu może być reprezentowany w inny sposób. Zobacz też *pozycji dokumentu*.  
  
 położenie dokumentu  
 Udostępnia abstrakcję pozycji w pliku źródłowym znane IDE. Dla większości języków dokument jest to pozycja w pliku źródłowym. W przypadku języków nietradycyjnych położenie dokumentu może być reprezentowany w inny sposób. Zobacz też *kontekstu dokumentu*.  
  
 Błąd punktu przerwania  
 Abstrakcja opisu błędu w oczekującym punktem przerwania. Błąd przerwania może opisano wystąpił błąd w lokalizacji oczekującym punktem przerwania wyrażenie skojarzone z oczekującym punktem przerwania lub innych informacji, która uniemożliwia oczekującym punktem przerwania powiązania do lokalizacji kodu.  
  
 kontekst oceny  
 Udostępnia abstrakcję kontekście programowania dla wyrażenia. Kontekst oceny jest zazwyczaj zakres. Podczas obliczania wyrażenia w kontekście wyrażenia, kontekstu wyrażenie zawiera reguły zakresu, zgodne punktu utworzenia. Na przykład kontekstu wyrażenia utworzone w ramce stosu zapewni kontekst oceny zmiennych lokalnych, parametrów metody elementy członkowskie klasy (jeśli dotyczy) i zmiennych globalnych.  
  
 przechwycone wyjątku  
 Wyjątek, który zostaje zatrzymana przez aparat debugowania, nawet jeśli żaden wyjątek mechanizmu obsługi został wywołany z bieżącej ramki stosu.  
  
 JustMyCode  
 Pojęcie debugowania tylko kodu, który należy do użytkownika i ignoruje wszystkie pośrednie kodu na przykład kod systemu — nawet, jeśli kod źródłowy jest niedostępny dla tego kodu systemu.  
  
 oczekującym punktem przerwania  
 Udostępnia abstrakcję do punktów przerwania przed, podczas i po kod jest załadowany i możliwości wirtualizacji punktów przerwania. A oczekujących punktu przerwania:  
  
-   Zawiera wszystkie informacje wymagane do powiązania punktu przerwania do kodu w jednej lub wielu programów.  
  
-   Może zostać powiązany z wieloma lokalizacjami kodu w jednej lub wielu programów.  
  
-   Nigdy nie wiąże się z kodu.  
  
 Ładuje każdego kodu w czasie, wszystkie oczekujące punkty przerwania w programie jest sprawdzenie, czy można powiązać. Oczekującym punktem przerwania jest nazywany zawierają wszystkie powiązane punkty przerwania, które tworzy ona powiązanie.  
  
 proces  
 Fizyczny procesu Win32. Proces może zawierać wielu programów. Zobacz też *program*.  
  
 program  
 Jedna przestrzeń nazw uruchomionych w szczególności Architektura środowiska wykonawczego. Zobacz też *procesu*.  
  
 Menedżer sesji debugowania (SDM)  
 Zarządza dowolną liczbę aparatami debugowania debugowania dowolną liczbę programów w wielu procesach w dowolnej liczby maszyn. Na podstawowym poziomie SDM jest multiplekser aparatów debugowania. Ponadto SDM zapewnia spójny obraz sesji debugowania do IDE.  
  
 ramka stosu  
 Reprezentuje stan obliczeń na określonej ramce i określonym poziomie wywołania zagnieżdżonych funkcji.  
  
 wątek  
 Pojęcia uogólniony uruchomiona w co najmniej jeden program wykonywania instrukcji opartego na stosie.  
  
 Ostrzeżenie punktu przerwania  
 Abstrakcja opisu ostrzeżenie w oczekującym punktem przerwania. Ostrzeżenie punkt przerwania w tym artykule opisano przyczyny, dlaczego oczekującym punktem przerwania nie ma jeszcze powiązany z lokalizacji kodu. Może to być, czy kod nie została załadowana jeszcze lokalizacji opisanego przez oczekującym punktem przerwania lub innego powodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)