---
title: "Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2ab3571da02fa56cd905369ee44e372aedea4e36
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-office-solution-security"></a>Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office
  Ten temat zawiera wskazówki dotyczące rozwiązywania problemów, które można napotkać podczas pracy z Zabezpieczanie rozwiązań pakietu Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Zaufane rozwiązania nie można zainstalować z witryny z ograniczeniami  
 Użytkownicy nie mogą instalować rozwiązanie z lokalizacji w sieci web, jeśli witryna sieci web znajduje się w programie Internet Explorer strefy witryn z ograniczeniami. Dotyczy to nawet wtedy, gdy rozwiązanie jest podpisany przy użyciu zaufanego certyfikatu.  
  
 Adres URL w manifeście rozmieszczenia można podzielić na jednej z pięciu stref:  
  
-   Komputer  
  
-   Internet  
  
-   Lokalny intranet  
  
-   Zaufane witryny  
  
-   Witryny z ograniczeniami  
  
 Jeśli lokalizacja manifestu rozmieszczenia zostało przypisane do strefy witryn z ograniczeniami [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie instaluje rozwiązanie. Jeśli lokalizacja jest znany i może być uważany za zaufany, użytkownik może usunąć lokalizację ze strefy witryn z ograniczeniami i zainstalować rozwiązania. Aby uzyskać informacje o sposobie zarządzania strefami, zobacz [Konfigurowanie ClickOnce zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Nie można zainstalować rozwiązania z udziałów plików w sieci lub lokalizacji w sieci Web, gdy program Internet Explorer Konfiguracja zwiększonych zabezpieczeń lub jest zainstalowany program Internet Explorer 7  
 Internet Explorer zwiększonych zabezpieczeń konfiguracji (IEESC) w systemie Windows Server 2003 lub nowszym i programu Internet Explorer 7 i nowsze wersje, znacznie ogranicza możliwość przeglądania Internetu przez użytkowników. Gdy użytkownicy próbują zainstalować rozwiązań pakietu Office z lokalizacji sieciowej pliku udziału lub sieci web, może pojawić się następujący komunikat błędu: "dostosowane funkcjonalności w tej aplikacji nie będą działać, ponieważ certyfikat używany do podpisywania manifestu wdrożenia *Nazwa rozwiązania* nie jest zaufany. Skontaktuj się z administratorem Aby uzyskać dalszą pomoc."  
  
 IEESC i przeglądarki Internet Explorer 7 i nowsze wersje Jeśli adres URL w manifeście rozmieszczenia jest podzielone na strefy internetowej, manifest musi mieć certyfikat zaufanego wydawcy lub rozwiązania nie może zostać zainstalowana. Bez IEESC domyślne zachowanie jest monitowanie użytkownika końcowego do podjęcia decyzji o zaufaniu.  
  
 Zarządzać wpływ IEESC i programu Internet Explorer 7 i nowszym, identyfikować witryn sieci web i universal naming convention (UNC) ścieżki który zaufania i dodaj je do jednej ze stref zabezpieczeń Zaufane (Lokalny intranet lub Zaufane witryny). Aby uzyskać informacje o sposobie zarządzania strefami, zobacz [Konfigurowanie ClickOnce zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  