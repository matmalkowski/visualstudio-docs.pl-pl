---
title: "Zagadnienia dotyczące zwolnienie i ponowne załadowanie zagnieżdżone projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf34a3fe708a6ecab200262224da395b9fa37ecb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Zagadnienia dotyczące zwalniania i przeładunku zagnieżdżonych projektów
Podczas implementowania projektu zagnieżdżonego typy, można wykonać dodatkowe kroki, jeśli zwolnisz i załaduj ponownie projektów. Poprawnie o do rozwiązania zdarzeń, musi poprawnie wygenerować `OnBeforeUnloadProject` i `OnAfterLoadProject` zdarzenia.  
  
 Jedną z przyczyn musi wywołać te zdarzenia w ten sposób jest, że nie ma kontroli kodu źródłowego (SCC), aby usunąć elementy z serwera i dodać je ponownie jako nowy element w przypadku `Get` SCC podczas operacji. W takim przypadku nowy plik będzie można załadować poza SCC i konieczne zwolnienie i ponowne załadowanie wszystkich plików w przypadku, gdy są one różne. Wywołania SCC `ReloadItem`. Implementacji tego wywołania jest Usuń projekt i ponownie utworzyć ją ponownie Wdrażając `IVsFireSolutionEvents` do wywołania `OnBeforeUnloadProject` i `OnAfterLoadProject`. Podczas wykonywania tej implementacji SCC jest informowany projektu zostało tymczasowo usunięty i dodany ponownie. W związku z tym SCC nie będzie działać w projekcie, tak jakby projektu był rzeczywiście zostały usunięte z serwera i ponownie dodać.  
  
## <a name="reloading-projects"></a>Ponowne ładowanie projektów  
 Do obsługi ponownego ładowania projektów zagnieżdżone, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody. W implementacji `ReloadItem`, zamknij zagnieżdżonych projektów, a następnie ponownie utwórz je.  
  
 Zwykle po załadowaniu projektu, uruchamia IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> i `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` zdarzenia. Zagnieżdżone projektów, które zostanie usunięty i ponownie załadowany, projektu nadrzędnego inicjuje proces nie IDE. Ponieważ projektu nadrzędnego nie powoduje rozwiązania zdarzeń i IDE nie ma informacji o inicjowania procesu, zdarzenia nie są zgłaszane.  
  
 Aby obsługiwać ten proces wywołania projektu nadrzędnego `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfejsu wyłączanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interfejsu. `IVsFireSolutionEvents`ma funkcje, które informują IDE, aby podnieść `OnBeforeUnloadProject` zdarzenie, aby zwolnić projektu zagnieżdżonego, a następnie wywołać `OnAfterLoadProject` zdarzeń, aby ponownie załadować samego projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Projekty zagnieżdżenia](../../extensibility/internals/nesting-projects.md)