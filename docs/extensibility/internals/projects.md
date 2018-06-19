---
title: Projekty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2ca4edabcee9f561dea51ea4b579ce194d13fa8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131015"
---
# <a name="projects"></a>Projekty
W programie Visual Studio, projekty są kontenerami, które deweloperzy korzystać w celu uporządkowania plików kodu źródłowego i innych zasobów, które są widoczne w **Eksploratora rozwiązań**. Projekty są zazwyczaj pliki (na przykład pliku .csproj, które projektu C#), które przechowują odwołania do plików kodu źródłowego i zasobów, takich jak pliki map bitowych. Projekty umożliwiają organizowanie, tworzenia, debugowania i wdrażania kodu źródłowego, odwołuje się do usług sieci Web i baz danych i innych zasobów. VSPackages mogą rozszerzać system projektu programu Visual Studio przede wszystkim na trzy sposoby: *typy projektów*, *projektu podtypów*, i *narzędzi niestandardowych*.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 *Typy projektów* obsługę nowych rodzajów projektach, takich jak języków programowania. Na przykład każdego języka, który obsługuje Visual Studio ma własny typ projektu i typu projektu w języku IronPython zawiera przykładowe integracji IronPython. Należy utworzyć typ projektu dla języków innych niż C# lub Visual Basic można dostosować sposób elementy są wbudowane, debugowania, wdrożone i wyświetlane w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [typów projektów](../../extensibility/internals/project-types.md).  
  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 *Projekt podtypów* są oparte na typy projektów i można dostosować sposób projekty są wbudowane, debugowania i wdrażane. Visual Studio będzie korzystać podtypów projektu z projektami urządzenia przenośne; dostosowywaniu wdrożenia przez skopiowanie nowo utworzony programu z komputera, na urządzeniu docelowym. C# i Visual Basic typy projektu może służyć jako podstawa dla podtypów projektu; Nie można typów projektów C++. Własnych typów projektu mogą służyć jako podstawa dla podtypów projektu. Aby uzyskać więcej informacji, zobacz [podtypów projektu](../../extensibility/internals/project-subtypes.md).  
  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)  
 W tym artykule wyjaśniono projektu sieci Web, który z kolei tworzenie aplikacji sieci Web.  
  
 [Generowanie nowego projektu: Kulisy, część jednego](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [nowej generacji projektu: Kulisy, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Wyjaśnienie działań faktycznie podczas tworzenia nowego projektu.  
  
 [Przykłady VSSDK](http://aka.ms/vs2015sdksamples)  
 Zawiera przykłady w VSSDK, które zajmują się projekty i rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wewnątrz zestawu Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Opis różnych aspektów rozszerzalności programu Visual Studio.