---
title: "Porady: Konfigurowanie analizy kodu dla projektu zarządzanego kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 575b81e9c213e4025cd38921ad467869686d867c
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Porady: konfigurowanie analizy kodu dla projektu zarządzanego kodu

W programie Visual Studio, można wybrać z listy analizy kodu *zestawów reguł* do zastosowania do projektu zarządzanego kodu. Domyślny zestaw reguł jest reguł zalecanych Minimum firmy Microsoft. Można stosować inną regułę ustawiony jako projekt lub do wszystkich projektów w rozwiązaniu.  
  
> [!NOTE]
> Aby uzyskać informacje o sposobie konfigurowania zestawu reguł dla aplikacji sieci Web ASP.NET, zobacz [porady: Konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Aby skonfigurować zestaw reguł dla projektu .NET Framework  
  
1.  W **Eksploratora rozwiązań**, kliknij projekt.  
  
2.  Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla** *ProjectName*.  
  
3.  W **konfiguracji** i **platformy** listy, kliknij przycisk platformy kompilacji konfiguracji i obiekt docelowy.  
  
4.  Aby uruchomić kod — analiza za każdym razem, gdy projekt jest utworzony przy użyciu wybranej konfiguracji, wybierz **Włącz analizę kodu podczas kompilacji** pole wyboru. Można również uruchomić kod — analiza ręcznie, otwierając **Analizuj** menu i wybierając ** Uruchom analizę kodu na * ProjectName ***.  
  
5.  Domyślnie analizy kodu nie raportuje ostrzeżenia z kodu, który jest automatycznie generowany przez zewnętrznych narzędzi. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.  
  
    > [!NOTE]
    > Ta opcja nie odrzuca błędy analizy kodu i ostrzeżeń z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Jednocześnie można wyświetlać i obsługa kodu źródłowego dla formularza lub szablonu, bez konieczności jego zastąpienie.
  
6.  W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:  
  
    -   Kliknij zestaw reguł, który ma być używany.  
  
    -   Kliknij przycisk  **\<Przeglądaj >** określ zestaw istniejącej reguły niestandardowe, których nie ma na liście.  
  
    -   Definiowanie niestandardowego zestawu reguł.  
  
         Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Zobacz także

[Przewodnik: Konfigurowanie niestandardowego zestawu reguł i korzystanie z niego](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)