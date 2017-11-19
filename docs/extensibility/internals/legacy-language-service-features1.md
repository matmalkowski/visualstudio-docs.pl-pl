---
title: "Język starszej wersji usługi Features1 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc29529c7ba499cdc7291078774b9f546a3a08ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-features"></a>Funkcje usługi starszej wersji języka
Usługa języka zarządzanego pakietu framework (MPF) może obsługiwać jeden lub więcej [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcje, takie jak wyróżnianie składni, funkcję IntelliSense i sprawdzanie poprawności punktu przerwania. Każdej funkcji można stosować niezależnie od innych, ale wymaga analizatora składni i skaner z wyjątkiem wyróżnianie składni, które wymaga tylko skanera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Parowanie nawiasów klamrowych w starsza wersja usługi języka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi języka pary dopasowania, znanej także jako parowanie nawiasów klamrowych.  
  
 [Kod komentowania w starsza wersja usługi języka](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi komentowania i usunięcie komentarza zaznaczonego kodu.  
  
 [Niestandardowe właściwości dokumentu w starsza wersja usługi języka](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi właściwości dokumentu, które są osadzone w pliku źródłowym.  
  
 [Konspekt w starsza wersja usługi języka](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane w celu obsługi zwijania poprzez wdrożenie ukryte obszary.  
  
 [Ponowne formatowanie kodu w starsza wersja usługi języka](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi ponownego formatowania kodu.  
  
 [Obsługa wstawki kodu za pośrednictwem usługi języka starsza wersja](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi fragmentów kodu, które segmentów kodu, które są wstawiane i można go edytować.  
  
 [Informacje o parametrach w starsza wersja usługi języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji informacje o parametrach IntelliSense do wyświetlania podpis metody jako metodę został wpisany.  
  
 [Szybkie informacje w starsza wersja usługi języka](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji IntelliSense szybkie informacje do wyświetlania informacji o identyfikatorze.  
  
 [Element członkowski uzupełniania w starsza wersja usługi języka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji zakończenia elementu członkowskiego IntelliSense do wybierania elementu członkowskiego przestrzeni nazw z listy.  
  
 [Zakończenie programu Word w starsza wersja usługi języka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane do obsługi operacji IntelliSense całe słowo częściowo klawiaturowe ukończenia.  
  
 [Obsługa okno zmiennych automatycznych w starsza wersja usługi języka](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 W tym artykule opisano, co można zrobić do obsługi usługi języka **automatycznych** okno podczas debugowania.  
  
 [Obsługa paska nawigacyjnego w usłudze języka starsza wersja](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Informacje dotyczące używania **pasek nawigacyjny** u góry widoku edytora w celu zapewnienia szybkiego nawigacji do dowolnego typu lub elementu członkowskiego w pliku, w tym widoku.  
  
 [Kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 W tym artykule opisano, co jest wymagane w celu obsługi wyróżnianie składni kodu źródłowego.  
  
 [Sprawdzanie poprawności punkty przerwania w starsza wersja usługi języka](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Zawiera opis usługi języka czynności do obsługi sprawdzania poprawności punktów przerwania poza debugera.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Analizatora usługi starszej wersji języka i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Opisuje analizatora i skanera, które są wymagane do wykonania wszystkich funkcji usługi języka, która używa w ramach zarządzanego pakietu.  
  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 W tym artykule opisano, co jest wymagane do wdrożenia usługi języka przy użyciu MPF.  
  
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 W tym artykule opisano kroki, które są wymagane do zarejestrowania usługi języka MPF z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Korzystanie z IntelliSense](../../ide/using-intellisense.md)  
 W tym artykule wyjaśniono, jak IntelliSense ułatwia języka odwołania dostępu.  
  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Zawiera informacje o sposobie używania framework zarządzanego pakietu (MPF) do wdrożenia usługi oferujący wszystkie funkcje języka w kodzie zarządzanym.