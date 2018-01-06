---
title: Dokumentacja interfejsu API dla modelowania zestawu SDK dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: "8"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: c5dace5862354c26a22b65b3f471163e50738c7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio
Visual Studio wizualizacji i modelowania SDK udostępnia platformy, na którym są wbudowane narzędziami języki specyficzne dla domeny (DSL).  
  
 Ta sekcja zawiera materiału odwołania do przestrzeni nazw, które mają nazwy zaczynające się od "Microsoft.VisualStudio.Modeling".  
  
|Przestrzeń nazw|Zawartość|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy takie jak element modelu, który jest klasą bazową dla wszystkich klas domeny zdefiniowanych w DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy, które stanowią część definicji DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Podgląd magazynu i wydajności pomiaru narzędzi modelu.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy takie jak ShapeElement, które jest klasą bazową dla wszystkich kształtów, które można zdefiniować w DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gest i wybór metod.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API definicji DSL projektanta.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Klasy wewnętrzne definicji DSL projektanta.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które umożliwiają rozszerzanie Projektant DSL z poleceń i gestów sprawdzania poprawności.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzenia dla ModelElement, które implementują rozszerzalności DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atrybuty rozszerzalności|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umożliwia tworzenie modelu tylko do odczytu.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Modelbus interfejsu API, która ułatwia integrowanie różne modele.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Okno dialogowe, które umożliwia użytkownikom przechodzenie do modeli i elementów do tworzenia odwołań Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Usługa selektora.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Struktury karty Modelbus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Okno dialogowe selektora, który umożliwia użytkownikom przechodzenie do modeli i elementów do tworzenia odwołań Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między DSLs i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie polecenia menu skrótów (context).|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia definiowanie ograniczeń walidacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)
