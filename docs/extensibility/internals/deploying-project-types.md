---
title: "Wdrażanie projektu typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7673839e44e913d7d0a219400142fe7e6a0b95e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-project-types"></a>Wdrażanie projektu typów
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instaluje nowy agregator typu projektu (ProjectAggregator2.dll), a także pakiet Instalatora Windows w celu rozpowszechniania (ProjectAggregator2.msi). Należy użyć nowego agregatora dla typów projektów kodu zarządzanego. ProjectAggregator2 działa arounds ograniczenia w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregator, który uniemożliwiać poprawne działanie typów projektów kodu zarządzanego. W poniższych krokach opisano sposób zmiany VSPackage do użycia nowego agregatora.  
  
1.  Usunięcie NativeHierarchyWrapper projektu z rozwiązania.  
  
2.  Usuń wszystkie pliki binarne NativeHierarchyWrapper z konfiguracji.  
  
3.  Dodaj ProjectAggregator2.msi do ustawienia.