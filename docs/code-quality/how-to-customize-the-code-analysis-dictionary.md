---
title: 'Porady: dostosowywanie słownika analizy kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2d60b2a187b7fccf4d5f564d9554badd5da9dec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Porady: dostosowywanie słownika analizy kodu
Kod — analiza używa wbudowanych słownika do sprawdzania identyfikatory w kodzie błędy w pisowni, gramatyczne przypadek i inne konwencje nazewnictwa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wytyczne. Można utworzyć pliku Xml słownika, aby dodać, usunąć lub zmodyfikować warunki, skrótów i akronimów do słownika wbudowanych.  
  
 Na przykład, załóżmy, że kod zawiera klasę o nazwie **DoorKnokker**. Analiza kodu będzie zidentyfikować nazwę jako związkiem dwa wyrazy: **drzwi** i **knokker**. Następnie wywołałoby ostrzeżenie który **knokker** nie został poprawnie wpisany. Aby wymusić analizy kodu do rozpoznawania pisownię, należy dodać termin **knokker** do słownika niestandardowego.  
  
## <a name="to-create-a-custom-dictionary"></a>Aby utworzyć słownika  
 Utwórz plik o nazwie **CustomDictionary.xml**.  
  
 Definiowanie niestandardowych słów przy użyciu następującej struktury XML:  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>Elementy słownika  
 Dodawanie warunków jako tekst wewnętrzny z następujących elementów do słownika można zmodyfikować zachowanie słownika analizy kodu:  
  
-   [Słownik/słowa/rozpoznany/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Słownik/słowa/nierozpoznany/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Słownik/słowa/przestarzałe/termin [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Słownik/słowa/związek/termin [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Słownik/słowa/DiscreteExceptions/termin](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Słownik/akronimów/CasingExceptions/akronim](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Słownik/słowa/rozpoznany/Word  
 Aby dołączyć termin warunków, które identyfikują analizy kodu jako poprawnie zapisany na liście, należy dodać termin jako tekst wewnętrzny elementu słownika/słowa/Recognized/Word. Warunki w elementach słownika/słowa/Recognized/Word nie jest rozróżniana.  
  
 **Przykład**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Warunki w węzłach Recognized-słownika/wyrazy są stosowane do następujących reguł analizy kodu:  
  
-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Słownik/słowa/nierozpoznany/Word  
 Aby wykluczyć warunek z listy warunków, które identyfikuje analizy kodu jako poprawnie zapisany, Dodaj wyrażenie, aby wykluczyć je jako tekst wewnętrzny elementu słownika/słowa/nierozpoznany/Word. Warunki w elementach słownika/słowa/nierozpoznany/Word nie jest rozróżniana.  
  
 **Przykład**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Warunki w węźle nierozpoznany-słownika/wyrazy są stosowane do następujących reguł analizy kodu:  
  
-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Słownik/słowa/przestarzałe/termin [@PreferredAlternate]  
 Aby dołączyć termin Lista warunków, które identyfikuje analizy kodu jako przestarzałe, należy dodać termin jako tekst wewnętrzny elementu słownika/słowa/przestarzały/termin. Przestarzałe termin jest słowa, które jest poprawna, ale nie powinny być używane.  
  
 Aby dołączyć sugerowany termin alternatywny ostrzeżenia, należy określić alternatywnego w atrybucie PreferredAlternate elementu terminu. Wartość atrybutu może pozostać puste, jeśli nie chcesz sugerować alternatywne.  
  
-   Przestarzałe termin w słownika / / przestarzały/termin element nie jest rozróżniana wielkość liter.  
  
-   Wartość atrybutu PreferredAlternate jest rozróżniana wielkość liter. Użyj litery Pascal dla złożonych alternatyw.  
  
 **Przykład**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Warunki w węźle przestarzały-słownika/wyrazy są stosowane do następujących reguł analizy kodu:  
  
-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Słownik/słowa/związek/termin [@CompoundAlternate]  
 Wbudowane słownika identyfikuje terminy, jako pojedynczą, odrębne warunki zamiast terminu złożonego. Do dołączenia do listy warunków, które identyfikują analizy kodu jako wyraz złożony termin i określ poprawny wielkość liter w wyrazie termin, Dodaj termin jako tekst wewnętrzny elementu słownika/słowa/związek/terminu. W atrybucie CompoundAlternate elementu termin Określ poszczególnych wyrazów wchodzące w skład złożonych termin przez pierwszą literę poszczególnych wyrazów (Pascal wielkości liter). Należy pamiętać, że okres określony w tekście wewnętrznym jest automatycznie dodawany do listy DiscreteExceptions-słownika/słów.  
  
-   Przestarzałe termin w słownika / / przestarzały/termin element nie jest rozróżniana wielkość liter.  
  
-   Wartość atrybutu PreferredAlternate jest rozróżniana wielkość liter. Użyj litery Pascal dla złożonych alternatyw.  
  
 **Przykład**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Warunki w węźle słownika/słowa/złożone są stosowane do następujących reguł analizy kodu:  
  
-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Słownik/słowa/DiscreteExceptions/termin  
 Aby wykluczyć termin na liście terminów, które identyfikuje analizy kodu jako pojedynczy, odrębny word, gdy zaznaczone jest pole termin reguł wielkości liter dla wyrazy złożone, Dodaj termin jako tekst wewnętrzny elementu słownika/słowa/DiscreteExceptions/terminu. Termin w elemencie słownika/słowa/DiscreteExceptions/termin nie jest rozróżniana wielkość liter.  
  
 **Przykład**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Warunki w węźle DiscreteExceptions-słownika/wyrazy są stosowane do następujących reguł analizy kodu:  
  
-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Słownik/akronimów/CasingExceptions/akronim  
 Aby objąć akronim Lista warunków, które analizy kodu wskazywany jest poprawna i wskazują, jak zasady wyrazy złożone akronim, gdy zaznaczone jest pole termin w małych i wielkich liter, Dodaj termin jako tekst wewnętrzny słownika/akronimów/CasingExceptions / Acronym element. Akronim w elemencie słownika/akronimów/CasingExceptions/skrót jest rozróżniana wielkość liter.  
  
 **Przykład**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Warunki w węźle słownika/akronimów/CasingExceptions są stosowane do następujących reguł analizy kodu:  
  
-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Aby zastosować słownika niestandardowego do projektu  
  
1.  W **Eksploratora rozwiązań**, użyj jednej z następujących procedur:  
  
2.  Aby dodać słownika do pojedynczego projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj istniejący element**. Określ plik w **Dodaj istniejący element** okno dialogowe.  
  
3.  Aby dodać słownika użytkowany przez dwa lub więcej projektów, Znajdź plik do udziału w **Dodaj istniejący element** okna dialogowego kliknij strzałkę w dół na **Dodaj** przycisk, a następnie kliknij przycisk **Dodaj jako Link** .  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **CustomDictionary.xml** nazwę pliku i kliknij przycisk **właściwości**.  
  
5.  Z **Akcja kompilacji** listy, wybierz **CodeAnalysisDictionary**.  
  
6.  Z **Kopiuj do katalogu wyjściowego** listy, wybierz **nie należy kopiować**.