---
title: "Edytor i języka usługi rozszerzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 59de764dfcb976dfac303f44a67340e117ae5e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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