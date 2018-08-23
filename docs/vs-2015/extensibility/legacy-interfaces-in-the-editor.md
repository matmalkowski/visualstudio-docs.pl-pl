---
title: Interfejsy starszej wersji w edytorze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ae8f087a9f52ca2eff130b7972c2cd9d68a139f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682969"
---
# <a name="legacy-interfaces-in-the-editor"></a>Interfejsy starszej wersji w edytorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [interfejsy starszej wersji w edytorze](https://docs.microsoft.com/visualstudio/extensibility/legacy-interfaces-in-the-editor).  
  
Edytor programu Visual Studio dostęp ze starszych interfejsów. Visual Studio SDK zawiera kart znanych jako *podkładki*, umożliwiają one te interfejsy do interakcji z nowego edytora. Niemniej jednak zaleca się zaktualizowanie starszej wersji kodu, aby użyć nowego edytora interfejsu API. Twój kod będzie działać lepiej i można użyć nowych technologii, takich jak Windows Presentation Foundation (WPF) i Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Dostosowanie kodem Legacy do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|Wyjaśnia, jak dostosować swój kod, aby nowego edytora.|  
|[Zachowaniem nowe lub zostały zmienione z kartami edytora](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|W tym artykule wyjaśniono, jak zachowanie kart edytora różni się od wcześniejszych wersjach edytora.|  
|[W edytorze podstawowych](../extensibility/inside-the-core-editor.md)|W tym artykule opisano różne składniki wcześniejszych wersjach edytora.|  
|[Utworzenie wystąpienia podstawowy edytor za pomocą starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Wyjaśnia, jak utworzyć podstawowy edytor za pomocą starszej wersji interfejsu API.|  
|[Fabryki edytora](../extensibility/editor-factories.md)|Wyjaśnia, jak fabryki edytora za pomocą starszej wersji interfejsu API.|  
|[Porady: rejestrowanie Edytor typów plików](../extensibility/how-to-register-editor-file-types.md)|Wyjaśnia, jak połączyć z rozszerzeniem nazwy pliku do edytora.|  
|[Wskazówki: Tworzenie edytora podstawowych i rejestrowania typu pliku w edytorze](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Wyjaśnia sposób tworzenia podstawowej edytora i połączyć rozszerzenie nazwy pliku.|  
|[Porady: dostarczanie kontekstu edytorów](../extensibility/how-to-provide-context-for-editors.md)|Wyjaśnia, jak zapewnić kontekst tego edytora.|  
|[Usługi języka oraz podstawowy edytor](../extensibility/language-services-and-the-core-editor.md)|W tym artykule wyjaśniono, interakcji między usługi językowej i edytora.|  
|[Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Wyjaśnia, jak dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API.|  
|[Dostęp do theText widoku przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Wyjaśnia, jak dostęp do widoku tekstu przy użyciu starszej wersji interfejsu API.|  
|[Dostosowywanie kodu Windows za pomocą starszej wersji interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Opis sposobu dostosowywania kodu systemu windows przy użyciu starszej wersji interfejsu API.|  
|[Uzyskiwanie dostępu do warstwy tekstu za pomocą starszej wersji interfejsu API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Wyjaśnia, jak dostęp do różnych warstw tekstu przy użyciu starszej wersji interfejsu API.|  
|[Znaczniki tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md)|Wyjaśnia, jak dodać znaczniki tekstu przy użyciu starszej wersji interfejsu API.|  
|[Dostosowywanie menu i formantów w edytorze za pomocą starszej wersji interfejsu API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Wyjaśnia, jak dostosować formanty edytora przy użyciu starszej wersji interfejsu API.|  
|[Zarządzanie Cofnij i ponów przy użyciu starszej wersji interfejsu API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Wyjaśnia, jak zarządzać Cofnij i wykonaj ponownie przy użyciu starszej wersji interfejsu API.|  
|[Porady: Implementowanie Znajdź i Zamień mechanizm](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Wyjaśnia, jak zarządzać Znajdź i Zamień przy użyciu starszej wersji interfejsu API.|  
|[Porady: pomijanie powiadomienia o zmianie pliku](../extensibility/how-to-suppress-file-change-notifications.md)|Wyjaśnia, jak wyłączyć powiadomienia o zmianie pliku przy użyciu starszej wersji interfejsu API.|  
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Wyjaśnia sposób tworzenia niestandardowych edytorów i projektantów.|  
|[Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)|Zawiera łącza do dokumentów o funkcjach, które zapewniają możliwość dostosowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorze podstawowych funkcji przez dodanie obsługi dla usługi w języka.|  
|[Używanie czcionek i kolorów](../extensibility/using-fonts-and-colors.md)|Opis sposobu użycia czcionki i kolory z interfejsami starszej wersji.|

