---
title: 'Porady: profilowanie kodu JavaScript na stronach sieci Web | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e33605b75dfe80bf755081692bc8a4991def801
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Porady: profilowanie kodu JavaScript na stronach sieci Web
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Narzędzia profilowania może zbierać dane wydajności dotyczące kodu JavaScript, która wykonuje w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web aplikacji, dowolnego strony sieci Web lub aplikacji JavaScript za pomocą metoda profilowania instrumentacji.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Internet Explorer 8 lub nowszy.  
  
> [!WARNING]
>  Aby profilować kod JavaScript w aplikacji platformy uniwersalnej systemu Windows, temacie [pamięć języka JavaScript](../profiling/javascript-memory.md) 
  
 Profilowanie Kreator służy do utworzenia sesji wydajności. Określ metody instrumentacji, a następnie określ JavaScript profilowania opcji na stronie Instrumentacji w oknie dialogowym właściwości sesji wydajności.  
  
 Po określeniu profilowanie plików JavaScript, kod JavaScript, który jest wykonywany w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] są sprofilować kodu wykonywanego na serwerze.  
  
-   Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, kod JavaScript wykonujący w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] są sprofilować kodu wykonywanego na serwerze.  
  
-   Dla dowolnego strony sieci Web jest profilowane kod JavaScript, która wykonuje w przeglądarce.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci Web ASP.NET  
  
1.  W [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu sieci Web.  
  
2.  Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów**.  
  
3.  Na pierwszej stronie kreatora osiągów określ **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.  
  
4.  Na drugiej stronie kreatora, upewnij się, że bieżący projekt jest wybrany na liście elementów docelowych, a następnie kliknij przycisk **dalej.**  
  
5.  Na trzeciej stronie kreatora wybierz **JavaScript profilu** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
6.  Na czwartej stronie kreatora, kliknij przycisk **Zakończ** można uruchomić aplikacji sieci Web w przeglądarce.  
  
7.  Wykonuje funkcje, które chcesz profilu.  
  
8.  Aby zakończyć sesję profilowania, zamknij przeglądarkę.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilowanie kodu JavaScript w poszczególnych stron sieci Web lub aplikacji JavaScript  
  
1.  Otwórz [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)].  
  
2.  Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów**.  
  
3.  Na pierwszej stronie kreatora osiągów określ **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.  
  
4.  Na drugiej stronie kreatora, kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **dalej.**  
  
5.  Na trzeciej stronie kreatora:  
  
    1.  Wpisz adres URL strony w **jakim adresem URL lub ścieżką będzie działała aplikacja sieci** pole.  
  
    2.  Wybierz **JavaScript profilu** pole wyboru, a następnie kliknij przycisk **dalej**.  
  
6.  Na czwartej stronie kreatora, kliknij przycisk **Zakończ** można uruchomić strony sieci Web w przeglądarce.  
  
7.  Wykonuje funkcje, które chcesz profilu.  
  
8.  Aby zakończyć sesję profilowania, zamknij przeglądarkę.