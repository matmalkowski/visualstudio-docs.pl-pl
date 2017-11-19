---
title: "Współtworzenie Model automatyzacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5907f540e5f81e26b7d184352e3c38531ec5da66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="contributing-to-the-automation-model"></a>Współtworzenie Model automatyzacji
Program Visual Studio oferuje zestaw interfejsów automatyzacji dostosowywania środowiska. Model automatyzacji jest model obiektów, która umożliwia użytkownikom końcowym tworzenie Visual Studio — dodatki i rozszerzenia.  
  
 Ponadto jest odpowiednie dla Ciebie, deweloper pakiet VSPackage przyczynić się do modelu automatyzacji; w ten sposób umożliwić użytkownicy końcowi VSPackage Tworzenie dodatków i zazwyczaj zapewnić spójne środowisko modelu przy korzystaniu z VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Aby zapewnić spójne środowisko użytkownika końcowego, można wykonać zestawu wytycznych podczas projektowania VSPackage, dzięki czemu model automatyzacji dla VSPackage następuje pomysły w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)  
 Definiuje model automatyzacji jako powiązane grupy obiektów, które kontrolować najważniejszych aspektów wspólnego środowiska. Ten zestaw obiektów przedstawionej na diagramie model automatyzacji.  
  
 [Zapewnianie automatyzacji do VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 W tym artykule omówiono dwa sposoby zapewnienia automatyzacji dla VSPackage.  
  
 [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)  
 Instrukcje krok po kroku do tworzenia obiektów specyficzne dla pakiet VSPackage.  
  
 [Projekt modelowania](../../extensibility/internals/project-modeling.md)  
 Wyjaśnia obiektów standardowe projektu, które są wymagane do utworzenia nowego typu projektu usługi Automatyzacja i przedstawia ścieżkę, którą następuje automatyzacji projektu. Ten temat zawiera również listy deklaracji i implementację klasy.  
  
 [Udostępnianie zdarzenia](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Instrukcje krok po kroku do tworzenia zdarzeń związanych z modelem automatyzacji.  
  
 [Obsługa automatyzacji dla strony opcji](../../extensibility/internals/automation-support-for-options-pages.md)  
 Opisuje sposób zwracać obiekt automatyzacji podczas niestandardowe Obsługa właściwości pakiet VSPackage **opcje** okno dialogowe na **narzędzie** menu rozszerzając `DTE.Properties` obiektu.  
  
 [Zapewnianie automatyzacji dla kodu](../../extensibility/internals/providing-automation-for-code.md)  
 Wyjaśniono, że tworzenie automatyzacji modelu kodu nie jest wymagane. Jednak w tym temacie, która zawiera informacje interesującego do modele kodu zostanie podane łącze.  
  
 [Porady: Podaj automatyzacji dla systemu Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Wyjaśniono, że dostarczanie automatyzacji jest dobrym rozwiązaniem, za każdym razem chcesz udostępnić obiekty automatyzacji w oknie i środowisko nie ma już obiekt automatyzacji gotowe do użycia. W tym artykule omówiono automatyzacji dla narzędzi systemu windows i windows dokumentu.  
  
 [Przy użyciu modelu automatyzacji](../../extensibility/internals/using-the-automation-model.md)  
 Udostępnia dwa przykłady kodu, które pokazują, jak konsumenta automatyzacji uzyskuje projektu początkowe obiekty automatyzacji.  
  
 [Automatyzacja konfiguracji i obiekty SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Zawiera informacje dotyczące automatyzacji dla opcji konfiguracji i automatyzacji dla wybrane elementy.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Zawiera przykładowy kod, który pokazuje, jak pakiet VSPackage uczestniczy w modelu obiektu automatyzacji DTE. Wyświetla listę parametrów zwracanych wartości i wybrane uwagi.  
  
## <a name="related-sections"></a>Sekcje pokrewne