---
title: Wdrażanie projektu typów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127978"
---
# <a name="deploying-project-types"></a>Wdrażanie projektu typów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instaluje nowy agregator typu projektu (ProjectAggregator2.dll), a także pakiet Instalatora Windows w celu rozpowszechniania (ProjectAggregator2.msi). Należy użyć nowego agregatora dla typów projektów kodu zarządzanego. ProjectAggregator2 działa arounds ograniczenia w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregator, który uniemożliwiać poprawne działanie typów projektów kodu zarządzanego. W poniższych krokach opisano sposób zmiany VSPackage do użycia nowego agregatora.  
  
1.  Usunięcie NativeHierarchyWrapper projektu z rozwiązania.  
  
2.  Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.  
  
3.  Dodaj ProjectAggregator2.msi do ustawienia.