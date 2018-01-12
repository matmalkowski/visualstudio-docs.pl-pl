---
title: "Rejestrowanie zdarzeń dla rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0c8a304b314fe09536e2659f88bfdbf53c58552c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="event-logging-for-office-solutions"></a>Rejestrowanie zdarzeń dla rozwiązań pakietu Office
  Aby wyświetlić komunikaty o wyjątku, które są przechwytywane przez służy Podgląd zdarzeń w systemie Windows [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] po zainstalowaniu lub odinstalowaniu rozwiązań pakietu Office. Te komunikaty z Rejestratora zdarzeń służy do rozwiązywania instalacji i problemy z wdrażaniem.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="reading-the-event-log"></a>Odczytywania dziennika zdarzeń  
 Otwórz **Podgląd zdarzeń** i filtrować zdarzenia mają być wyświetlane.  
  
#### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Do odczytu dziennika zdarzeń w systemie Windows Server 2003 i Windows XP  
  
1.  W Panelu sterowania otwórz **narzędzia administracyjne**.  
  
2.  Uruchom **Podgląd zdarzeń**.  
  
3.  Na liście dzienniki zdarzeń, wybierz **aplikacji**.  
  
4.  Na **widoku** menu, kliknij przycisk **filtru**.  
  
5.  W **źródło zdarzenia** listy, wybierz **VSTO 4.0**.  
  
6.  Dla zdarzeń instalacji w **identyfikator zdarzenia** wpisz **4096**.  
  
7.  Kliknij przycisk **OK** Aby wyświetlić widok filtrowany.  
  
#### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Do odczytu dziennika zdarzeń w systemie Windows 7, Windows Vista i Windows Server 2008  
  
1.  W Panelu sterowania otwórz **narzędzia administracyjne**.  
  
2.  Uruchom **Podgląd zdarzeń**.  
  
3.  Rozwiń węzeł **dzienniki systemu Windows**.  
  
4.  Na liście dzienniki zdarzeń, wybierz **aplikacji**.  
  
5.  Na **akcji** menu, kliknij przycisk **Filtruj bieżący dziennik**.  
  
6.  W **źródło zdarzenia** listy, wybierz **VSTO 4.0**.  
  
7.  Dla zdarzeń instalacji w **identyfikator zdarzenia** wpisz **4096**.  
  
8.  Kliknij przycisk **OK** Aby wyświetlić widok filtrowany.  
  
 Podgląd zdarzeń zawiera następujące informacje:  
  
-   Lokalizacja manifestu rozmieszczenia dla rozwiązania.  
  
-   Komunikat opisujący przyczynę błędu lub wyjątek.  
  
 Te komunikaty wyjątku może pomóc określić przyczynę problem z instalacją, takie jak niezaufany certyfikat, lokalizacji niezaufanych dokumentu lub manifest rozmieszczenia nieprawidłowy.  
  
 Po odinstalowaniu rozwiązania do pakietu Office, komunikaty o wyjątkach pozostają w dzienniku zdarzeń.  
  
 Aby wyświetlić lub wyjątek komunikaty dziennika, gdy działa rozwiązania do pakietu Office, zobacz [debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md) i [debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Lokalizacja  
 Język komunikat o wyjątku jest określana przez Visual Studio Tools for Office runtime języka. Na przykład jeśli na komputerze użytkownika końcowego jest zainstalowany pakiet języka japońskiego, komunikat o wyjątku jest zapisywane w dzienniku zdarzeń w języku japońskim.  
  
## <a name="disabling-the-event-logger"></a>Wyłączenie rejestrowania zdarzeń  
 Domyślnie program rejestrujący zdarzenia jest włączona po zainstalowaniu lub odinstalowaniu rozwiązań pakietu Office. Rejestrator zdarzeń można wyłączyć, ustawiając zmienną środowiskową VSTO_EVENTLOGDISABLED "1" (jeden).  
  
#### <a name="to-disable-the-event-log"></a>Aby wyłączyć dziennik zdarzeń  
  
1.  W Panelu sterowania otwórz **systemu**.  
  
2.  Na **zaawansowane** , kliknij pozycję **zmiennych środowiskowych**.  
  
3.  W **zmienne systemowe** okienku, kliknij przycisk **nowy**.  
  
4.  W **Nowa zmienna systemowa** okno dialogowe, typ **VSTO_EVENTLOGDISABLED** w **nazwa zmiennej** pole.  
  
5.  W **wartość zmiennej** wpisz **1**.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Rozwiązywanie problemów z wdrażaniem rozwiązań Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  