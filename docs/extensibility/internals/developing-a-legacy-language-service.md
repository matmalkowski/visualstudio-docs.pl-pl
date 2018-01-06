---
title: "Tworzenie usługi języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords: language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b7a88c00e980cb86764958886d737d5113dfe1fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="developing-a-legacy-language-service"></a>Tworzenie usługi języka starsza wersja
Ta sekcja łącza do tematów, które ułatwiają tworzenie usługi starszej wersji języka.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej o nowy sposób wdrożenia usługi języka, zobacz [edytora i rozszerzenia usługi języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model starszej wersji usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Udostępnia model usługi minimalnego języka dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] core edytora. Ten model jako przewodnik służy do tworzenia usługi języka.  
  
 [Interfejsy starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-interfaces.md)  
 W tym artykule omówiono obiekty wymagane do wdrożenia usługi języka i zawiera listę dodatkowych obiektów, które służy do zapewnienia wyróżnianie składni, Metoda danych i inne funkcje.  
  
 [Przechwytywanie poleceń starszej wersji usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Opisuje sposób wstawiania filtr polecenia do usługi języka do przechwycenia poleceń, które w przeciwnym razie będzie obsługiwać widoku tekstu.  
  
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Zawiera informacje o tym, jak zarejestrować usługi języka przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md)  
 W tym artykule opisano, jak usługa języka zapewniają funkcje do obsługi debugera.  
  
 [Lista kontrolna: tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Instrukcje krok po kroku dotyczące tworzenia i Integrowanie usługi języka edytora core.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 W tym artykule omówiono implementowania wyróżnianie składni w usłudze języka.  
  
 [Uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 W tym artykule omówiono uzupełniania instrukcji, proces, za pomocą którego usługa języka umożliwia użytkownikom Zakończ element, który zostały uruchomione, wpisując lub słowo kluczowe języka.  
  
 [Informacje o parametrach w starsza wersja usługi języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Opisuje sposób zapewnienia porady metody przeciążonej funkcji i metod.  
  
 [Instrukcje: zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Objaśnienie jego przeznaczenia obszaru tekstu ukrytego i zawiera instrukcje dotyczące sposobu wdrażania region tekstu ukrytego.  
  
 [Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Opisano dwie opcje rozszerzających zwijania obsługę języka poza obsługi *Zwiń definicji* polecenia.