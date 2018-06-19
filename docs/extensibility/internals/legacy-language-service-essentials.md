---
title: Podstawowe informacje dotyczące języka starszej wersji usługi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68b92b821ad77b050ad2116da6fd930b975dad5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135448"
---
# <a name="legacy-language-service-essentials"></a>Podstawowe informacje dotyczące języka starszej wersji usługi
Należy podać usługi języka Aby zintegrować język programowania Visual Studio. W tym temacie opisano funkcje dostępne w usługach starszej wersji języka.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej o nowy sposób wdrożenia usługi języka, zobacz [edytora i rozszerzenia usługi języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
 Usługi w starszej wersji języka zapewniają następujące funkcje:  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Kolorowanie składni|Powoduje, że widoku edytora wyświetlić różne kolory i styl czcionki dla różnych elementów języka. To zróżnicowanie może ułatwić odczyt i Edycja plików.<br /><br /> Aby uzyskać ogólne informacje, zobacz [kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informacje o tej funkcji w ramach zarządzanego pakietu (MPF), zobacz [kolorowanie składni w starsza wersja usługi języka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Uzupełnianie składni|Wykonuje instrukcję lub użytkownik rozpoczął, wpisując słowo kluczowe. Uzupełnianie ułatwia użytkownikom łatwiej, wprowadź trudne instrukcji z mniej pisania i mniej prawdopodobieństwo błędu.<br /><br /> Aby uzyskać ogólne informacje, zobacz [uzupełniania w starsza wersja usługi języka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Uzyskać informacji dotyczących tej funkcji w MPF, zobacz [zakończenia programu Word w starsza wersja usługi języka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Parowanie nawiasów klamrowych|Najważniejsze funkcje łączyć znaki, takie jak nawiasów klamrowych. Gdy użytkownik wpisze znak zamykającego takich jak "}", pasujących nawiasów klamrowych wyróżnia odpowiadającego otwierania znaków, takich jak "{". Jeśli istnieje kilka poziomów otaczającej znaków, ta funkcja pomaga użytkowników upewnij się, że otaczającego znaki są poprawnie połączone w pary.<br /><br /> Uzyskać informacji dotyczących tej funkcji w MPF, zobacz [dopasowywanie nawias klamrowy w starsza wersja usługi języka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Etykietki narzędzi informacji parametru|Wyświetla listę możliwych podpisów dla przeciążonej metody, które użytkownik jest obecnie wpisywania.<br /><br /> Aby uzyskać ogólne informacje, zobacz [informacje o parametrach w starsza wersja usługi języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Uzyskać informacji dotyczących tej funkcji w MPF, zobacz [informacje o parametrach w starsza wersja usługi języka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Znaczniki błędów|Wyświetla faliste podkreślenie czerwony, znanej także jako dowolnym kształcie, w obszarze tekst, który ma niepoprawną składnię. Znaczniki błędów zwykle są używane do uświadomić użytkowników błędnie wpisane słowa kluczowe, niezamknięty nawias nieprawidłowe znaki i podobne błędy.<br /><br /> W klasach MPF błąd znaczniki są obsługiwane automatycznie w <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metody <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy.|  
  
 Wiele z tych funkcji wymaga usługi języka aby przeanalizować kod źródłowy. Często można wykorzystać tokenizację i analizowania kod dla kompilatora lub interpreter.  
  
 Następujące funkcje są powiązane z obsługę języków programowania, ale nie są częścią usługi języka:  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Ewaluatory wyrażeń|Obsługuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debuger przez sprawdzanie poprawności punktów przerwania i dostarczenie wyrażeń na liście mają być wyświetlane w **automatycznych** okna debugowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [języka usługi obsługę debugowania](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Narzędzia do przeglądania symbol|Obsługuje **przeglądarka obiektów**, **widok klasy**, **wywołania przeglądarki**, i **wyniki Znajdź Symbol**.|