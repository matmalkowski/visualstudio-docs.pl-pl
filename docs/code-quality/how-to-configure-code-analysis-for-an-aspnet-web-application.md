---
title: 'Porady: Konfigurowanie analizy kodu dla aplikacji internetowej ASP.NET w programie Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: c924a866f1bb34f41664fbf62e372b77f4d2620e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178240"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Porady: konfigurowanie analizy kodu dla aplikacji internetowej ASP.NET

W programie Visual Studio, możesz wybrać z listy analizy kodu *zestawów reguł* dotyczą [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web. Domyślny zestaw reguł jest reguł zalecanych Minimum firmy Microsoft. Możesz wybrać inny zestaw reguł, aby zastosować do witryny sieci web.

1. Wybierz witrynę sieci web w **Eksploratora rozwiązań**.

2. Na **analizy** menu, kliknij przycisk **Konfigurowanie analizy kodu dla witryny sieci Web**.

3. Jeśli rozwiązanie ma więcej niż jeden projekt zaznaczonego rozwiązanie, wybierz opcję kompilacji konfiguracji i docelowy system operacyjny z **konfiguracji** i **platformy** listy.

4. Dla każdego projektu w rozwiązaniu, kliknij przycisk **zestaw reguł** kolumny, a następnie kliknij przycisk, nazwa reguły jest ustawiony na uruchamianie.

5. Domyślnie analiza kodu jest uruchamiany na wszystkie projekty w rozwiązaniu. Aby wyłączyć lub włączyć analizy kodu dla konkretnego projektu, wykonaj następujące kroki:

    1. Kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie Właściwości.

    2. Zaznacz lub wyczyść **Włącz analizę kodu** pole wyboru. Można również uruchomić analizę kodu ręcznie, wybierając **Uruchom analizę kodu dla witryny sieci Web** z **analizy** menu.

6. W **Uruchom ten zestaw reguł** listy rozwijanej listy, wykonaj następujące kroki:

    - Wybierz zestaw reguł, który chcesz użyć.

    - Wybierz  **\<Przeglądaj >** do określenia, ustaw istniejącej reguły niestandardowe, który nie jest na liście.

    - Zdefiniuj [niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md).