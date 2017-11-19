---
title: "CA1704: Identyfikatory powinny być napisane poprawnie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e43e3340cdbc05ec00c909542e201692199ccfef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Identyfikatory powinny być napisane poprawnie
|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa identyfikatora zawiera co najmniej jeden słowa, które nie są rozpoznawane przez moduł sprawdzania pisowni biblioteki. Ta zasada nie Sprawdź konstruktorów lub o nazwie specjalne elementów członkowskich, takich jak get i ustawić metod dostępu do właściwości.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada analizuje identyfikator w tokenach oraz sprawdzając pisownię każdego tokenu. Algorytm analizy wykonuje następujące przekształcenia:  
  
-   Wielkie litery uruchomić nowy token. Na przykład MyNameIsJoe tokenizes "Mój", "Name", "Is", "Jan".  
  
-   W przypadku wielu wielkich liter ostatni wielką literę uruchamia nowy token. Na przykład GUIEditor tokenizes do "Graficznym interfejsem użytkownika", "Edytor".  
  
-   Początkowe i końcowe apostrofów zostaną usunięte. Na przykład "sender" tokenizes do "sender".  
  
-   Znaki podkreślenia oznaczającego koniec token i są usuwane. Na przykład Hello_world tokenizes na tekst "Hello", "world".  
  
-   Osadzony takie znaki zostaną usunięte. Na przykład dla & mat tokenizes do "format".  
  
 Domyślnie używana wersja angielski (en) przez moduł sprawdzania pisowni. Brak słowników języka są obecnie dostępne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Popraw pisownię wyrazu lub Dodaj ten wyraz do słownika niestandardowego o nazwie CustomDictionary.xml. Umieść słownik w katalogu instalacji narzędzia katalogu projektu lub w katalogu, który jest skojarzony z narzędzia w profilu użytkownika (%USERPROFILE%\Application danych\\...). Aby dowiedzieć się, jak dodać słownika niestandardowego do projektu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zobacz [porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Dodaj wyrazy, które nie powinno powodować naruszenie ścieżce Recognized-słownika/słów.  
  
-   Dodaj wyrazy, które powinno spowodować naruszenie ścieżce nierozpoznany-słownika/słów.  
  
-   Dodaj wyrazy, które powinny być oznaczone jako przestarzałe w ścieżce słownika/słowa/przestarzały. Zobacz temat powiązane reguły [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md) Aby uzyskać więcej informacji.  
  
-   Dodawanie wyjątków z regułami wielkości liter akronim do słownika/akronimów/CasingExceptions ścieżki.  
  
 Oto przykład struktury plików słownika.  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej zasady tylko wtedy, gdy jest celowe błędne słowo i wyraz dotyczy ograniczony zestaw biblioteki. Poprawnie zapisanych wyrazów skrócić czas nauki wymaganego dla nowej biblioteki oprogramowania.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2204: Literały powinny być napisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: Ciągów zasobów powinna być poprawna](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identyfikatory powinny różnić się tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
