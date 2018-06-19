---
title: Zapewnianie automatyzacji do VSPackages | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131583"
---
# <a name="providing-automation-for-vspackages"></a>Zapewnianie automatyzacji do VSPackages
Istnieją dwa sposoby zapewnienia automatyzacji dla Twojego VSPackages: zaimplementowanie obiekty specyficzne pakiet VSPackage i wdrażając obiektów automatyzacji w wersji standard. Ogólnie rzecz biorąc są one używane razem Rozszerzanie modelu automatyzacji środowiska.  
  
## <a name="vspackage-specific-objects"></a>Pakiet VSPackage określonych obiektów  
 Niektóre miejsca w ramach modelu automatyzacji wymagają podania obiekty automatyzacji, które są unikatowe dla VSPackage. Na przykład nowych projektów wymagają różnych obiektów, które zawiera tylko VSPackage. Nazwy tych obiektów są wprowadzane w rejestrze i pobierane za pośrednictwem wywołania w środowisku `DTE` obiektu.  
  
 Pakiet VSPackage określonych obiektów można także uzyskać wykorzystującym konsumenta automatyzacji obiekt udostępniany za pośrednictwem właściwości obiektu standardowego obiektu. Na przykład standardowe `Window` obiekt ma `Object` właściwości, powszechnie znane jako `Windows.Object` właściwości. Gdy konsumenci wywołać `Window.Object` w oknie zaimplementowana w pakiecie VSPackage, możesz przesłać obiektu automatyzacji określonych własnego projektu.  
  
#### <a name="projects"></a>Projekty  
 VSPackages można rozszerzyć model automatyzacji dla nowych typów projektu za pomocą własnych obiekty specyficzne dla pakiet VSPackage. Podstawowy w celu zapewnienia nowych obiektów automatyzacji, VSPackage jest rozróżnianie unikatowy projektu obiektów z <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> lub <xref:VSLangProj80.VSProject2> obiektu. To zróżnicowanie jest przydatne, gdy chcesz zapewnić sposób wyróżnia lub iteracji typ projektu, oprócz innych typów projektów powinna występować side-by-side w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Zdarzenia  
 Architektura zdarzeń środowiska oferuje innym miejscu należy dołączyć obiektów specyficzne dla pakiet VSPackage. Na przykład przez tworzenie obiektów unikatowy zdarzeń, można rozszerzyć w środowisku model zdarzeń dla projektów. Możesz podać własne zdarzenia, po dodaniu nowego elementu do typu projektu. Aby uzyskać więcej informacji, zobacz [udostępnianie zdarzenia](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Obiekty okien  
 Systemu Windows można przesłać obiektu automatyzacji specyficzne dla pakiet VSPackage do środowiska po wywołaniu. Implementuje obiektu, który jest pochodną <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> lub `IDispatch` ponownie przekazuje właściwości rozszerzanie obiekt window, w którym jest ulokowany. Na przykład można użyć tej metody zapewnienie automatyzacji dla formantu ulokowany ramki okna. Semantyka tego obiektu i inne obiekty, które mogą rozszerzać go są do Ciebie do projektowania. Aby uzyskać więcej informacji, zobacz [porady: Podaj automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Opcje strony w menu Narzędzia  
 Można utworzyć strony, aby rozszerzyć narzędzia, opcje automatyzacji modelu za pomocą implementacja stron i dodawanie informacji do rejestru w celu utworzenia własnych opcji. Następnie można wywołać stron za pośrednictwem modelu obiektu środowiska, podobnie jak inne strony opcji. Jeśli projekt funkcji dodawanego do środowiska za pośrednictwem VSPackages wymaga strony opcji, należy dodać także obsługa automatyzacji. Aby uzyskać więcej informacji, zobacz [Obsługa automatyzacji dla strony opcji](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Obiekty automatyzacji w wersji Standard  
 Rozszerzenie automatyzacji dla projektów, można też wdrożyć obiektów automatyzacji w wersji standard (pochodną `IDispatch`) czy pozostawić obok inne obiekty projektu i implementuje standardowe metody i właściwości. Przykłady standardowych obiektów zawierają obiekty projektu, które są wstawiane do hierarchii rozwiązania, takie jak `Projects`, `Project`, `ProjectItem`, i `ProjectItems`. Każdy nowy typ projektu należy zaimplementować obiekty te (i prawdopodobnie innych protokołów w zależności od semantykę projektu).  
  
 W tym sensie tych obiektów podaj przeciwną zaletą obiektów pakiet VSPackage określonego projektu. Obiekty automatyzacji w wersji standard Zezwalaj projektu do użycia w sposób ogólnych, takich jak inny projekt obsługujące te same obiekty. W związku z tym dodatek zapisane przed ogólne `Project` i `ProjectItem` obiekty mogą działać z projektów dowolnego typu. Aby uzyskać więcej informacji, zobacz [projektu modelowania](../../extensibility/internals/project-modeling.md).