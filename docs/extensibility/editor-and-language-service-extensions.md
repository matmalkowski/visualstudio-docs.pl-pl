---
title: "Edytor i języka usługi rozszerzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e5ad07694604c7b61c922cd097809fa037e0501
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="editor-and-language-service-extensions"></a>Edytora i rozszerzenia usługi języka
Można rozszerzyć większość funkcji edytora kodu programu Visual Studio. Edytor jest oparta na systemie Windows Presentation Foundation (WPF) i jest zapisywany w kodzie zarządzanym. Mimo że ten projekt różni się od projektów we wcześniejszych wersjach programu Visual Studio, zawiera większość tej samej funkcji. Do rozszerzania edytora, użyj Framework Managed Extensibility (MEF).  
  
 Visual Studio SDK udostępnia kart znany jako *podkładek* do obsługi VSPackages napisanych dla wcześniejszych wersji. Jeśli masz istniejący pakiet VSPackage, firma Microsoft zaleca jednak zaktualizować go do nowej technologii, aby uzyskać większą wydajność i niezawodność.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Wprowadzenie do korzystania z szablonów elementów edytora.|  
|[Rozszerzanie edytora i usług języka](../extensibility/extending-the-editor-and-language-services.md)|Linki do dokumentów, projektowania oraz funkcje edytora podstawowych, które pokazują, jak jego rozszerzenia.|  
|[Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)|Linki do dokumentów, które opisują sposób uzyskać dostęp do edytora core z istniejącego kodu.|  
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Linki do dokumentów, które zawierają opis tworzenia niestandardowych edytory.|  
|[Rozszerzalność usługi starszej wersji języka](../extensibility/internals/legacy-language-service-extensibility.md)|Linki do dokumentów, których opisano sposób integracji języków programowania w Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Wprowadza Managed Extensibility Framework (MEF).|  
|[Program Windows Presentation Foundation](/dotnet/framework/wpf/index)|Wprowadza Windows Presentation Foundation (WPF).|