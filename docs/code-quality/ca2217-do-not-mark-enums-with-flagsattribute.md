---
title: "CA2217: Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b76453fe2283acace75cddbbdc3ccb08864c60c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute
|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wyliczenie widoczne na zewnątrz jest oznaczony atrybutem <xref:System.FlagsAttribute> i ma jedną lub więcej wartości, które nie są potęgami liczby dwa lub kombinacji innych wartości określone w wyliczeniu.  
  
## <a name="rule-description"></a>Opis reguły  
 Wyliczenie powinny mieć <xref:System.FlagsAttribute> przedstawia tylko wtedy, gdy każda wartość zdefiniowana w wyliczeniu jest potęgą liczby dwa lub kombinacji zdefiniowanych wartości.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń <xref:System.FlagsAttribute> z wyliczenia.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono wyliczenie kolor, który zawiera wartość 3, który nie jest ani potęgą liczby dwa ani kombinacji zdefiniowanych wartości. Wyliczenie kolorów nie powinien być oznaczony przez <xref:System.FlagsAttribute>.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono wyliczenie, dni, który spełnia wymagania oznaczana z System.FlagsAttribute.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.FlagsAttribute?displayProperty=fullName>