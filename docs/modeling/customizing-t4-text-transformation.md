---
title: "Dopasowanie przekształcenia tekstu T4 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: "28"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 4909edabd71686948632f390dfeed5f49cb6fca0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-t4-text-transformation"></a>Dopasowanie przekształcenia tekstu T4
Szablony tekstowe są funkcją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] umożliwiające generowanie kodu programu lub inne pliki tekstowe, proces przekształcenia. Przy użyciu [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], można rozszerzyć domyślny proces przekształcania szablonu dostosowując procesora dyrektywy szablonu tekstu lub hosta szablonu tekstowego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Proces transformacji szablonu tekstowego](../modeling/the-text-template-transformation-process.md)  
 W tym artykule opisano, jak działa transformacji tekstu i opisano rolę hosta szablonu i procesory dyrektywy.  
  
 [Tworzenie procesory dyrektywy szablonu tekstowego T4 niestandardowych](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Procesor dyrektywy dotyczy dyrektywy w szablonie, takich jak `<#@template#>.` jest uruchamiany podczas tworzenia szablonu, a można załadować zestawów i innych zasobów. Można także wstawić kod, który zostanie załadowany zasobów w czasie wykonywania. Definiując własne procesora dyrektywy, można zmniejszyć złożoność szablonów.  
  
 [Wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Jeśli piszesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenie, np. menu polecenie lub procedury obsługi zdarzeń, rozszerzenie można użyć usługi tworzenia szablonów tekstowych do przekształcania dowolnego szablonu tekstu. Przekazywanie danych parametru do szablonu, za pomocą obiektu sesji i uzyskiwanie wartości z szablonu przy użyciu `<#@parameter#>` dyrektywy.  
  
 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Wykonuje kod szablonu tekstowego, hosta zapewniają dostęp do zewnętrznych plików i stan aplikacji. Na przykład host, który uruchamia transformacji tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można zapewnić dostęp do Eksploratora rozwiązań. Wyświetla również błędy w oknie komunikat błędu. Jeśli chcesz uruchamiać transformacji tekstu w kontekście innej można zdefiniować własny hosta, który zapewnia dostęp do usług, które są dostępne w tym kontekście.  
  
 Jeśli piszesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenie, należy rozważyć użycie istniejącej usługi przekształcania tekstu zamiast zapisywania własnych hosta. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Tematy pomocy  
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)  
  
 Udostępnia składni dyrektywy szablonu tekstu i bloków sterowania.