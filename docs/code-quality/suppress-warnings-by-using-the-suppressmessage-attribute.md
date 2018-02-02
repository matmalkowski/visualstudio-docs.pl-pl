---
title: "Tłumienie ostrzeżeń przy użyciu atrybutu SuppressMessage | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCFxCopTool.InputAssemblyFileName
- VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile
- VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression
- VC.Project.VCFxCopTool.OutputFile
helpviewer_keywords:
- code analysis, source suppression
- source suppression
- SuppressMessage attribute
- code analysis, SuppressMessage attribute
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ce246c0ff960c78aed1901618fdc26bff97779d2
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2018
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>Tłumienie ostrzeżeń przy użyciu atrybutu SuppressMessage
Warto często oznaczać, że to ostrzeżenie jest nonapplicable, aby umożliwić członkom zespołu dowiedzieć się, że zostało sprawdzone kod i ustalono, że można pominąć to ostrzeżenie. Pomijanie źródła (ISS) umożliwia deweloperom umieść atrybut, który powoduje pominięcie ostrzeżenia bliski lokalizacji, który wygenerował ostrzeżenia. Można dodać atrybutu ISS bezpośrednio w pliku źródłowym lub skorzystać z menu skrótów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|||  
|-|-|  
|[Pomijanie w kodzie źródłowym — przegląd](../code-quality/in-source-suppression-overview.md)|Więcej informacji na temat ISS i jak z niego korzystać w kodzie.|  
|[Instrukcje: Pomijanie ostrzeżeń przy użyciu pozycji menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Dowiedz się, jak pomijanie ostrzeżeń w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE przy użyciu menu skrótów.|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)