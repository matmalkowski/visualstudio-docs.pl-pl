---
title: "Przykładowe rozszerzenie kodowanych testów UI dla programu Excel | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a446fbf087441be9e02c54314d05845ce759e47b
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Przykładowe rozszerzenie kodowanych testów UI dla programu Excel
Składnik rozszerzenia próbki jest uruchamiany w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] procesu kodowanego testu interfejsu użytkownika i jest nieco hierarchiczna z `ExtensionPackage` klasy na podstawowym. `TechnologyManager`, `ActionFilter`, I `PropertyProvider` klasy są przy następnym poziomu, elementów kontroli na najwyższym poziomie.

 ![Architektura rozszerzenia testu w programie Excel](../test/media/excel_extarch.png "Excel_ExtArch") Architektura rozszerzenia w programie Excel

## <a name="extension-points"></a>Punkty rozszerzenia
 Te klasy reprezentują punkty rozszerzenia, które są wdrażane w przykładzie, aby umożliwić testowanie pod kątem kodowanego interfejsu użytkownika [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

### <a name="extensionpackage"></a>ExtensionPackage
 Dziedziczone z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> klasa, jest punkt wejścia dla kodowanego interfejsu użytkownika, testowanie rozszerzenia. Implementowanie ta klasa ogólna zapewnia kodowanego interfejsu użytkownika sprawdzania dostępu wewnętrzny framework do niestandardowego Menedżera technologii testu interfejsu użytkownika, Dostawca właściwości testu interfejsu użytkownika i filtr akcji testu interfejsu użytkownika do testowania nowego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [klasa ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Dziedziczone z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> klasy, ta klasa udostępnia Menedżera technologii dla testu rejestrowaniem i odtwarzaniem. Aby uzyskać więcej informacji, zobacz [klasa TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Dziedziczone z <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> klasy, ta klasa udostępnia klasę podstawową dla agregacji podobne wyniki akcji testu w wyniku pojedynczy test. Aby uzyskać więcej informacji, zobacz [klasa ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Elementy technologii
 Odziedziczone po klasie podstawowej <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasa stanowi podstawę dla elementów technologii, w które mogą być rejestrowane i odtwarzania testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [klasy elementów](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Dziedziczone z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> klasy, ta klasa udostępnia klasę podstawową dla obsługi właściwości elementów interfejsu użytkownika dla rejestrowania testu i odtwarzania. Aby uzyskać więcej informacji, zobacz [klasa PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Extensionpackage — klasa](../test/sample-excel-extension-extensionpackage-class.md)
- [Klasa TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)
- [Klasa ActionFilter](../test/sample-excel-extension-actionfilter-class.md)
- [Klasy elementów](../test/sample-excel-extension-element-classes.md)
- [Klasa PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
