---
title: "Testu obszar 8: Przełączanie wtyczki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f6a518d618b3a98ec85cbbe015d3b2c5fc7a710
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-8-plug-in-switching"></a>Testu obszar 8: Przełączanie wtyczki
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) ma interfejs użytkownika (UI), aby zmienić bieżącą wtyczką kontroli źródła. Ten obszar testu udostępnia przypadków testowych dla procesu pobrania, które wtyczki do użycia na potrzeby rozwiązania do kontroli źródła.  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowanego środowiska menu ścieżki są używane w przypadku testowego.  
  
-   Bieżącą wtyczką kontroli źródła: **narzędzia** -> **opcje** -> **kontroli źródła** -> **wyboru wtyczek** .  
  
-   Zmień źródło powiązaniu kontroli: **pliku** -> **kontroli źródła** -> **Zmień kontrolę źródła**...  
  
## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie  
 Zmiana wtyczka do kontroli źródła dla rozwiązania jest możliwa bez zamykania programu Visual Studio lub ponownego ładowania rozwiązania. Ponadto bieżącą wtyczką kontroli źródła automatycznie zmienia się z działaniem używanym przez rozwiązanie po załadowaniu tego rozwiązania.  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla wtyczki przełączania obszaru testu.  
  
### <a name="case-8a-automatic-change"></a>Przypadek 8a: automatyczna zmiana  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
 Gdy użytkownik wczytuje rozwiązania, które jest pod kontrolą źródła, rozwiązanie jest ładowane automatycznie i odpowiednie wtyczka do kontroli źródła jest wybrany jako bieżący.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Zmiana wtyczkę kontroli źródła automatyczne|1.  Wybierz wtyczki w ramach testu jako bieżący (**narzędzia** -> **opcje** -> **kontroli źródła** -> **wtyczki Wybór**.)<br />2.  Utwórz nowy projekt.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Wybierz inny wtyczki (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Akceptowanie zwalniania monitu rozwiązania.<br />6.  Otwórz rozwiązanie z dysku.|Rozwiązanie jest otwarte.<br /><br /> Dodatek w ramach testu jest bieżącą wtyczką kontroli źródła.|  
  
### <a name="case-8b-solution-based-change"></a>Przypadek 8b: rozwiązania na podstawie zmiany  
  
#### <a name="expected-behavior"></a>Oczekiwane zachowanie  
 Rozwiązanie może mieć jego skojarzony wtyczka do kontroli źródła zmienione.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Zmiana wtyczki dla rozwiązania|1.  Wybierz wtyczki w ramach testu jako bieżący (**narzędzia** -> **opcje** -> **kontroli źródła** -> **wtyczki Wybór**).<br />2.  Utwórz nowy projekt i rozwiązanie.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Usuń powiązanie rozwiązanie z kontroli źródła (przy użyciu **Zmień kontrolę źródła** okno dialogowe).<br />5.  Wybierz inny wtyczki (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Załaduj ponownie rozwiązanie z dysku, jeśli zwalnianie modułu.<br />7.  Dodaj rozwiązanie do kontroli źródła.<br />8.  Usuń powiązanie rozwiązanie z kontroli źródła (przy użyciu **Zmień kontrolę źródła** okno dialogowe).<br />9. Wybierz wtyczki w ramach testu ponownie.<br />10. Załaduj ponownie rozwiązanie z dysku, jeśli zwalnianie modułu.<br />11. Powiąż rozwiązania do oryginalnej lokalizacji (przy użyciu **Zmień kontrolę źródła** okno dialogowe).|Rozwiązanie jest dodawany do kontroli źródła przy użyciu wybranej wtyczki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)