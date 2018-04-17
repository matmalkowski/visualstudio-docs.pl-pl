---
title: Dopasowanie przekształcenia tekstu T4 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 158e39dfe01dd0016d622918082d6ec4874dc661
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-t4-text-transformation"></a>Dopasowanie przekształcenia tekstu T4
Szablony tekstowe są funkcją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] umożliwiające generowanie kodu programu lub inne pliki tekstowe, proces przekształcenia. Przy użyciu [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], można rozszerzyć domyślny proces przekształcania szablonu dostosowując procesora dyrektywy szablonu tekstu lub hosta szablonu tekstowego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md)  
 W tym artykule opisano, jak działa transformacji tekstu i opisano rolę hosta szablonu i procesory dyrektywy.  
  
 [Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Procesor dyrektywy dotyczy dyrektywy w szablonie, takich jak `<#@template#>.` jest uruchamiany podczas tworzenia szablonu, a można załadować zestawów i innych zasobów. Można także wstawić kod, który zostanie załadowany zasobów w czasie wykonywania. Definiując własne procesora dyrektywy, można zmniejszyć złożoność szablonów.  
  
 [Wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Jeśli piszesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenie, np. menu polecenie lub procedury obsługi zdarzeń, rozszerzenie można użyć usługi tworzenia szablonów tekstowych do przekształcania dowolnego szablonu tekstu. Przekazywanie danych parametru do szablonu, za pomocą obiektu sesji i uzyskiwanie wartości z szablonu przy użyciu `<#@parameter#>` dyrektywy.  
  
 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Wykonuje kod szablonu tekstowego, hosta zapewniają dostęp do zewnętrznych plików i stan aplikacji. Na przykład host, który uruchamia transformacji tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można zapewnić dostęp do Eksploratora rozwiązań. Wyświetla również błędy w oknie komunikat błędu. Jeśli chcesz uruchamiać transformacji tekstu w kontekście innej można zdefiniować własny hosta, który zapewnia dostęp do usług, które są dostępne w tym kontekście.  
  
 Jeśli piszesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenie, należy rozważyć użycie istniejącej usługi przekształcania tekstu zamiast zapisywania własnych hosta. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Tematy pomocy  
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)  
  
 Udostępnia składni dyrektywy szablonu tekstu i bloków sterowania.