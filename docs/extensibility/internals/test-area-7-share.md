---
title: 'Obszar testu 7: Udostępnianie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa74d6ff2291288a1ca0e7f17a2edb1e126f222b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142471"
---
# <a name="test-area-7-share"></a>Testowanie obszaru 7: udziału
Obszar ten test obejmuje udostępniania elementów między lokacjami za pomocą **udziału** polecenia.  
  
 Operacja hhare jest widoczna duplikatów plików i folderów elementów między co najmniej dwie lokalizacje w hierarchii plików kontroli źródła. Duplikowanie nie naprawdę występuje na serwerze, ale użytkownik znajduje się w tym samym pliku w dwóch lub więcej określonych lokalizacji. Ze zmianami do żadnego z elementów udostępnionych, zmiany te są wyświetlane w innych lokalizacji udostępnionej.  
  
 Udostępnianie w folderach działa, jeśli wybierz folder z co najmniej jeden plik pod kontrolą źródła w nim. Polecenie udziału jest wyłączone w następujących warunkach:  
  
-   Jeśli wybrany folder jest pusty folder.  
  
-   Jeśli istnieje folder prawdziwe, ale nie zawiera on źródła kontroli plików.  
  
-   Jeśli istnieje folder wirtualny, czy pliki pod kontrolą źródła są w nim czy nie.  
  
-   W przypadku projektu zdalnej witryny sieci Web.  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowanego środowiska menu ścieżki są używane w przypadku testowego.  
  
 Udział: **pliku**->**kontroli źródła**->**udziału**.  
  
## <a name="expected-behavior"></a>Oczekiwane zachowanie  
  
-   Udostępniony plik pojawia się w lokalizacji udostępnionej.  
  
-   Wyświetlanie w źródłowym kontroli wersji magazynu historii przedstawiono udostępnianych plików.  
  
-   Edytowanie pliku udostępnionego edytuje zarówno w lokalizacji pliku.  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla obszaru testu udziału.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Udostępnianie pliku z jednego załadowanego projektu pod kontrolą źródła w innym załadowanego projektu|1.  Utwórz nowy projekt.<br />2.  Dodaj drugi projektu do rozwiązania.<br />3.  Utwórz plik w drugim projektu o nazwie, która nie znajduje się w pierwszy projekt.<br />4.  Dodaj rozwiązanie do kontroli źródła.<br />5.  Wybierz pierwszy projekt.<br />6.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />7.  Udostępnianie pliku z drugiego projektu do pierwszego projektu.<br />8.  Zaakceptuj **Wyewidencjonuj** Jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|  
|Udział plików z jednego projektu do innego|1.  Utwórz nowy projekt.<br />2.  Dodaj go do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz drugi projekt (nowe rozwiązanie).<br />5.  Dodaj rozwiązanie do kontroli źródła.<br />6.  Wybierz projekt.<br />7.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />8.  Udostępnij plik z projektu uprzednio dodanych do otwartego projektu.<br />9. Zaakceptuj **Wyewidencjonuj** Jeśli zostanie wyświetlony monit.|Typowe oczekiwane zachowanie.|  
|Udostępnianie pliku nie jest częścią projektu z kontroli źródła do aktualnie załadowanego projektu|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik do kontroli źródła, która nie jest częścią projektu lub rozwiązania.<br />4.  Wybierz projekt i Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />5.  Wybierz plik, w ramach **udostępnianie** okno dialogowe, które nie istnieje wewnątrz bieżącego projektu lub rozwiązania i udostępnić go.<br />6.  Zaakceptuj **Wyewidencjonuj** Jeśli zostanie wyświetlony monit.|Kontroli źródła wykonał operację pobierania, plik jest teraz w lokalizacji lokalnej projektu.|  
|Udostępnianie plików w ramach tego samego projektu do innego folderu|1.  Wybierz **wyewidencjonować automatycznie** w **narzędzia** -> **opcje** -> **kontroli źródła**.<br />2.  Utwórz nowy projekt, a następnie dodaj go do kontroli źródła.<br />3.  Dodaj folder do projektu.<br />4.  Dodaj plik do folderu i sprawdź w folderze.<br />5.  Wybierz folder.<br />6.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />7.  Udział plików w wybranym folderze.|Typowe oczekiwane zachowanie.<br /><br /> Folder musi być sprawdzany przy użyciu pliku w jego zanim będzie można użyć do udziału.|  
|Udostępnianie folderu do załadowanego projektu — cykliczne|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Wybierz projekt.<br />4.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />5.  Wybierz folder.<br />6.  Udostępnianie rekursywnie folderu do projektu.|Typowe oczekiwane zachowanie.|  
|Udostępnianie kilka plików z jednego projektu do innego|1.  Utwórz nowy projekt z kilku plików.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Zamknij rozwiązanie.<br />4.  Utwórz nowy projekt w rozwiązaniu do nowego.<br />5.  Dodaj rozwiązanie do kontroli źródła.<br />6.  Wybierz projekt.<br />7.  Otwórz **udziału** okno dialogowe (**pliku** -> **kontroli źródła** -> **udziału**).<br />8.  Udostępnianie kilka plików z wcześniej utworzony projekt do aktualnie otwartego projektu.|Typowe oczekiwane zachowanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)