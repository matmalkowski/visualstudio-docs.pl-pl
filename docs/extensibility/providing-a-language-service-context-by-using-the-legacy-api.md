---
title: Udostępnia kontekst usługi języka przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3556fcce3d14d5069854c64d81cb780123a979d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140075"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Udostępnia kontekst usługi języka przy użyciu interfejsu API starsza wersja
Dostępne są dwie opcje usługi języka zapewnić przy użyciu kontekstu użytkownika [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor rdzeni: dostarczy w kontekście znacznika tekstu, lub wszystkich kontekstu użytkownika. Różnice między nimi są opisane w tym miejscu.  
  
 Aby uzyskać więcej informacji dotyczących zapewniania kontekstu do usługi języka, która jest połączona z własnego edytora, zobacz [porady: Podaj kontekst dla edytory](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Podaj w kontekście znacznika tekstu do edytora  
 Zapewnienie błędy kompilatora wskazywanym przez znacznikach tekstu w kontekście [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podstawowe edytora, implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejsu. W tym scenariuszu Usługa języka udostępnia kontekst tylko wtedy, gdy kursor znajduje się na znacznika tekstu. Dzięki temu edytora w celu zapewnienia — słowo kluczowe wskazywanej przez kursor do **Pomoc dynamiczna** okna bez atrybutów.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Podaj wszystkie kontekstu użytkownika do edytora  
 Jeśli tworzysz usługi języka i korzystają z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podstawowe edytor, a następnie można wdrożyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfejsu zapewnienie kontekstu usługi języka.  
  
 Do wykonania `IVsLanguageContextProvider`, zbiór kontekstu (kolekcja) jest dołączony do edytora, który jest odpowiedzialny za aktualizację zbiorze kontekstu. Gdy **Pomoc dynamiczna** wywołań okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfejs tego zbioru kontekstu w czasie bezczynności zbiorze kontekst zapytania edytor dla aktualizacji. Edytor następnie powiadamia usługi języka, że należy zaktualizować edytora i przekazuje wskaźnik do zbioru kontekstu. Jest to realizowane przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> metody z edytora do usługi języka. Za pomocą wskaźnika zbiorze kontekstu, usługi języka można teraz dodawać i usuwać atrybuty i słów kluczowych. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Istnieją dwa różne sposoby, aby zaimplementować `IVsLanguageContextProvider`:  
  
-   Podaj słowa kluczowego zbiorze kontekstu  
  
     Edytor wywołanego zaktualizować zbiorze kontekstu podaj odpowiednie słów kluczowych i atrybutów, a następnie wróć `S_OK`. Zwrócona wartość powoduje, że edytor, aby zachować kontekst — słowo kluczowe i atrybutów, a nie zapewniają słowa kluczowego wskazywanej przez kursor do zbioru kontekstu.  
  
-   Uzyskaj słowo kluczowe z — słowo kluczowe pod kursorem  
  
     Edytor wywołanego zaktualizować zbiorze kontekstu podaj odpowiednie atrybuty, a następnie wróć `E_FAIL`. Zwrócona wartość powoduje, że edytor zachować z atrybutów w zbiorze kontekstu, ale zaktualizuj pakiet kontekstu ze słowem kluczowym wskazywanej przez kursor.  
  
 Poniższy diagram przedstawia sposób kontekstu jest dostępne w celu usługi języka, który implementuje `IVsLanguageContextProvider`.  
  
 ![LangServiceImplementation2 — grafika](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Kontekst dla usługi języka  
  
 Jak widać na diagramie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora tekstów core ma zbiór kontekstu do niego dołączony. Ten zbiór kontekstu wskazuje trzech oddzielnych kontekst podrzędny torebki: Usługa języka domyślnego edytora i znacznika tekstu. Język usługi i tekstu znacznika kontekst podrzędny torebki zawierać atrybuty i słów kluczowych języka usługi, jeśli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfejs jest wdrażany, znaczniki tekstu i jeśli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejs jest wdrażany. Jeśli nie implementuje jednej z tych interfejsów, następnie Edytor zawierają kontekst dotyczący — słowo kluczowe wskazywanej przez kursor w zbiorze domyślny edytor kontekst podrzędny.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Kontekst wytyczne dotyczące edytory oraz projektantów  
 Projektanci i edytory podać ogólne — słowo kluczowe dla edytora lub okna projektanta. Można to zrobić, aby tematu pomocy rodzajowy, lecz właściwe, zostaną wyświetlone dla projektancie lub edytorze, gdy użytkownik naciśnie klawisz F1. Edytor musi oprócz tego, podaj bieżącego słowa kluczowego wskazywanej przez kursor lub Zapewnij termin klucza na podstawie bieżącego zaznaczenia. Pozwala to zapewnić, że tematu pomocy dla tekstu lub elementu interfejsu użytkownika wskazywał Wyświetla wybrany, gdy użytkownik naciśnie klawisz F1. Projektant dostarcza kontekst dla elementu wybranego w projektancie, takie jak przycisk w formularzu. Projektanci i edytory również musi połączyć się z usługą języka w sposób opisany w [starsza wersja języka usługi Essentials](../extensibility/internals/legacy-language-service-essentials.md).