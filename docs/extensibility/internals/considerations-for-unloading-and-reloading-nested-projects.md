---
title: Zagadnienia dotyczące zwolnienie i ponowne załadowanie zagnieżdżone projektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f22575c4affa6e6a13ea80b32674a3e517202fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Zagadnienia dotyczące zwalniania i przeładunku zagnieżdżonych projektów

Podczas implementowania projektu zagnieżdżonego typy, można wykonać dodatkowe kroki, jeśli zwolnisz i załaduj ponownie projektów. Poprawnie o do rozwiązania zdarzeń, musi poprawnie wygenerować `OnBeforeUnloadProject` i `OnAfterLoadProject` zdarzenia.

Jest jednym z powodów wywołania tych zdarzeń do kontroli kodu źródłowego (SCC). Nie chcesz SCC usunąć elementy z serwera, a następnie dodać je jako *nowe* w przypadku `Get` SCC podczas operacji. W takim przypadku nowy plik będzie można załadować poza SCC. Będzie konieczne zwolnienie i ponowne załadowanie wszystkich plików w przypadku, gdy są one różne.

Wywołania kontroli kodu źródłowego `ReloadItem`. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfejs do wywołania `OnBeforeUnloadProject` i `OnAfterLoadProject` Usuń projekt i utwórz go ponownie. Po zaimplementowaniu interfejsu w ten sposób SCC jest informowany projektu zostało tymczasowo usunięty i dodany ponownie. W związku z tym SCC nie działają na projekt tak, jakby była projektu *faktycznie* usunięty i ponownie dodany.

## <a name="reloading-projects"></a>Ponowne ładowanie projektów

Do obsługi ponownego ładowania projektów zagnieżdżone, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody. W implementacji `ReloadItem`, zamknij zagnieżdżonych projektów, a następnie ponownie utwórz je.

Zwykle po załadowaniu projektu, uruchamia IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> zdarzenia. Zagnieżdżonych projektów, które usunąć i ponownie załadować projektu nadrzędnego inicjuje proces nie IDE. Ponieważ projektu nadrzędnego nie wywoływanie zdarzeń rozwiązania, a IDE nie ma informacji o inicjowania procesu, zdarzenia nie są zgłaszane.

Aby obsługiwać ten proces wywołania projektu nadrzędnego `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> interfejsu. `IVsFireSolutionEvents` ma funkcje, które informują IDE, aby podnieść `OnBeforeUnloadProject` zdarzenie, aby zwolnić projektu zagnieżdżonego, a następnie wywołać `OnAfterLoadProject` zdarzeń, aby ponownie załadować samego projektu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)