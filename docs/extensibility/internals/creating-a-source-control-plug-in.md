---
title: "Tworzenie wtyczki kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e376ced68301abae6090a87114e2178c0adc28cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-source-control-plug-in"></a>Tworzenie wtyczki kontroli źródła
Visual Studio SDK udostępnia zasoby, które umożliwiają dodanie możliwości kontroli źródła do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Umożliwia ona używać biblioteki DLL w dodatku, który jest zgodny z API dodatku typu Plug-in kontroli źródła opisane w niniejszej dokumentacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Opisuje sposób instalowania dodatku plug-in kontroli źródła i zaznacza aktualnie dostępne wersje interfejsu API dodatku typu Plug-in kontroli źródła.  
  
 [Architektura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Diagram architektury nawiązywał wyjaśnić integrację wtyczki z kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Przewodnik po testowym dla plug-in kontroli źródła](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Zawiera wskazówki dotyczące sposobu testowania instalacji i działania dodatku plug-in kontroli źródła.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie pakiet VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 W tym artykule omówiono sposób tworzenia kontroli źródła pakiet VSPackage, który nie tylko udostępnia funkcje kontroli źródła, ale zastępuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła formantu interfejsu użytkownika.  
  
 [Plug-in kontroli źródła](../../extensibility/source-control-plug-ins.md)  
 Zawiera pełną listę wszystkich elementów w interfejsie API dodatku typu Plug-in kontroli źródła.  
  
 [Kontrola źródła](../../extensibility/internals/source-control.md)  
 W tym artykule omówiono opcje implementacji jako funkcja zintegrowanego z kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].