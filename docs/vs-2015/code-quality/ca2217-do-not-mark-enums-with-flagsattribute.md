---
title: 'CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute | Dokumentacja firmy Microsoft'
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
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 638208a697a84dc6e6c76dc3981bca98d530a22f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680438"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2217: nie oznaczaj wyliczeń za pomocą FlagsAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca2217-do-not-mark-enums-with-flagsattribute).  
  
Element TypeName | DoNotMarkEnumsWithFlags |  
| CheckId | CA2217 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz wyliczenie jest oznaczona za pomocą <xref:System.FlagsAttribute> i ma jedną lub więcej wartości, które nie są potęgami dwa lub kombinacji innych zdefiniowanych wartości w wyliczeniu.  
  
## <a name="rule-description"></a>Opis reguły  
 Wyliczenie powinny mieć <xref:System.FlagsAttribute> obecne tylko wtedy, gdy każda wartość zdefiniowana w wyliczeniu jest potęgą liczby dwa, lub kombinacji zdefiniowane wartości.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, Usuń <xref:System.FlagsAttribute> z wyliczenia.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje wyliczenie kolor, który zawiera wartość 3, która jest potęgą liczby dwa, ani kombinację wszystkich zdefiniowanych wartości. Wyliczenie Color nie powinien być oznaczony za pomocą <xref:System.FlagsAttribute>.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]  
  
## <a name="example"></a>Przykład  
 Wyliczenie, dni, który spełnia wymagania są oznaczone System.FlagsAttribute można znaleźć w poniższym przykładzie.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.FlagsAttribute?displayProperty=fullName>



