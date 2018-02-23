---
title: 'Porady: profilowanie kodu JavaScript na stronach sieci Web | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 737ead7c9745fc7cb173d542379f3c0d8ba39e89
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Porady: profilowanie kodu JavaScript na stronach sieci Web

Visual Studio Profiling Tools może zbierać dane wydajności dotyczące kodu JavaScript, która wykonuje w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web aplikacji, dowolnego strony sieci Web lub aplikacji JavaScript za pomocą metoda profilowania instrumentacji. Wymaga programu Internet Explorer 8 lub nowszy.

> [!WARNING]
> Aby profilować kod JavaScript w aplikacji platformy uniwersalnej systemu Windows, temacie [pamięć języka JavaScript](../profiling/javascript-memory.md) 

Profilowanie Kreator służy do utworzenia sesji wydajności. Określ metody instrumentacji, a następnie określ JavaScript profilowania opcji na stronie Instrumentacji w oknie dialogowym właściwości sesji wydajności.

Po określeniu profilowanie plików JavaScript, kod JavaScript, który jest wykonywany w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] są sprofilować kodu wykonywanego na serwerze.

- Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, kod JavaScript wykonujący w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] są sprofilować kodu wykonywanego na serwerze.

- Dla dowolnego strony sieci Web jest profilowane kod JavaScript, która wykonuje w przeglądarce.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci Web ASP.NET

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu sieci Web w programie Visual Studio.

2. Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów**.

3. Na pierwszej stronie kreatora osiągów określ **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora, upewnij się, że bieżący projekt jest wybrany na liście elementów docelowych, a następnie kliknij przycisk **dalej.**

5. Na trzeciej stronie kreatora wybierz **JavaScript profilu** pole wyboru, a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora, kliknij przycisk **Zakończ** można uruchomić aplikacji sieci Web w przeglądarce.

7. Wykonuje funkcje, które chcesz profilu.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilowanie kodu JavaScript w poszczególnych stron sieci Web lub aplikacji JavaScript

1. Otwórz program Visual Studio.

2. Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów**.

3. Na pierwszej stronie kreatora osiągów określ **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora, kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **dalej.**

5. Na trzeciej stronie kreatora:

    1. Wpisz adres URL strony w **jakim adresem URL lub ścieżką będzie działała aplikacja sieci** pole.

    2. Wybierz **JavaScript profilu** pole wyboru, a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora, kliknij przycisk **Zakończ** można uruchomić strony sieci Web w przeglądarce.

7. Wykonuje funkcje, które chcesz profilu.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.