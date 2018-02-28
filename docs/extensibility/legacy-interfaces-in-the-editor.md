---
title: Interfejsy starszej wersji w edytorze | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a9d09c452fb6d03f7f5072e34813c3757455f96a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfejsy starszej wersji w edytorze
Dostępne edytorze programu Visual Studio z interfejsów starszej wersji. Visual Studio SDK zawiera karty znany jako *podkładek*, umożliwiające te interfejsy do interakcji z nowego edytora. Niemniej jednak zaleca się zaktualizowanie starszej wersji kodu za pomocą edytora nowego interfejsu API. Kod będą działać lepiej i można używać nowych technologii, takich jak Windows Presentation Foundation (WPF) i zarządzane Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Adaptacja starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|Wyjaśniono, jak dostosować swój kod, aby nowy edytor.|  
|[Zachowanie nowe lub zostały zmienione z kartami edytora](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|W tym artykule wyjaśniono, jak zachowania kart Edytor różni się od wcześniejszych wersji edytora.|  
|[W edytorze Core](../extensibility/inside-the-core-editor.md)|W tym artykule opisano różne składniki wcześniejszych wersji edytora.|  
|[Tworzenie wystąpień Edytor Core przy użyciu interfejsu API starsza wersja](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Wyjaśniono, jak utworzyć wystąpienia Edytor core za pomocą starszej wersji interfejsu API.|  
|[Fabryki edytora](../extensibility/editor-factories.md)|Wyjaśniono, jak fabryki edytora za pomocą starszej wersji interfejsu API.|  
|[Porady: Rejestrowanie typów plików edytora](../extensibility/how-to-register-editor-file-types.md)|Wyjaśniono, jak połączyć rozszerzenie nazwy pliku w edytorze.|  
|[Wskazówki: Tworzenie edytora rdzeni i rejestrowania edytora typu pliku](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Wyjaśniono, jak utworzyć podstawowa edytora i połączyć rozszerzenie nazwy pliku.|  
|[Porady: Podaj kontekstu edytorów](../extensibility/how-to-provide-context-for-editors.md)|Wyjaśniono, jak zapewnienie kontekst tego edytora.|  
|[Usługi językowe i Edytor Core](../extensibility/language-services-and-the-core-editor.md)|Opisano interakcje między usługą języka i edytora.|  
|[Dostęp do buforu tekstu przy użyciu interfejsu API starsza wersja](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Wyjaśniono, jak dostęp do buforu tekstu przy użyciu starszej wersji interfejsu API.|  
|[Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starsza wersja](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Wyjaśniono, jak dostęp do widoku tekstu przy użyciu starszej wersji interfejsu API.|  
|[Dostosowywanie kodu systemu Windows przy użyciu interfejsu API starsza wersja](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Opis sposobu dostosowywania kodu systemu windows przy użyciu starszej wersji interfejsu API.|  
|[Uzyskiwanie dostępu do warstwy tekstu przy użyciu interfejsu API starsza wersja](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Wyjaśniono, jak dostęp do różnych warstw tekstu przy użyciu starszej wersji interfejsu API.|  
|[Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)|Wyjaśniono, jak dodać znacznikach tekstu przy użyciu starszej wersji interfejsu API.|  
|[Dostosowywanie menu i formanty edytora przy użyciu interfejsu API starsza wersja](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Opis sposobu dostosowywania formanty edytora przy użyciu starszej wersji interfejsu API.|  
|[Zarządzanie Cofnij i ponów przy użyciu interfejsu API starsza wersja](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Wyjaśniono, jak zarządzać cofania i ponawiania przy użyciu starszej wersji interfejsu API.|  
|[Porady: Implementowanie Znajdź i Zastąp mechanizmu](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Wyjaśniono, jak zarządzać Znajdź i Zamień przy użyciu starszej wersji interfejsu API.|  
|[Porady: pomijanie powiadomienia o zmianie pliku](../extensibility/how-to-suppress-file-change-notifications.md)|Wyjaśniono, jak wyłączyć powiadomienia o zmianie pliku przy użyciu starszej wersji interfejsu API.|  
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Wyjaśnia sposób tworzenia niestandardowych edytorów i projektantów.|  
|[Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)|Zawiera linki do dokumentów dotyczących funkcji zapewniających możliwości dostosowywania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor core przez dodanie obsługi usługi języka.|  
|[Używanie czcionek i kolorów](../extensibility/using-fonts-and-colors.md)|Wyjaśniono, jak czcionki i kolory za pomocą starszej wersji interfejsów.|