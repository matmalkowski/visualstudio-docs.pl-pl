---
title: Wzorce interakcji dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="interaction-patterns-for-visual-studio"></a>Wzorce interakcji dla programu Visual Studio
## <a name="overview"></a>Omówienie  
 Wzorzec projektowania, ogólnie rzecz biorąc, stanowi podstawę projektu, który można zastosować w następujących sytuacjach do rozwiązywania problemów z podobne zestawy warunków ograniczających. Funkcja i system projektanci używali tych wzorców projektowych z rozpoczynaniem punktów, które następnie mogą być dostosowywane do ich konkretnej sytuacji.  
  
 Visual Studio ma biblioteki typowe wzorce interakcji, które należy wziąć pod uwagę podczas tworzenia nowych funkcji. Istnieją dwa podstawowe kontekstów dla naszych wzorce projektowe: klienta programu Visual Studio (devenv) i Visual Studio Online. Dla niektórych problemów projektu istnieje powszechny wzorzec, który działa dobrze w sytuacji wszystkie. W wielu przypadkach jednak rozwiązanie mogą się różnić dla interfejsu użytkownika, który zobaczy w obrębie przeglądarki i który znajduje się w aplikacji klienta.  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio klienta wzorca typów  
  
|Typ wzorca|Opis|Przykłady|  
|------------------|-----------------|--------------|  
|**Wzorce na poziomie aplikacji**|Wzorce wysokiego poziomu wspólne dla aplikacji, określania lub wyświetlanie kontekst aplikacji i zawierający wzorce złożone i kontroli w nich|— Windows narzędzie<br />-Okna dokumentów|  
|**Wzorce złożone**|Wspólne wzorce, które mogą obejmować między wzorce aplikacji lub rozpoznanym szablon składa się z kilku formantów w różnych konfiguracji|— Przełączanie Widok<br />— Konstruktorzy listy<br />-Wyświetlanie danych<br />-Powiadomienia<br />-Weryfikacji<br />— Modele wybór|  
|**Wzorce formantu**|Szczegółowe informacje o formantach jak niskiego poziomu ma zachowywać się|-Widok drzewa<br />-Edycji w formancie siatki|  
  
## <a name="application-patterns"></a>Wzorce aplikacji  
 Na wysokim poziomie interfejsu programu Visual Studio obejmuje wiele systemu windows, okna dialogowe poleceń i paski narzędzi w obrębie jednego IDE. Hierarchia programu Visual Studio Określa menu kontekstowe i dysków. Punkty integracji klucza w interfejsie użytkownika IDE są okna dokumentów, okien narzędzi, projekty, strukturę polecenia, Edytor tekstu, przybornika, okno właściwości i narzędzia > Opcje.  
  
 Istnieją wzorców użycia podstawowe dla każdego z punktów integracji klucza w interfejsie użytkownika IDE:  
  
-   [Menu i poleceń programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interakcje okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Okna narzędzi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Konwencje dokumentów edytora](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Wspólne wzorce formantu  
 Wzorce kontrolki są głównie informacje o poszczególnych kontrolkach ma zachowywać się. Jest to jeden obszar, w którym jest najważniejszych spójności.  
  
 Najbardziej typowych formantów w programie Visual Studio powinien postępuj zgodnie z wytycznymi pulpitu systemu Windows. Nasze wskazówki obejmują tylko obszary, w których należy rozszerzyć typowych konwersji z programu Visual Studio specyficzne dla interakcji lub miejsc, w których firma Microsoft zastępują wytyczne wyłącznie w celu dostosowania programu Visual Studio do potrzeb użytkowników zaawansowanych.  
  
-   [Wspólne wzorce formantu dla programu Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Formanty standardowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Kontrolki tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Przyciski i hiperłącza](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Wzorce złożone  
 Istnieją różne sposoby, które użytkownicy będą wykonywać zadania. Tam gdzie to możliwe, funkcje należy tak zaprojektować do używania tych wzorców interakcji i projekt visual.  
  
 Gdy istnieje wiele wzorce złożone w programie Visual Studio, niektóre z najważniejszych w odniesieniu do spójności są:  
  
-   [Wzorce złożone dla programu Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Interfejs użytkownika i wgląd w obiekcie](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Wybór modeli](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Trwałość i zapisywania ustawień](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Wprowadzania dotykowego](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)