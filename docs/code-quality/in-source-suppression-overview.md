---
title: "W kodzie źródłowym-omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92babbf3c7a5863d178463b69525bdb722bf28ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="in-source-suppression-overview"></a>Ograniczanie w kodzie źródłowym - Omówienie
Pomijanie w źródła jest możliwość Pomiń lub Ignoruj naruszeń analizy kodu w kodzie zarządzanym przez dodanie **SuppressMessage** atrybutu segmenty kodu, które powodują naruszenia. **SuppressMessage** atrybut jest atrybutem warunkowym, który jest dostępny w IL metadanych zestawu z kodu zarządzanego, tylko wtedy, gdy CODE_ANALYSIS symbol kompilacji jest definiowany w czasie kompilacji.  
  
 W języku C + +/ CLI, użyj makra CA_SUPPRESS_MESSAGE lub CA_GLOBAL_SUPPRESS_MESSAGE w pliku nagłówka, aby dodać ten atrybut.  
  
 Nie należy używać w źródłowym pominięć w kompilacjach wydania Aby uniknąć przypadkowego wysyłania metadanych pomijanie w źródła. Z powodu przetwarzania pomijania-source wydajność aplikacji może być znacznie umieszczając metadanych pomijanie w źródła.  
  
> [!NOTE]
>  Nie masz do strony kodu te atrybuty samodzielnie. Aby uzyskać więcej informacji, zobacz [porady: pomijanie ostrzeżeń przy użyciu elementu Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Element menu nie jest dostępna dla kodu C++.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage — atrybut  
 Po kliknięciu prawym przyciskiem myszy ostrzeżenia analizy kodu w **listy błędów** , a następnie kliknij przycisk **Pomiń komunikaty**, **SuppressMessage** jest dodawany atrybut kodu lub do Plik pominięć globalnych projektu.  
  
 **SuppressMessage** atrybut ma następujący format:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Gdzie:  
  
-   **Reguły kategorii** -kategorii, w którym zdefiniowana jest reguła. Aby uzyskać więcej informacji o kategoriach reguł analizy kodu, zobacz [analizy kodu dla zarządzanego kodu — ostrzeżenia](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Identyfikator reguły** — identyfikator reguły. Obsługa obejmuje zarówno nazwę krótkich i długich identyfikatorem reguły. Krótka nazwa jest CAXXXX; długa nazwa jest CAXXXX:FriendlyTypeName.  
  
-   **Justowanie** — tekst, który jest używany do dokumentu Przyczyna pomijanie wiadomości.  
  
-   **Identyfikator wiadomości** — Unikatowy identyfikator problemu dla każdego komunikatu.  
  
-   **Zakres** — element docelowy, na którym pomijane jest ostrzeżenie. Jeśli element docelowy nie zostanie określony, ustawiono element docelowy atrybutu. Zakresy obsługiwane są następujące:  
  
    -   Moduł  
  
    -   Przestrzeń nazw  
  
    -   Zasób  
  
    -   Typ  
  
    -   Element członkowski  
  
-   **Docelowy** — identyfikator, który służy do określania docelowych, na którym pomijane jest ostrzeżenie. Musi zawierać element w pełni kwalifikowaną nazwę.  
  
## <a name="suppressmessage-usage"></a>Użycie SuppressMessage  
 Ostrzeżenia analizy kodu są pomijane na poziomie, do którego wystąpienia **SuppressMessage** atrybut jest stosowany. Celem tego jest ściśle połączenie informacji pomijania kod gdzie występuje naruszenie.  
  
 Ogólny kształt pomijania obejmuje kategoria reguł i identyfikator reguły, który zawiera opcjonalne reprezentacja zrozumiałą dla użytkownika nazwa reguły. Na przykład  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 W przypadku ze względu na wydajność strict dla minimalizując pomijanie w źródła metadanych nazwa reguły może pozostać. Kategoria reguł wraz z jego identyfikator reguły stanowić wystarczająco Unikatowy identyfikator reguły. Na przykład  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Ten format nie jest zalecane z powodu problemów dotyczących utrzymania.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Pomijanie wielu naruszeń w treści metody  
 Atrybuty można stosować do metody i nie może być osadzony w treści metody. Jednak jako identyfikator komunikatu w celu rozróżnienia wielu wystąpień naruszenia w metodzie można określić identyfikatora.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Kompilatory kodu zarządzanego i niektóre narzędzia innych firm generowanie kodu w celu ułatwienia kodu szybkie programowanie. Kod wygenerowany przez kompilator pojawia się w plikach źródłowych jest zwykle oznaczony atrybutem **GeneratedCodeAttribute** atrybutu.  
  
 Można wybrać, czy pominąć kod analizy ostrzeżenia i błędy dla wygenerowanego kodu. Informacje o sposobie Pomiń tych ostrzeżeń i błędów, zobacz [porady: pomijanie ostrzeżeń dla wygenerowany kod](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Należy pamiętać, że analiza kodu ignoruje **GeneratedCodeAttribute** gdy jest stosowany do całego zestawu lub jeden parametr. Tych sytuacjach występują rzadko.  
  
## <a name="global-level-suppressions"></a>Pominięcia na poziomie globalnym  
 Sprawdza, czy narzędzie do analizy kodu zarządzanego **SuppressMessage** atrybuty, które są stosowane na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametr. On również generowane naruszeń względem zasobów i przestrzenie nazw. Naruszenia należy zastosować na poziomie globalnym zakresie i docelowe. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Pomijaj ostrzeżenia o zakresie przestrzeni nazw, powoduje pominięcie ostrzeżenie przed przestrzeni nazw, do samej siebie. Odrzuca ostrzeżenie przed typy w przestrzeni nazw.  
  
 Wszelkie pomijania można wyrazić, określając zakres jawnego. Te pominięć musi istnieć na poziomie globalnym. Pomijanie poziom elementu członkowskiego nie można określić przez dekoracji typu.  
  
 Pominięcia na poziomie globalnych są jedynym sposobem na wyświetlanie komunikatów, które odwołują się do kod wygenerowany przez kompilator, który nie został zmapowany do źródła jawnie podany użytkownik. Na przykład następujący kod pomija naruszenie względem konstruktora wysyłanego kompilatora:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Cel zawsze zawiera element w pełni kwalifikowaną nazwę.  
  
## <a name="global-suppression-file"></a>Plik pominięć globalnych  
 Plik pominięć globalnych przechowuje pominięć pominięcia na poziomie globalnym lub ograniczeń, które nie określają elementu docelowego. Na przykład ograniczeń dla zestawu poziomu naruszeń są przechowywane w tym pliku. Ponadto niektóre pominięć ASP.NET są przechowywane w tego pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kod związany z formularzem. Pomijanie globalnego jest tworzony i dodawany do projektu po raz pierwszy należy wybrać **w pliku pominięć projektu** opcji **Pomiń komunikaty** polecenie w oknie Lista błędów. Aby uzyskać więcej informacji, zobacz [porady: pomijanie ostrzeżeń przy użyciu elementu Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.CodeAnalysis>