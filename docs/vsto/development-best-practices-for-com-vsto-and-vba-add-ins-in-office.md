---
title: "Programowanie najlepszych rozwiązań dla modelu COM, VSTO i VBA dodatków pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: 
helpviewer_keywords: 
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2158
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8985b3bb6e20b24b86174286104158c8830de971
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba--add-ins-in-office"></a>Programowanie najlepsze rozwiązania dotyczące modelu COM, VSTO i VBA dodatków pakietu Office
  Jeśli tworzysz COM VSTO lub VBA dodatków pakietu Office, należy przestrzegać zaleceń programowanie opisane w tym artykule.   Zapewni:

-  Zgodność dodatki między różnymi wersjami i wdrożenia pakietu Office.
-  Złożoności wdrażania dodatków dla użytkowników i administratorów IT.
-  Nie występują niezamierzone instalacji lub środowisko uruchomieniowe błędów dodatku.

>Uwaga: Przy użyciu [Mostek pulpitu](/windows/uwp/porting/desktop-to-uwp-root) przygotować z modelu COM, VSTO lub VBA dodatku dla Sklepu Windows nie jest obsługiwany. Dodatki COM, VSTO i VBA nie mogą być dystrybuowane w magazynie systemu Windows lub pakietu Office. 
  
## <a name="do-not-check-for-office-during-installation"></a>Nie sprawdzaj Office podczas instalacji  
 Nie zaleca się o dodatek wykrycia jest zainstalowane podczas instalacji dodatku pakietu Office. Jeśli nie zainstalowano pakietu Office, można zainstalować dodatek, a użytkownik będzie mógł uzyskać do niego dostęp, po zainstalowaniu pakietu Office. 
  
## <a name="use-embedded-interop-types-nopia"></a>Użyj osadzone typy międzyoperacyjne (NoPIA)  
Jeśli rozwiązanie korzysta z programu .NET 4.0 lub nowszym, użyj osadzone typy współdziałania (NoPIA) zamiast w zależności od Office głównej Interop zestawy MIĘDZYOPERACYJNE pakietu redystrybucyjnego. Przy użyciu typu osadzanie zmniejsza rozmiar instalacji rozwiązania i zapewnia zgodności w przyszłości. Pakiet Office 2010 został ostatniej wersji pakietu Office, dostarczonej PIA do dystrybucji. Aby uzyskać więcej informacji, zobacz [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/en-us/library/ee317478.aspx) i [równoważność typów i osadzone typy międzyoperacyjne](/windows/uwp/porting/desktop-to-uwp-root).

Jeśli rozwiązania korzystają z wcześniejszej wersji programu .NET, zaleca się zaktualizowanie rozwiązania do używania .NET 4.0 lub nowszy. Przy użyciu platformy .NET 4.0 lub nowszym zmniejsza wymagania wstępne dotyczące środowiska uruchomieniowego w nowszych wersjach systemu Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Unikaj w zależności od określonych wersji pakietu Office  
Jeśli rozwiązanie korzysta z funkcji, która jest dostępna tylko w nowszej wersji pakietu Office, sprawdź, czy ta funkcja istnieje (Jeśli to możliwe, na poziomie funkcji) w czasie wykonywania (na przykład za pomocą wyjątek obsługi lub Sprawdzanie wersji). Sprawdzanie poprawności co najmniej wersji zamiast określonych wersji przy użyciu obsługiwanych interfejsów API w modelu obiektów, takich jak [Application.Version właściwości](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx). Nie zaleca się, że możesz zależeć binarne metadanych, ścieżek instalacji i kluczy rejestru pakietu Office, ponieważ te można przełączać się między instalacji, środowisk i wersji.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Włącz użycie Office zarówno 32-bitowe i 64-bitowych   
Urządzenie docelowe kompilacji domyślnej powinno obsługiwać zarówno (x86) 32-bitowe i (x64) 64-bitowych, chyba że rozwiązanie jest zależna od bibliotek, które są dostępne tylko dla określonej liczbie bitów. 64-bitowej wersji pakietu Office zwiększa się w przyjęcia, szczególnie w środowiskach danych big data. Wspierające zarówno 32-bitowe i 64-bitowe ułatwia użytkownikom przejścia między 32-bitowe i 64-bitowej wersji pakietu Office.

Podczas pisania kodu VBA, użyj 64-bitowych bezpieczne zadeklarować instrukcje i skonwertować zmiennej zależnie od potrzeb. Ponadto upewnij się, że dokumenty mogą być współużytkowane między użytkowników systemu, podając kod każdego bitowości 32-bitowy lub 64-bitowej wersji pakietu Office. Aby uzyskać więcej informacji, zobacz [64-bitowe języka Visual Basic dla aplikacji — omówienie](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Ograniczona obsługa środowisk   
Rozwiązanie nie powinny wymagać uprawnień podniesienia uprawnień konta użytkownika lub administratora. Ponadto rozwiązanie nie należy uwzględniać Ustawianie lub zmienianie:

- Bieżący katalog roboczy.
- Katalogi załadowanie biblioteki DLL.
- Zmienna ścieżki.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Zapisz zmiany lokalizacji udostępnionych danych i ustawień
Jeśli rozwiązanie zawiera dodatek i procesem zewnętrznej dla pakietu Office, nie należy używać folderu danych aplikacji użytkownika lub rejestru do wymiany danych lub ustawień między dodatek i procesu zewnętrznego. Zamiast tego należy wziąć pod uwagę przy użyciu folder tymczasowy użytkownika, dokumentów lub katalog instalacyjny tego rozwiązania.

## <a name="increment-the-version-number-with-each-update"></a>Zwiększenie numeru wersji przy każdej aktualizacji
Ustaw numer wersji plików binarnych w rozwiązaniu i zwiększenia przy każdej aktualizacji. Ułatwi użytkownikom identyfikację zmian między wersjami i oceny zgodności.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Podaj oświadczenia dotyczące pomocy technicznej dla najnowszej wersji pakietu Office
Klienci prośbę o niezależnym dostawcom oprogramowania, aby zapewnić oświadczenia dotyczące pomocy technicznej dla ich COM, VSTO VBA dodatki i uruchamiane w pakiecie Office. Wyświetlanie listy pomaga instrukcje jawną obsługę klientów przy użyciu usługi Office 365 ProPlus gotowości narzędzia zrozumieć działem pomocy technicznej. 

Zapewnienie oświadczenia dotyczące pomocy technicznej dla aplikacji klienckich pakietu Office (na przykład programu Word lub Excel), najpierw sprawdź, czy dodatki uruchomione w bieżącej wersji pakietu Office, a następnie przekazać do udostępnienia aktualizacji, jeśli dodatek przerwy w przyszłej wersji. Nie masz do testowania dodatki, gdy firma Microsoft udostępnia nowej kompilacji lub aktualizacji pakietu Office. Microsoft zmieniają się rzadko platformą rozszerzeń COM, VSTO i VBA w pakiecie Office, a te zmiany zostaną dobrze udokumentowane.

>Ważne: Firma Microsoft udostępnia listę obsługiwanych dodatków gotowości raportów, a informacje kontaktowe niezależnego dostawcy oprogramowania. Aby pobrać dodatek na liście, zobacz [https://aka.ms/readyforwindows](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Przy użyciu procesu monitora debugować instalacji lub ładowania problemów
Jeśli dodatek ma problemy ze zgodnością podczas instalacji lub obciążenia, może być związana z problemów z dostępem do plików i rejestru. Użyj [Monitor procesu](/sysinternals/downloads/procmon) lub podobnego narzędzia debugowania do logowania i porównania zachowania dla środowiska pracy, aby łatwiej zidentyfikować problem.
