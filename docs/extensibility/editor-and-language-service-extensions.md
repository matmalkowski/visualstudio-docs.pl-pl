---
title: Edytor i języka usługi rozszerzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2fceb0487c23dc34d3f4f4937d7a5998340ae3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="editor-and-language-service-extensions"></a>Edytora i rozszerzenia usługi języka
Można rozszerzyć większość funkcji edytora kodu programu Visual Studio. Edytor jest oparta na systemie Windows Presentation Foundation (WPF) i jest zapisywany w kodzie zarządzanym. Mimo że ten projekt różni się od projektów we wcześniejszych wersjach programu Visual Studio, zawiera większość tej samej funkcji. Do rozszerzania edytora, użyj Framework Managed Extensibility (MEF).  
  
 Visual Studio SDK udostępnia kart znany jako *podkładek* do obsługi VSPackages napisanych dla wcześniejszych wersji. Jeśli masz istniejący pakiet VSPackage, firma Microsoft zaleca jednak zaktualizować go do nowej technologii, aby uzyskać większą wydajność i niezawodność.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Wprowadzenie do korzystania z szablonów elementów edytora.|  
|[Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)|Linki do dokumentów, projektowania oraz funkcje edytora podstawowych, które pokazują, jak jego rozszerzenia.|  
|[Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)|Linki do dokumentów, które opisują sposób uzyskać dostęp do edytora core z istniejącego kodu.|  
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Linki do dokumentów, które zawierają opis tworzenia niestandardowych edytory.|  
|[Rozszerzalność starszej wersji usługi językowej](../extensibility/internals/legacy-language-service-extensibility.md)|Linki do dokumentów, których opisano sposób integracji języków programowania w Visual Studio.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Wprowadza Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Wprowadza Windows Presentation Foundation (WPF).|