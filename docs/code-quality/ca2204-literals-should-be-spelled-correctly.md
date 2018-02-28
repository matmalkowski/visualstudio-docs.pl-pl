---
title: "CA2204: Literały powinny być napisane poprawnie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ad1fb951f17d223f248c678738070d1c5b70ae7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literały powinny być napisane poprawnie
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Przekazuje metody, ciąg literału, do którego jest używany w parametru lub właściwości, które wymaga zlokalizowany ciąg literału ciągu zawiera co najmniej jeden słowa, które nie są rozpoznawane przez moduł sprawdzania pisowni biblioteki.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła sprawdza ciąg literału, który jest przekazywany jako wartość parametru lub właściwości, gdy dla jednego lub więcej z następujących przypadków ma wartość true:  
  
-   <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwość jest ustawiona na true.  
  
-   Nazwa parametru lub właściwości zawiera "Text", "Komunikat" lub "Podpis".  
  
-   Nazwa parametru ciągu, który jest przekazywany do metody Console.Write lub elementu Console.WriteLine jest "value" lub "format".  
  
 Ta reguła umożliwia przekształcanie ciągów literałów w wyrazy, tokenizację wyrazy złożone, sprawdzając pisownię każdego wyrazu/tokenu. Uzyskać informacji o algorytmie analizy, zobacz [CA1704: identyfikatory powinny być napisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Domyślnie używana wersja angielski (en) przez moduł sprawdzania pisowni.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Popraw pisownię wyrazu, lub Dodaj ten wyraz do słownika niestandardowego. Aby uzyskać informacje o sposobie używania niestandardowych słowników, zobacz [porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Poprawnie zapisanych wyrazów skrócić czas nauki wymagane dla nowej biblioteki oprogramowania.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)