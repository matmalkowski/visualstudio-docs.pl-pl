---
title: "Architektura wtyczek do kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 22929c34d656fb4f163076ca0b5dfb498d44c884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-architecture"></a>Architektura wtyczkę kontroli źródła
Można dodać obsługę kontroli źródła do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) przez implementację i dołączanie wtyczka do kontroli źródła. IDE nawiązuje połączenie z kontrolą źródła wtyczki za pomocą dobrze zdefiniowany interfejsu API dodatku typu Plug-In kontroli źródła. IDE przedstawia funkcje kontroli wersji z systemu kontroli źródła, zapewniając interfejsu użytkownika (UI), która składa się z pasków narzędzi i poleceń menu. Wtyczka do kontroli źródła implementuje funkcje kontroli źródła.  
  
## <a name="source-control-plug-in-resources"></a>Zasoby wtyczkę kontroli źródła  
 Plug-in kontroli źródła zawiera zasoby, aby utworzyć i połączyć aplikację z wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Dodatek kontroli źródła zawiera specyfikację interfejsu API, która musi być implementowana przez wtyczki kontroli źródła, dzięki czemu mogą zostać włączone do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Zawiera ona także (napisana w języku C++) przykładowy kod implementujący szkielet źródła formantu wtyczki ilustrujące implementacji podstawowych funkcji zgodnych z interfejsem API dodatku typu Plug-in kontroli źródła.  
  
 Specyfikacja interfejsu API dodatku typu Plug-in kontroli źródła pozwala korzystać z systemu kontroli źródła, wszystkie wybrane po utworzeniu kontroli źródła biblioteki DLL z wymagany zestaw funkcji wdrożone zgodnie z interfejsu API dodatku typu Plug-in kontroli źródła.  
  
## <a name="components"></a>Składniki  
 Pakiet karty kontroli źródła na diagramie jest składnik IDE, który tłumaczy żądanie użytkownika dla operacji kontroli źródła w wywołaniu funkcji obsługiwanych przez wtyczkę kontroli źródła. W tym celu IDE i wtyczkę kontroli źródła muszą mieć efektywny okna dialogowego przekazujący dane i z powrotem między IDE i wtyczki. Dla tego okna dialogowego została wykonana mogą używać tego samego języka. API dodatku Plug-in kontroli źródła, opisane w tej dokumentacji jest wspólnego słownika dla tego programu exchange.  
  
 ![Diagram architektury kontroli kodu źródłowego](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
Diagram architektury przedstawiający interakcji między VS i kontroli źródła wtyczek  
  
 Jak pokazano na diagramie architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki oznakowane jako powłoki programu VS na diagramie obsługuje skojarzone składniki, takie jak edytory i Eksploratora rozwiązań i projekty robocze użytkownika. Pakiet karty kontroli źródła obsługuje interakcję między IDE i wtyczkę kontroli źródła. Pakiet karty kontroli źródła udostępnia własnego interfejsu użytkownika kontroli źródła. Jest najwyższego poziomu interfejsu użytkownika, który użytkownik użyje w celu inicjowania i zdefiniuj zakres operacja kontroli źródła.  
  
 Wtyczka do kontroli źródła może mieć własny interfejs użytkownika może składać się z dwóch części, jak pokazano na rysunku. Pole o nazwie "Dostawca UI" reprezentuje elementy interfejsu użytkownika niestandardowego, twórca wtyczkę kontroli źródła, udostępnić. Te są wyświetlane bezpośrednio przez wtyczkę kontroli źródła, gdy użytkownik wywołuje operację kontroli źródła zaawansowane. Pole o nazwie "Pomocnika UI" to zestaw źródła formantu interfejsu użytkownika funkcje wtyczek wywoływane pośrednio przez IDE. Wtyczka do kontroli źródła przekazuje komunikatów interfejsu użytkownika IDE przez funkcje specjalne wywołania podano IDE. Pomocnik interfejsu użytkownika umożliwia bardziej bezproblemową integrację z IDE (często z **zaawansowane** przycisku) i w związku z tym zapewnia bardziej ujednolicone środowisko użytkownika końcowego.  
  
 Wtyczka do kontroli źródła nie można wprowadzić zmian do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki, a w rezultacie pakiet karty kontroli źródła lub źródło kontroli podał IDE interfejsu użytkownika. Należy go maksymalne wykorzystanie możliwości oferowane przez wdrożenie różnych funkcji API dodatku typu Plug-in kontroli źródła, składających się na zintegrowane środowisko użytkownika końcowego. Sekcja odwołania dokumentacji interfejsu API dodatku typu Plug-in kontroli źródła zawiera informacje o niektórych możliwości wtyczkę kontroli źródła zaawansowane. Aby wykorzystać te funkcje, wtyczkę kontroli źródła musi deklarowanie zaawansowane możliwości do środowiska IDE programu podczas inicjowania i musi on implementować określone funkcje zaawansowane, dla każdej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Plug-in kontroli źródła](../../extensibility/source-control-plug-ins.md)   
 [Słownik](../../extensibility/source-control-plug-in-glossary.md)   
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)