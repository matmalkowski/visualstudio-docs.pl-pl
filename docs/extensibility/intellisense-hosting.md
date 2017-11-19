---
title: IntelliSense Hosting | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850e4b2ef6d455bb141827fa125c4c7c6860b652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense-hosting"></a>IntelliSense Hosting
Program Visual Studio pozwala IntelliSense hosting. IntellSense hosting umożliwia podanie IntelliSense do kodu, który nie jest obsługiwany przez Edytor tekstu Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Użycie Hosting IntelliSense  
 W programie Visual Studio kodu, który ma dostęp do zestawu uzupełniania i bufor tekstowy można uzyskać IntelliSense systemu windows z dowolnego miejsca w interfejsie użytkownika (UI). Niektóre przykładowe scenariusze dotyczące to są zakończenia w **czujki** okna lub w polu stanu w oknie Właściwości punktu przerwania.  
  
### <a name="implementation-interfaces"></a>Implementacja interfejsów  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Każdego składnika interfejsu użytkownika, który obsługuje wyskakujące IntelliSense musi obsługiwać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu. Domyślny widok tekstu edytora core obejmuje zasobu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu implementacji, aby zachować bieżącą funkcjonalność IntelliSense. W większości przypadków metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu stanowią podzbiór co to jest wdrażana w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu. Podzbiór obejmuje obsługi interfejsu użytkownika funkcji IntelliSense, karetki i manipulowania wybór i prosty tekst zastępczy funkcji. Ponadto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejs umożliwia oddzielne IntelliSense "temat" i "context", dzięki czemu można podać IntelliSense dla podmiotów, które nie istnieją bezpośrednio w buforze tekst, który jest używany dla kontekstu.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Musi implementować interfejs dostawcy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> obsługuje metodę umożliwiającą włączenie klienta w celu określenia, jakiego rodzaju IntelliSense funkcji hosta.  
  
 Flagi hosta, zdefiniowane w [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), zestawiono poniżej.  
  
|Flaga hosta IntelliSense|Opis|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Ustawienie tej flagi oznacza, że bufor kontekstu jest tylko do odczytu i edycji występuje tylko w obrębie tekst tematu.|  
|IHF_NOSEPERATESUBJECT|Ustawienie tej flagi oznacza brak jest bez oddzielnego tematu IntelliSense. Podmiot istnieje do buforu kontekstu, takie jak w przypadku tradycyjnych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> systemu IntelliSense.|  
|IHF_SINGLELINESUBJECT|Ustawienie tej flagi oznacza, że temat nie jest wiele wierszy funkcją, na przykład w jednym wierszu edytować w **czujki** okna.|  
|IHF_FORCECOMMITTOCONTEXT|Jeśli ta flaga jest ustawiona, muszą zostać zaktualizowane buforu kontekstu hosta umożliwia flagi tylko do odczytu dla buforu kontekstu, które mają być ignorowane i zmiany, aby kontynuować.|  
|IHF_OVERTYPE|Edytowanie (w temacie lub w kontekście) powinno być wykonywane w trybie zastępowania.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit i IVsIntellisenseHost.AfterCompletorCommit  
 Te metody wywołania zwrotnego są wywoływane przez zakończenia okna przed i po tekst dokłada starań, aby włączyć przetwarzanie wstępne i przetwarzania końcowego.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Interfejsu jest wersją wspólnie możliwość utworzenia okna ukończenia standardowego używanym przez zintegrowane środowisko programistyczne (IDE). Wszelkie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interfejsu można szybko wdrożyć IntelliSense przy użyciu tego interfejsu completor.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop>