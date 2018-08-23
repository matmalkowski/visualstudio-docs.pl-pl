---
title: 'CA1709: Identyfikatory powinny mieć prawidłową wielkość liter | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a06d85367ae40b05e76f89c9b1bf0dac11e1980
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630484"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Identyfikatory powinny być zapisywane z uwzględnieniem wielkości liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [CA1709: identyfikatory powinny mieć prawidłową wielkość liter](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Przerywanie — gdy wywołany zestawów, przestrzeni nazw, typów, elementów członkowskich i parametry.<br /><br /> Bez podziału — gdy wywoływane w parametrach typu ogólnego.|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa identyfikatora nie jest poprawna.  
  
 \- lub —  
  
 Nazwa identyfikatora zawiera akronim dwuliterowych, a drugi literą jest pisana małymi literami.  
  
 \- lub —  
  
 Nazwa identyfikatora zawiera akronim co najmniej trzech wielkich liter.  
  
## <a name="rule-description"></a>Opis reguły  
 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.  
  
 Według Konwencji nazwy parametrów używają notacji camelcase; nazwy przestrzeni nazw, typów i elementów członkowskich Użyj Pascal wielkość liter w wyrazie. W nazwie formacie camelcase pierwszą literą jest pisana małymi literami, a pierwszą literę wszelkie pozostałe słów w nazwie jest pisane wielkimi literami. Przykłady formacie camelcase nazw są "packetSniffer", "ioFile" i "fatalErrorCode". W nazwie Pascal — z uwzględnieniem wielkości liter pierwszą literą jest wielką literą, a pierwsza litera wszystkie pozostałe słowa jest pisane wielkimi literami. Przykłady Pascal — z uwzględnieniem wielkości liter nazwy to "PacketSniffer", "IOFile" i "FatalErrorCode".  
  
 Ta zasada dzieli nazwę w oparciu o wielkość liter w wyrazie wyrazy i sprawdza, czy wszystkie wyrazy dwuliterowych z listą popularne wyrazy dwuliterowych, takie jak "In" lub "Moje". Jeśli nie zostanie znalezione dopasowanie, wyraz zakłada się, że akronim. Ponadto ta reguła zakłada, że znalazł akronim, gdy nazwa zawiera cztery wielkich liter w wierszu albo trzy wielkich liter w wierszu na końcu nazwy.  
  
 Zgodnie z Konwencją skrótów dwuliterowych Użyj wielkie litery, a akronimów trzech lub więcej znaków Użyj Pascal wielkość liter w wyrazie. W poniższych przykładach używane tę konwencję nazewnictwa: "DB", "CR", "Cpa" i "Ecma". Poniższe przykłady naruszają Konwencji: "We/wy", "XML" i "DoD" i nazw nonparameter, "xp" i "Panel sterowania".  
  
 'Identyfikator' to specjalny — z uwzględnieniem wielkości liter spowodować naruszenie tej zasady. 'Identyfikator' nie jest akronim, ale stanowi skrót od "Identyfikacja".  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę, dzięki czemu jest poprawna.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć to ostrzeżenie, jeśli masz konwencje nazewnictwa, czy identyfikator reprezentuje nazwę odpowiedniego, na przykład nazwę firmy lub technologii.  
  
 Można również dodać konkretne terminy, skrótów i akronimów ją do niestandardowego słownika analizy kodu. Terminem do słownika nie spowoduje naruszenie tej zasady. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

