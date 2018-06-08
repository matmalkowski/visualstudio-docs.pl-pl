---
title: 'Porady: profilowanie kodu JavaScript na stronach sieci Web | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 007603f0695a658b6bfa6c1ab1173b4483004c13
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843926"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Porady: kodu JavaScript profilu na stronach sieci web

Visual Studio Profiling Tools może zbierać dane wydajności dotyczące kodu JavaScript, która wykonuje w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, dowolnego strony sieci web lub aplikacji JavaScript za pomocą metoda profilowania instrumentacji. Wymaga programu Internet Explorer 8 lub nowszy.

> [!WARNING]
> Aby profilować kod JavaScript w aplikacji platformy uniwersalnej systemu Windows, temacie [pamięć języka JavaScript](../profiling/javascript-memory.md) 

Profilowanie Kreator służy do utworzenia sesji wydajności. Określ metody instrumentacji, a następnie określ JavaScript profilowania opcji na stronie Instrumentacji w oknie dialogowym właściwości sesji wydajności.

Po określeniu profilowanie plików JavaScript, kod JavaScript, który jest wykonywany w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] są sprofilować kodu wykonywanego na serwerze.

- Dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, kod JavaScript wykonujący w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] są sprofilować kodu wykonywanego na serwerze.

- Dla dowolnego strony sieci web jest profilowane kod JavaScript, która wykonuje w przeglądarce.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci web ASP.NET

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu sieci web w programie Visual Studio.

2. Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów**.

3. Na pierwszej stronie kreatora osiągów określ **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora, upewnij się, że bieżący projekt jest wybrany na liście elementów docelowych, a następnie kliknij przycisk **dalej.**

5. Na trzeciej stronie kreatora wybierz **JavaScript profilu** pole wyboru, a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora, kliknij przycisk **Zakończ** można uruchomić aplikacji sieci web w przeglądarce.

7. Wykonuje funkcje, które chcesz profilu.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilowanie kodu JavaScript w poszczególnych stron sieci web lub aplikacji JavaScript

1. Otwórz program Visual Studio.

2. Na **Analizuj** menu, kliknij przycisk **Uruchom Kreatora osiągów**.

3. Na pierwszej stronie kreatora osiągów określ **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora, kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **dalej.**

5. Na trzeciej stronie kreatora:

    1. Wpisz adres URL strony w **jakim adresem URL lub ścieżką będzie działała aplikacja sieci** pole.

    2. Wybierz **JavaScript profilu** pole wyboru, a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora, kliknij przycisk **Zakończ** można uruchomić strony sieci web w przeglądarce.

7. Wykonuje funkcje, które chcesz profilu.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.