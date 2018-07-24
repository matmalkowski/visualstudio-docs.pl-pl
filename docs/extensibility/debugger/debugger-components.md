---
title: Składniki debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efdba3366168a6e60fa88bd23e36f6ef487e979a
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203602"
---
# <a name="debugger-components"></a>Składniki debugera
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugera jest zaimplementowany jako pakietu VSPackage i zarządza cały debugowanie. Sesja debugowania obejmuje następujące elementy:  
  
-   **Pakiet debugowania:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera zawiera ten sam interfejs użytkownika, niezależnie od tego, co jest debugowany.  
  
-   **Menedżer debugowania sesji (SDM):** zapewnia spójny interfejs programistyczny do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera dla zarządzania szereg aparaty debugowania. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Menedżer debugowania procesów (menedżerów PDM):** służy do zarządzania, dla wszystkich uruchomionych wystąpieniach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], listę wszystkich programów, które mogą być lub są debugowane. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Debugowanie aparatu (DE):** jest odpowiedzialny za monitorowanie debugowanego programu komunikacji stan uruchomionego programu SDM i menedżerów PDM oraz interakcji z nimi Ewaluator wyrażeń i dostawca symboli zapewniają analizę w czasie rzeczywistym Stan zmiennych i pamięci programu. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla języków, obsługuje on) i dostawców innych firm, którzy mają być obsługiwane ich w czasie wykonywania. 
  
-   **Ewaluator wyrażeń (EE):** zapewnia obsługę dynamicznie Szacowanie zmiennych i wyrażeń, dostarczone przez użytkownika, gdy program został zatrzymany w określonym punkcie. Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla języków, obsługuje on) i od innych dostawców, którzy mają być obsługiwane w ich własnym języku.  
  
-   **Dostawca symboli (SP):** jest określana skrótem obsługi symboli, mapuje symbole debugowania programu uruchomionego wystąpienia programu, dzięki czemu można podać istotnych informacji (takich jak ocena debugowania i wyrażenie poziomie kodu źródłowego). Jest implementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (Aby uzyskać środowisko uruchomieniowe języka wspólnego [CLR] symboli i bazy danych programu [PDB] symboli format pliku), jak również od innych dostawców, którzy mają własne własności sposób przechowywania informacji o debugowaniu.  
  
 Na poniższym diagramie przedstawiono relację między tymi elementami debugera programu Visual Studio.  
  
 ![Przegląd składników debugowania](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Pakiet debugowania](../../extensibility/debugger/debug-package.md)  
 W tym artykule omówiono debugowanie pakietu, który jest uruchamiany w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki i obsługuje cały interfejs użytkownika.  
  
 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)  
 Zawiera omówienie funkcji menedżerów PDM, czyli menedżera procesów, które mogą być debugowane.  
  
 [Menedżer debugowania sesji](../../extensibility/debugger/session-debug-manager.md)  
 Definiuje SDM, co zapewnia spójny widok sesji debugowania środowiska IDE. SDM zarządza DE.  
  
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)  
 Dokumenty debugowania usług, które zapewnia DE.  
  
 [Tryby operacyjne](../../extensibility/debugger/operational-modes.md)  
 Zawiera omówienie trzech trybów, w których może działać IDE: projektowania trybu, tryb uruchamiania i trybie przerwania. Omówiono także mechanizmów przejścia.  
  
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)  
 Zawiera wyjaśnienie przeznaczenia EE w czasie wykonywania.  
  
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)  
 W tym artykule omówiono, jak to zrobić, na wdrażanie, dostawca symboli ocenia zmiennych i wyrażeń.  
  
 [Wizualizator typów i Przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 W tym artykule omówiono co Wizualizator typów i Przeglądarka niestandardowa są i jaką rolę Ewaluator wyrażeń odgrywa w obsłudze, obu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak DE działa jednocześnie w ramach kodu, dokumentację i konteksty oceny wyrażenia. W tym artykule opisano, dla każdego z trzech kontekstów, lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i wyrażeń.  
  
## <a name="see-also"></a>Zobacz także  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)