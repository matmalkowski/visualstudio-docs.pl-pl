---
title: Projekty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: "43"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c175d85b55734df841f30d131639c3bfeed40361
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="projects"></a>Projekty
W programie Visual Studio, projekty są kontenerami, które deweloperzy korzystać w celu uporządkowania plików kodu źródłowego i innych zasobów, które są widoczne w **Eksploratora rozwiązań**. Projekty są zazwyczaj pliki (na przykład pliku .csproj, które projektu C#), które przechowują odwołania do plików kodu źródłowego i zasobów, takich jak pliki map bitowych. Projekty umożliwiają organizowanie, tworzenia, debugowania i wdrażania kodu źródłowego, odwołuje się do usług sieci Web i baz danych i innych zasobów. VSPackages mogą rozszerzać system projektu programu Visual Studio przede wszystkim na trzy sposoby: *typy projektów*, *projektu podtypów*, i *narzędzi niestandardowych*.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 *Typy projektów* obsługę nowych rodzajów projektach, takich jak języków programowania. Na przykład każdego języka, który obsługuje Visual Studio ma własny typ projektu i typu projektu w języku IronPython zawiera przykładowe integracji IronPython. Należy utworzyć typ projektu dla języków innych niż C# lub Visual Basic można dostosować sposób elementy są wbudowane, debugowania, wdrożone i wyświetlane w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [typów projektów](../../extensibility/internals/project-types.md).  
  
 [Podtypów projektu](../../extensibility/internals/project-subtypes.md)  
 *Projekt podtypów* są oparte na typy projektów i można dostosować sposób projekty są wbudowane, debugowania i wdrażane. Visual Studio będzie korzystać podtypów projektu z projektami urządzenia przenośne; dostosowywaniu wdrożenia przez skopiowanie nowo utworzony programu z komputera, na urządzeniu docelowym. C# i Visual Basic typy projektu może służyć jako podstawa dla podtypów projektu; Nie można typów projektów C++. Własnych typów projektu mogą służyć jako podstawa dla podtypów projektu. Aby uzyskać więcej informacji, zobacz [podtypów projektu](../../extensibility/internals/project-subtypes.md).  
  
 [Projekty sieci Web](../../extensibility/internals/web-projects.md)  
 W tym artykule wyjaśniono projektu sieci Web, który z kolei tworzenie aplikacji sieci Web.  
  
 [Generowanie nowego projektu: Kulisy, część jednego](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) i [nowej generacji projektu: Kulisy, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Wyjaśnienie działań faktycznie podczas tworzenia nowego projektu.  
  
 [Przykłady VSSDK](http://aka.ms/vs2015sdksamples)  
 Zawiera przykłady w VSSDK, które zajmują się projekty i rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [W programie Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Opis różnych aspektów rozszerzalności programu Visual Studio.