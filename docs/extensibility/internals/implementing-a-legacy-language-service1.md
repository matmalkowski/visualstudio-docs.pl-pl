---
title: "Implementowanie Service1 języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18ff0fef277967dcb446f62120843f476ddb4a3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-legacy-language-service"></a>Wdrażanie usługi języka starsza wersja
Można klas w ramach zarządzanego pakietu (MPF) implementację usługi języka starszej wersji, która obsługuje wiele funkcji, takich jak wyróżnianie składni, pasujących nawiasów klamrowych i uzupełniania IntelliSense.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej o nowy sposób wdrożenia usługi języka, zobacz [edytora i rozszerzenia usługi języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-overview.md)  
 Przegląd funkcji usługi języka, które są obsługiwane w MPF.  
  
 [Wdrażanie usługi języka starsza wersja](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 W tym artykule opisano, co jest wymagane do wdrożenia usługi języka przy użyciu MPF.  
  
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 W tym artykule opisano kroki, które są wymagane do zarejestrowania usługi języka MPF z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Analizatora usługi starszej wersji języka i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 W tym artykule opisano dwa analizatory składni, które są wymagane do wdrożenia przy użyciu MPF wszystkich funkcji usługi języka.  
  
 [Wskazówki: Tworzenie usługi języka starsza wersja](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Zawiera podstawowe kroki, które są wymagane do wdrożenia usługi języka MPF w pakiet VSPackage.  
  
 [Wskazówki: Pobieranie listy fragmentów kodu zainstalowanych (wykonanie starsza wersja)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Prezentuje techniki pobierania listy fragmentów kodu zainstalowane.  
  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)  
 Zawiera łącza do tematów w tym szczegółów, co należy wykonać w celu wdrożenia wszystkich funkcji usługi języka przy użyciu MPF.