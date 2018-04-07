---
title: 'Porady: Konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET w programie Visual Studio | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 075382db550fae1198b0eca239be8efd1bfadff6
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Porady: konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET

W programie Visual Studio, możesz wybrać z listy analizy kodu *zestawów reguł* do zastosowania do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. Domyślny zestaw reguł jest reguł zalecanych Minimum firmy Microsoft. Można wybrać innego zestawu reguł do zastosowania do witryny sieci Web.

1. Wybierz witrynę sieci Web w **Eksploratora rozwiązań**.

2. Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla witryny sieci Web**.

3. Jeśli wybrano rozwiązania i rozwiązanie ma więcej niż jednego projektu, zaznacz kompilacji konfiguracji i obiekt docelowy system operacyjny z **konfiguracji** i **platformy** listy.

4. Dla każdego projektu w rozwiązaniu, kliknij przycisk **zestawu reguł** kolumny, a następnie kliknij przycisk Nazwa reguły jest ustawiony na uruchomienie.

5. Domyślnie uruchamiania analizy kodu dla wszystkich projektów w rozwiązaniu. Aby wyłączyć lub włączyć analizy kodu dla konkretnego projektu, wykonaj następujące kroki:

    1. Kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk Właściwości.

    2. Zaznacz lub usuń zaznaczenie **Włącz analizę kodu** pole wyboru. Można również uruchomić kod — analiza ręcznie, wybierając **Uruchom analizę kodu na witrynie sieci Web** z **Analizuj** menu.

6. W **Uruchom ten zestaw reguł** listy rozwijanej liście, wykonaj następujące kroki:

    - Wybierz zestaw reguł, którego chcesz używać.

    - Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły niestandardowe, których nie ma na liście.

    - Zdefiniuj [niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md).