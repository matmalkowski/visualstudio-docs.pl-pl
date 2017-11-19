---
title: "Wprowadzenie do rozszerzalności debugera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1419f4e45aefed59aa36b249568a53a47ad3c459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Wprowadzenie do rozszerzalności debugera
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Zawiera informacje potrzebne do tworzenia i dostosowywania debugera składniki używane do debugowania programów z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie zostało dodane ulepszenia pochodzące z szeroką gamę użyteczność testów wykonanych na poprzedniej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugery. Można użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania kroków aplikacji obsługi wielu języków, lub można wdrożyć na bieżąco edytowanie zmiennych podczas debugowania aplikacji i rozwiązań obsługi wielu języków.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie jest wykonywane poza procesem z debugowanego programu i dlatego ta opcja jest mniej pożądana w obszaru procesu aplikacji. W rezultacie jest pisanie składniki wchodzące w interakcje z debugera bez wpływu na debugowanie programu.  
  
 Najlepiej użyć [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], należy zapoznać się z następujących czynności:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE)  
  
-   Język programowania w języku C++  
  
-   ATL COM  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik po rozszerzanie debugera](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Zawiera opis procesu wdrażania debugowania w produkcie, w zależności od kompilujący i jego dane wyjściowe.  
  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania składniki, które zawierają aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Zawiera opis głównych pojęć architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak aparat debugowania (DE) działa jednocześnie w ramach kodu, dokumentacji i konteksty Obliczanie wyrażenia. Opisuje, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i obliczaniu wyrażeń.