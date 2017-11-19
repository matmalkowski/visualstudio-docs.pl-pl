---
title: "CA1709: Identyfikatory powinny mieć prawidłową wielkość liter | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9332359228d657e9155996443822a5d1c11ad01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Identyfikatory powinny być zapisywane z uwzględnieniem wielkości liter
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Przerywanie — gdy na zestawy, obszary nazw, typów, członków i parametry.<br /><br /> Bez podziału — po na parametry typu ogólnego.|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa identyfikatora jest nie z uwzględnieniem wielkości liter.  
  
 \-lub -  
  
 Nazwa identyfikatora zawiera akronim dwuliterowych i drugą literę jest pisana małymi literami.  
  
 \-lub -  
  
 Nazwa identyfikatora zawiera akronim co najmniej trzech wielkich liter.  
  
## <a name="rule-description"></a>Opis reguły  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
 Konwencja nazwy parametrów Użyj mieszanej wielkości liter; nazwy przestrzeni nazw, typu i element członkowski użyć Pascal wielkości liter. W nazwie formatu — z uwzględnieniem wielkości liter jest małe litery, a pierwszą literę wszelkie pozostałe słów w nazwie jest pisane wielkimi literami. Przykłady stosowania formatu — z uwzględnieniem wielkości liter nazwy to "packetSniffer", "ioFile" i "fatalErrorCode". W nazwie Pascal — z uwzględnieniem wielkości liter jest wielką literą, a pierwsza litera wszelkie pozostałe słów w nazwie jest pisane wielkimi literami. Przykłady Pascal — z uwzględnieniem wielkości liter nazwy to "PacketSniffer", "IOFile" i "FatalErrorCode".  
  
 Ta zasada dzieli nazwę na słów w oparciu o wielkości liter i sprawdza słów dwuliterowych z listą popularnych wyrazów dwuliterowych, takie jak "W" lub "Moje". Jeśli nie, wyraz zakłada się, że skrótem. Ponadto ta reguła przyjęto założenie, że znalazła akronim, jeśli nazwa zawiera cztery wielkich liter w wierszu albo trzy wielkich liter w wiersz na końcu nazwy.  
  
 Według Konwencji akronimów dwuliterowych używać wielkie litery, a akronimów trzy lub więcej znaków Pascal wielkości liter. W poniższych przykładach użyto tę konwencję nazewnictwa: "Bazy danych", "CR", "Cpa" i "Ecma". Poniższe przykłady narusza konwencji: ' We/wy', 'XML' i "DoD" oraz nazwy nonparameter, "xp" i "Panel sterowania".  
  
 'ID' to specjalne liter spowodować naruszenie tej reguły. 'Id' nie jest skrót, ale stanowi skrót od "Identyfikacja".  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę, dzięki czemu jest prawidłową wielkość liter.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć to ostrzeżenie, jeśli masz konwencji nazewnictwa, czy identyfikator reprezentuje nazwę poprawnej, na przykład nazwę firmy lub technologii.  
  
 Można również dodać konkretnych terminów, skrótów i akronimów do słownika analizy kodu. Warunki określone w słownika nie spowoduje naruszeń tej reguły. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1708: Identyfikatory powinny różnić się tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)