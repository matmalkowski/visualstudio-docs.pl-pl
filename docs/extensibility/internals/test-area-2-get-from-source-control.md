---
title: "Obszar Test 2: Uzyskaj z kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d436ef99907556c93f48c55bea315ae66e6218e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-2-get-from-source-control"></a>Obszar Test 2: Uzyskaj z kontroli źródła
Obszar ten test obejmuje przypadków testowych do pobierania elementów z magazynu wersji za pomocą polecenia Get. Te przypadki testowe można zastosować do lokalnego i projekty sieci Web.  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowanego środowiska menu ścieżki są używane w przypadku testowego.  
  
##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:  
  
-   **Plik**, **kontroli źródła**, **Pobierz najnowszą wersję**.  
  
-   **Plik**, **Pobierz najnowszą wersję**.  
  
-   Menu skrótów **Pobierz najnowszą wersję**.  
  
-   Get: **pliku**, **kontroli źródła**, **uzyskać**.  
  
## <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
##### <a name="get-latest-version"></a>Pobierz najnowszą wersję:  
 Wykonuje pobierania silent (bez interfejsu użytkownika), najnowszej wersji elementu z magazynu wersji.  
  
##### <a name="get"></a>Pobierz:  
 Wyświetla **uzyskać** okno dialogowe i umożliwia użytkownikowi wprowadzać zmiany do zestawu plików, które mają zostać pobrane, jak również zmodyfikować opcje, które mają wpływ na sposób pliki są pobierane.  
  
## <a name="test-cases"></a>Przypadki testowe  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Pobierz najnowszą wersję pliku, który nie istnieje lokalnie|1.  Tworzenie projektu.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu pod kontrolą źródła.<br />4.  Usuń kopię lokalną elementu.<br />5.  Pobierz najnowszą wersję elementu (Menu skrótów **Pobierz najnowszą wersję**).|Plik elementu jest pobierana lokalnie.|  
|Pobierz plik, który nie istnieje lokalnie|1.  Tworzenie projektu.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu pod kontrolą źródła.<br />4.  Usuń kopię lokalną elementu.<br />5.  Pobierz element (**pliku**, **kontroli źródła**, **uzyskać** \<element >).|Plik elementu jest pobierana lokalnie.|  
|Pobierz plik, który został wyewidencjonowany w trybie wyłączności i zmodyfikowany lokalnie|1.  Tworzenie projektu.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu pod kontrolą źródła.<br />4.  Wyewidencjonuj wyłącznie elementu projektu.<br />5.  Zmodyfikuj kopii lokalnej.<br />6.  Pobierz najnowszą wersję elementu (**pliku**, **Pobierz najnowszą wersję** \<element >). Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />7.  Kliknij przycisk **Zastąp** przycisk w oknie dialogowym ostrzeżenia.|**ReResult w kroku 6**`:`<br /><br /> Okno dialogowe ostrzeżenia wskazuje, że ten plik jest wyewidencjonowany.<br /><br /> **ReResult w kroku 7:**<br /><br /> Zmodyfikowany plik lokalny zastępuje oryginalną wersją z magazynu wersji.<br /><br /> Plik jest odczytu/zapisu.|  
|Pobierz i Zastąp plik, który jest wyewidencjonowany, udostępnionych i modyfikować lokalnie|1.  Utwórz nowy projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu pod kontrolą źródła.<br />4.  Zapoznaj się z elementu projektu jako udostępniony.<br />5.  Zmodyfikuj kopii lokalnej.<br />6.  Pobierz najnowszą wersję elementu (**pliku**, **Pobierz najnowszą wersję** \<element >). Jeśli ten krok zakończy się powodzeniem, przejdź do następnego kroku.<br />7.  Kliknij przycisk **Zastąp** w oknie dialogowym ostrzeżenia.|**Wynikiem krok 6:**<br /><br /> Okno dialogowe ostrzeżenia wskazuje, że ten plik jest wyewidencjonowany.<br /><br /> **Wynikiem krok 7:**<br /><br /> Zmodyfikowany plik lokalny zastępuje oryginalną wersją z magazynu wersji.<br /><br /> Plik jest odczytu/zapisu.|  
|Pobierz plik, który istnieje lokalnie, jak w przypadku najnowszej wersji w magazynie wersji|1.  Utwórz nowy projekt.<br />2.  Dodaj element do projektu.<br />3.  Umieść projektu pod kontrolą źródła.<br />4.  Pobierz element (**pliku**, **kontroli źródła**, **uzyskać** \<element >).|Plik lokalny nie ulega zmianie.|  
|Rozwiązanie z jednego projektu|1.  Tworzenie rozwiązania z jednego projektu.<br />2.  Umieść rozwiązania pod kontrolą źródła.<br />3.  Usuń wszystkie pliki projektu lokalnie.<br />4.  Rozwiązanie (**pliku**, **kontroli źródła**, **uzyskać**).|Wszystkie usunięte pliki zostaną przywrócone lokalnie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik po testowym dla plug-in kontroli źródła](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)