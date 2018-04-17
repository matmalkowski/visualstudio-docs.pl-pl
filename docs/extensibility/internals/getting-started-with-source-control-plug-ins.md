---
title: Wprowadzenie do korzystania z wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f5c88d932fd2915273c86924d2df8f1233baeed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-source-control-plug-ins"></a>Wprowadzenie do korzystania z wtyczki kontroli źródła
Aby utworzyć wtyczkę kontroli źródła, należy utworzyć bibliotekę DLL, która implementuje funkcje zdefiniowane w interfejsie API dodatku typu Plug-in kontroli źródła, a następnie można zarejestrować biblioteki DLL z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aby był dostępny do użytku w kontroli wersji kodu źródłowego.  
  
 Trzy wersje API dodatku typu Plug-in kontroli źródła (w wersji 1.1 i 1.2, 1.3) są dostępne dla plug-in kontroli źródła. API dodatku typu Plug-in kontroli źródła opisanych tutaj jest w wersji 1.3. Została zaprojektowana w celu pełnej zgodności z Plug-in kontroli źródła pomocniczych w wersji 1.1 i 1.2. [What's New in źródła formantu wtyczek interfejsu API w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) szczegółowo opisano nowe funkcje obsługiwane w najnowszej wersji interfejsu API dodatku typu Plug-in kontroli źródła.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: instalowanie wtyczki kontroli kodu źródłowego](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Opisuje sposób wprowadzania wpisy rejestru, które są wymagane do podłączenia w kontroli źródła biblioteki DLL.  
  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Krótki przegląd zmiany wprowadzone do interfejsu API dodatku typu Plug-in kontroli źródła w wersji 1.3.  
  
 [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Krótki przegląd zmiany wprowadzone do interfejsu API dodatku typu Plug-in kontroli źródła w wersji 1.2.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)  
 Zawiera pełną listę wszystkich elementów w interfejsie API dodatku typu Plug-in kontroli źródła.  
  
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiuje zestaw SDK dodatku typu Plug-in kontroli źródła i opisano dołączone zasoby.