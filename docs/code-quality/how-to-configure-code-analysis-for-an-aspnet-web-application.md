---
title: 'Porady: Konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET w programie Visual Studio'
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
ms.openlocfilehash: bb1adaf9e97a950c6e9c53b3734debf5588fe0b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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