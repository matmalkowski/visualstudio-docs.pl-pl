---
title: Szczegóły konfiguracji kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc10c7602f3298b532b4af76e66b43d469416ba5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134129"
---
# <a name="source-control-configuration-details"></a>Szczegóły konfiguracji kontroli źródła
Aby zaimplementować kontroli źródła, należy poprawnie skonfigurować system projektu lub edytora, aby wykonać następujące czynności:

-   Żądanie uprawnienia do przejścia do stanu zmienione

-   Żądanie uprawnienia do zapisania pliku

-   Żądanie uprawnienia do dodawania, usuwania lub zmiany nazwy plików w projekcie

## <a name="request-permission-to-transition-to-changed-state"></a>Żądanie uprawnienia do przejścia do stanu zmienione
 Projekt lub Edytor żądania uprawnień do przejścia do zmienionego stanu (dirty) przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Każdy edytorze, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> uprawnia do zatwierdzenia zmian w dokumencie ze środowiska przed zwróceniem `True` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Projekt jest zasadniczo edytora pliku projektu i w związku z tym ma tego samego odpowiedzialność dotyczące implementowania śledzenia zmienić stan pliku projektu, tak jak w przypadku edytora tekstu dla jego plików. Środowisko obsługi zmienione stan rozwiązania, ale musi obsługiwać zmienione stan dowolnego obiektu odwołuje się do rozwiązania, ale nie są zapisywane, takich jak plik projektu lub jego elementów. Ogólnie rzecz biorąc Jeśli projekt lub edytora jest odpowiedzialny za zarządzanie trwałości dla elementu, następnie odpowiada dotyczące implementowania śledzenia stanu zmienione.

 W odpowiedzi na `IVsQueryEditQuerySave2::QueryEditFiles` wywołać, środowisko, można wykonać następujące czynności:

-   Odrzuć wywołanie do zmiany, w którym to przypadku Edytor lub projekt musi pozostać w niezmienionym stanie (czyste).

-   Wskazuje, czy dane dokumentu powinny zostać ponownie załadowana. W projekcie środowiska spowoduje ponowne załadowanie danych dla projektu. Edytor musi ponownie załadować danych z dysku za pomocą jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementacji. W obu przypadkach kontekstu w projekcie lub edytorze, można zmienić po załadowaniu danych.

 Jest to zadanie złożonej i trudnej zakresie wyposażenia odpowiednie `IVsQueryEditQuerySave2::QueryEditFiles` wywołania na istniejący kod podstawowy. W związku z tym te wywołania powinna zostać włączona podczas tworzenia projektu lub edytora.

## <a name="request-permission-to-save-a-file"></a>Żądanie uprawnienia do zapisania pliku
 Przed projektu lub edytorze zapisuje plik, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Pliki projektu automatycznie wykonuje się tymi połączeniami za rozwiązania, które wie, kiedy można zapisać pliku projektu. Edytory są odpowiedzialne za wykonywanie tych wywołań, chyba że wykonania edytor `IVsPersistDocData2` funkcja Pomocnika <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Jeśli Edytor implementuje `IVsPersistDocData2` w ten sposób, a następnie wywołać `IVsQueryEditQuerySave2::QuerySaveFile` lub `IVsQueryEditQuerySave2::QuerySaveFiles` staje się automatycznie.

> [!NOTE]
>  Zawsze wywołań tych preemptively — to znaczy w czasie, gdy edytor jest możliwość anulowania.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Żądanie uprawnienia do dodawania, usuwania lub zmiany nazwy plików w projekcie
 Przed projektu można dodać, zmienić lub usunąć pliku lub katalogu, należy wywołać odpowiednie `IVsTrackProjectDocuments2::OnQuery*` metody, aby uzyskać uprawnienia ze środowiska. Jeśli uprawnienia, a następnie projektu musi ukończyć operacji, a następnie wywołać odpowiednie `IVsTrackProjectDocuments2::OnAfter*` metodę, aby powiadomić środowiska zakończeniu operacji. Projekt musi wywoływać metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejs dla wszystkich plików (na przykład specjalne) i nie tylko pliki nadrzędnej. Wywołania pliku są wymagane, ale wywołania katalogu są opcjonalne. Jeśli projekt zawiera informacje o katalogu, a następnie powinny wywoływać odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody, ale jeśli nie ma tych informacji, a następnie środowiska wywnioskuje informacji katalogowych.

 Projekt nie powinny wywoływać metody `IVsTrackProjectDocuments2` w projekcie otwarcie lub zamknięcie. Odbiorniki, które mają te informacje podczas uruchamiania poczekać na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> zdarzeń i rozwiązania w celu znalezienia informacji muszą wykonać iterację. Podczas zamykania te informacje nie są potrzebne. `IVsTrackProjectDocuments2` podano z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Dla każdego Dodaj, Zmień nazwę i Usuń akcję istnieje `OnQuery*` — metoda i `OnAfter*` metody. Wywołanie `OnQuery*` metody zażądać uprawnień do dodawania, zmienić lub usunąć pliku lub katalogu. Wywołanie `OnAfter*` metody po plik lub katalog został dodany, zmieniono jego nazwę lub usunięty, i nowy stan odzwierciedla stan projektu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)