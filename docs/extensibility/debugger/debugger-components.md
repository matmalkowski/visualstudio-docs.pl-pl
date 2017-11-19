---
title: "Debuger składniki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec2b7a18dac9616db1743a50539c2860caca2e26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-components"></a>Składniki debugera
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugera jest wdrażany jako pakiet VSPackage i zarządza nimi cała debugowanie. Sesja debugowania obejmuje następujące elementy:  
  
-   **Pakiet debugowania:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera udostępnia interfejs użytkownika niezależnie od tego, co jest debugowany.  
  
-   **Menedżer sesji debugowania (SDM):** zapewnia spójny interfejs programowy do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debuger w celu zarządzania różnych aparaty debugowania. Jest implementowany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Menedżer debugowania procesu (PDM):** służy do zarządzania, dla wszystkich uruchomionych wystąpieniach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], listę wszystkich programów, które mogą być lub są debugowane. Jest implementowany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **(DE) aparatu debugowania:** jest odpowiedzialna za monitorowanie programu debugowany, komunikuje stanu uruchomiony program SDM i PDM i interakcji z Ewaluator wyrażeń i dostawcy symbol zapewnienie analizy w czasie rzeczywistym Stan zmiennych i pamięci programu. Jest implementowany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla języków, obsługuje on) i innych dostawców, którzy mają być obsługiwane własnych w czasie wykonywania.  
  
-   **Ewaluator wyrażeń (EE):** zapewnia obsługę dynamicznie oceny zmiennych i wyrażeń podane przez użytkownika, gdy program został zatrzymany w określonym punkcie. Jest implementowany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla języków, obsługuje on) i innych dostawców, którzy mają być obsługiwane języki własnych.  
  
-   **Symbol dostawcy:** skrót obsługi symboli, mapy symbole debugowania programu uruchomione wystąpienie programu, aby uzyskać przydatne informacje można podać (na przykład poziomu źródła kodu do debugowania i wyrażenia w celu oceny). Jest implementowany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (dla środowiska CLR [CLR] symbole i bazy danych programu [plik PDB] symbolu format pliku) oraz przez innych dostawców, którzy mają własne zastrzeżonych metoda przechowywania informacji o debugowaniu.  
  
 Na poniższym diagramie przedstawiono związek między tymi elementami debuger programu Visual Studio.  
  
 ![Przegląd składników debugowania](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Debugowanie pakietu](../../extensibility/debugger/debug-package.md)  
 W tym artykule omówiono pakietu debugowania, w którym jest uruchomiona w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłokę i obsługuje wszystkie interfejsu użytkownika.  
  
 [Menedżer debugowania procesu](../../extensibility/debugger/process-debug-manager.md)  
 Zawiera omówienie funkcji PDM, czyli menedżera procesów, które może być debugowany.  
  
 [Menedżer sesji debugowania](../../extensibility/debugger/session-debug-manager.md)  
 Definiuje SDM, co zapewnia spójny obraz sesji debugowania do środowiska IDE. SDM zarządza DE.  
  
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)  
 Dokumenty debugowania usług, które zapewnia DE.  
  
 [Tryby operacyjne](../../extensibility/debugger/operational-modes.md)  
 Omówienie trzech trybów, w których może działać IDE: Projektowanie tryb, w trybie uruchamiania i tryb przerwania. Omówiono także mechanizmów przejścia.  
  
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)  
 Objaśnienie jego przeznaczenia EE w czasie wykonywania.  
  
 [Dostawca — symbol](../../extensibility/debugger/symbol-provider.md)  
 W tym artykule omówiono, jak to zrobić, w implementacji dostawcy symbol ocenia zmiennych i wyrażeń.  
  
 [Typ wizualizatora i podglądu niestandardowego](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 W tym artykule omówiono co typ wizualizatora i podglądu niestandardowego są i jaką rolę ewaluatora wyrażenia odtworzenie w obu obsługi.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Zawiera opis głównych pojęć architektury debugowania.  
  
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)  
 W tym artykule wyjaśniono, jak DE działa jednocześnie w ramach kodu, dokumentacji i konteksty Obliczanie wyrażenia. Opisuje, dla każdego z trzech kontekstów lokalizacji, pozycja lub oceny odpowiednie do niego.  
  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i obliczaniu wyrażeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)