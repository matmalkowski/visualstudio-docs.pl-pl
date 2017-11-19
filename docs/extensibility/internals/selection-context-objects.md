---
title: "Wybór obiektów kontekstu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe4921e48c978b1073c985d4c11f11a14f3b351c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="selection-context-objects"></a>Wybór obiektów kontekstu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) używa obiekt kontekstu globalnego wyboru w celu określenia, co powinno być wyświetlane w IDE. Każde okno w IDE może mieć własną obiekt kontekstu wyboru do kontekst zaznaczenia globalnych. IDE aktualizuje kontekst zaznaczenia globalnych z wartościami z okna, gdy okno ma fokus. Aby uzyskać więcej informacji, zobacz [opinii użytkownikowi](../../extensibility/internals/feedback-to-the-user.md).  
  
 Każdy ramki okna lub lokacji w środowisku IDE ma usługi o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Należy wywołać obiekt utworzony przez VSPackage, który jest zlokalizowany w ramki okna `QueryService` metodę, aby otrzymywać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu.  
  
 Okna ramowe można zachować części ich informacje o kontekście wybór z rozpropagowana na kontekst zaznaczenia globalnych, gdy zostaną uruchomione. Ta możliwość jest przydatna do okna narzędzi, które mogą mieć zaczynać się zaznaczenie jest puste.  
  
 Modyfikowanie wyzwala zdarzenia kontekst zaznaczenia globalne monitorujących VSPackages. VSPackages można wykonywać następujące zadania zaimplementowanie `IVsTrackSelectionEx` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfejsów:  
  
-   Zaktualizuj plik aktualnie aktywne w hierarchii.  
  
-   Monitorowanie zmian w niektórych typów elementów. Na przykład, jeśli VSPackage używa specjalnego **właściwości** okna, należy monitorować zmiany aktywności **właściwości** okna i uruchom ponownie, gdy jest to wymagane do Ciebie.  
  
 Poniższa sekwencja zawiera typowe kursu zaznaczenia śledzenia.  
  
1.  IDE pobiera kontekst zaznaczenia z nowo otwartym oknie i umieszczenie go w kontekście globalne zaznaczenia. Jeśli kontekst zaznaczenia używa HIERARCHY_DONTPROPAGATE lub SELCONTAINER_DONTPROPAGATE, te informacje nie są propagowane do globalnego kontekstu. Aby uzyskać więcej informacji, zobacz [opinii użytkownikowi](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Zdarzenia powiadomień emitowanych do dowolnego pakiet VSPackage, który je żądanie.  
  
3.  Pakiet VSPackage działa na zdarzenia, które otrzymuje, wykonując działania, takie jak aktualizowanie hierarchii, ponowne uaktywnianie narzędzia lub inne podobne zadania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Wybór i waluty w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Typy projektów](../../extensibility/internals/project-types.md)