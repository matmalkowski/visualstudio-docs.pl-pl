---
title: "CA2109: Przejrzyj widoczne programy obsługi zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d437aab8e6e6dcdb0500ecfef53c78fab6c1c6b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Przejrzyj widoczne programy obsługi zdarzeń
|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Wykryto publiczną lub chronioną metodę obsługi zdarzeń.  
  
## <a name="rule-description"></a>Opis reguły  
 Widocznej zewnętrznie metodzie obsługi zdarzeń stanowi problem zabezpieczeń, który wymaga przeglądu.  
  
 Metody obsługi zdarzeń nie powinny być udostępnione, chyba że jest to absolutnie konieczne. Program obsługi zdarzeń typu delegata, która wywołuje metodę narażonych można dodać do dowolnego zdarzenia tak długo, jak program obsługi i zdarzenia podpisy są zgodne. Zdarzenia potencjalnie może być zgłaszany przez kod i są często wygenerowane przez kod wysoce zaufanych system w odpowiedzi na działania użytkownika, takie jak kliknięcie przycisku. Dodawanie sprawdzania zabezpieczeń do metody obsługi zdarzeń nie zapobiega kodu rejestrowania programu obsługi zdarzeń, która wywołuje metodę.  
  
 Żądanie nie może chronić niezawodnie metody wywoływane przez program obsługi zdarzeń. Zabezpieczeń wymaga pomocy zabezpieczyć kod z niezaufanej wywołań, sprawdzając obiektów wywołujących na stosie wywołań. Kod, który dodaje program obsługi zdarzeń do zdarzenia nie jest musi występować w stosie wywołań, podczas uruchamiania metody obsługi zdarzeń. W związku z tym stos wywołań może mieć tylko bardzo zaufane obiekty wywołujące po wywołaniu metody obsługi zdarzeń. Powoduje to, że wprowadzone przez metoda obsługi zdarzeń w celu pomyślnego żądania. Ponadto żądane uprawnienie może potwierdzone po wywołaniu metody. Z tego względu ryzyko nie ustalania naruszenie tej reguły można tylko ocenić po przejrzeniu metoda obsługi zdarzeń. Możesz przejrzeć kod, należy uwzględnić następujące kwestie:  
  
-   Obsługi zdarzenia wykonać wszystkie operacje są niebezpieczne lub kończona, takich jak potwierdzające uprawnienia lub pomijanie kodu niezarządzanego uprawnienia?  
  
-   Co to są zagrożenia bezpieczeństwa, do i z kodu, ponieważ można uruchamiać w dowolnym momencie tylko bardzo zaufane obiekty wywołujące na stosie?  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, przejrzyj metody i ocenić poniżej:  
  
-   Czy można utworzyć metody obsługi zdarzeń niepublicznych?  
  
-   Można przeniesieniu wszystkich niebezpiecznych funkcji poza programu obsługi zdarzeń  
  
-   Jeśli nakłada się na żądanie zabezpieczeń, można to osiągnąć, w inny sposób?  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej zasady tylko po dokonaniu przeglądu zabezpieczeń dokładne upewnij się, że kodu nie stanowią zagrożenia bezpieczeństwa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia metody obsługi zdarzeń, która może być używane przez złośliwy kod.  
  
 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 