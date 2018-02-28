---
title: "Omówienie usługi starszej wersji języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 05805e5cf4b21f4c7d233cab7dd8421ee76f626f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-overview"></a>Omówienie usługi starszej wersji języka
Usługa języka zapewnia obsługę edytora, który umożliwia wdrożenie niektórych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funkcji. Klasy usługi języka zarządzane pakietu Framework (MPF) zapewniają pełną obsługę często używane funkcje i częściowe obsługę innych funkcji.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Pełni obsługiwane funkcje w MPF  
 Klasy usługi języka MPF obsługuje następujące funkcje:  
  
-   wyróżnianie składni  
  
-   Tworzenie konspektu  
  
-   Dodawanie komentarza do bloków kodu  
  
-   Parowanie nawiasów klamrowych  
  
-   Wstawki kodu  
  
-   Niestandardowe właściwości dokumentu  
  
-   Informacje o parametrach IntelliSense  
  
-   Informacje o szybkie IntelliSense  
  
-   IntelliSense zakończenia elementu członkowskiego  
  
-   Uzupełnianie word IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Częściowo obsługiwane funkcje w MPF  
 MPF zapewnia tylko częściowe obsługę następujących funkcji. Oznacza to, że musi implementować metody, które są wywoływane przez MPF.  
  
-   Ponowne formatowanie kodu. Należy podać kod, który implementuje ponownego formatowania.  
  
-   Sprawdzanie poprawności punktów przerwania, określając prawidłowy kod zakresów. Należy podać kod, który identyfikuje fragmentu kodu.  
  
-   Obsługa debugera **automatycznych** okna wyświetlania zmiennych. Należy podać kod, który określa, jakie do wyświetlenia w oknie.  
  
-   Obsługa **pasek nawigacyjny** Szybkie nawigowanie między typy i składniki. Wdrożenie i zwrócić klasę pomocy, które wypełnia list w **pasek nawigacyjny** pola kombi.  
  
## <a name="implementation"></a>Implementacja  
 Należy wykonać kilka czynności implementowania samej usługi języka oraz funkcji usługi języka, które mają być obsługiwane dla danego języka. Te kroki opisano w następujących tematach:  
  
-   [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Zwijanie w starszej wersji usługi językowej](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Komentowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Ponowne formatowanie kodu w starszej wersji usługi językowej](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Niestandardowe właściwości dokumentu w starszej wersji usługi językowej](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Obsługa fragmentów kodu w starszej wersji usługi językowej](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Uzupełnianie wyrazów w starszej wersji usługi językowej](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Uzupełnianie składowych w starszej wersji usługi językowej](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informacje o parametrach w starsza wersja usługi języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Szybkie informacje w starszej wersji usługi językowej](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Obsługa okna zmiennych automatycznych w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)