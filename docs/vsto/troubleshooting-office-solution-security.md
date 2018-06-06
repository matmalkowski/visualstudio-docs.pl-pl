---
title: Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 547ba6d1e58376c50d0e01ab8fd3d55f62d5a935
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693321"
---
# <a name="troubleshooting-office-solution-security"></a>Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office
  Ten temat zawiera wskazówki dotyczące rozwiązywania problemów, które można napotkać podczas pracy z Zabezpieczanie rozwiązań pakietu Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Zaufane rozwiązania nie można zainstalować z witryny z ograniczeniami  
 Użytkownicy nie mogą instalować rozwiązanie z lokalizacji w sieci web, jeśli witryna sieci Web znajduje się w programie Internet Explorer strefy witryn z ograniczeniami. Dotyczy to nawet wtedy, gdy rozwiązanie jest podpisany przy użyciu zaufanego certyfikatu.  
  
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
  
 Zarządzać wpływ IEESC i programu Internet Explorer 7 i nowszym, identyfikować witryn sieci Web i universal naming convention (UNC) ścieżki który zaufania i dodaj je do jednej ze stref zabezpieczeń Zaufane (Lokalny intranet lub Zaufane witryny). Aby uzyskać informacje o sposobie zarządzania strefami, zobacz [Konfigurowanie ClickOnce zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
  
  