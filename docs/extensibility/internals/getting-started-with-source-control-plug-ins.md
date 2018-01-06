---
title: "Wprowadzenie do korzystania z wtyczki kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 197cc0f0997e80d6cae277c4b19c5bbc82dce805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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