---
title: 'Porady: Tworzenie funkcji niestandardowej oraz zasady walidacji pakietu dla rozwiązań SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1d36b049aefe9eb574809cfedf4aa1f2ebddbc4c
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120579"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Porady: Tworzenie funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności dla rozwiązań SharePoint
  Można utworzyć niestandardowe reguły walidacji można zweryfikować pakietu rozwiązania generowane przez program Visual Studio. Można wykonać pełnej weryfikacji w całej funkcji lub pakietu, wybierając **weryfikacji** z menu kontekstowego pakietu lub funkcji w **PackagingExplorer**. Częściowego sprawdzania poprawności jest wykonywane podczas dodawania nowych elementów projektu SharePonit lub funkcje do projektu, aby określić pakietu lub funkcji działałoby w prawidłowym stanie.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Aby utworzyć regułę sprawdzania poprawności pakietu niestandardowego  
  
1.  Tworzenie projektu biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje jednej z następujących interfejsów:  
  
    -   Aby utworzyć reguły sprawdzania poprawności pakietu, należy zaimplementować <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfejsu.  
  
    -   Aby utworzyć regułę funkcji sprawdzania poprawności, zaimplementuj <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfejsu.  
  
4.  Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy. Ten atrybut umożliwia Visual Studio, aby odnaleźć i załadować reguły sprawdzania poprawności. Przekaż <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> lub <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> typu konstruktora atrybutu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak utworzyć niestandardowe reguły walidacji funkcji.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [narzędzia wdrażania rozszerzeń dla programu SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
