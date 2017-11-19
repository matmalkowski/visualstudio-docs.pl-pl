---
title: 'Porady: Konfigurowanie analizy kodu dla aplikacji sieci Web programu ASP.NET | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dbc2ba8f78cc8f38bce62adbd3d91604875bffa3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Porady: konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET
W [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] i [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] można wybrać z listy analizy kodu *zestawów reguł* do zastosowania do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. Domyślny zestaw reguł jest reguł zalecanych minimalna firmy Microsoft. Można wybrać innego zestawu reguł do zastosowania do witryny sieci Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Aby skonfigurować zestaw reguł dla projektu struktury strony ASP.NET  
  
1.  Wybierz witrynę sieci Web w **Eksploratora rozwiązań**.  
  
2.  Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla witryny sieci Web**.  
  
3.  Jeśli wybrano rozwiązania i rozwiązanie ma więcej niż jednego projektu, zaznacz kompilacji konfiguracji i obiekt docelowy system operacyjny z **konfiguracji** i **platformy** listy.  
  
4.  Dla każdego projektu w rozwiązaniu, kliknij przycisk **zestawu reguł** kolumny, a następnie kliknij przycisk Nazwa reguły jest ustawiony na uruchomienie.  
  
5.  Domyślnie uruchamiania analizy kodu dla wszystkich projektów w rozwiązaniu. Aby wyłączyć lub włączyć analizy kodu dla konkretnego projektu, wykonaj następujące kroki:  
  
    1.  Kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk Właściwości.  
  
    2.  Zaznacz lub usuń zaznaczenie **Włącz analizę kodu** pole wyboru. Można również uruchomić kod — analiza ręcznie, wybierając **Uruchom analizę kodu na witrynie sieci Web** z **Analizuj** menu.  
  
6.  W **Uruchom ten zestaw reguł** listy rozwijanej liście, wykonaj następujące kroki:  
  
    -   Wybierz zestaw reguł, którego chcesz używać.  
  
    -   Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły niestandardowe, których nie ma na liście.  
  
    -   Definiowanie niestandardowego zestawu reguł. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).