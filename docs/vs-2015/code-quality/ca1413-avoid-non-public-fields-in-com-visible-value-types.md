---
title: 'CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM | Dokumentacja firmy Microsoft'
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
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 190ca50d00d17d36eb4cab82f6062e3241b65469
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680657"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Unikaj pól niepublicznych w typach wartościowych widocznych dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](https://docs.microsoft.com/visualstudio/code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types).  
  
Element TypeName | AvoidNonpublicFieldsInComVisibleValueTypes |  
| CheckId | CA1413 |  
| Kategoria | Microsoft.Interoperability|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Typ wartości, który jest specjalnie oznaczony jako widoczny na Component Object Model (COM), deklaruje pola niepubliczne wystąpień.  
  
## <a name="rule-description"></a>Opis reguły  
 Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pola, aby uzyskać informacje, które nie powinny zostać ujawnione lub będą mieć niezamierzone efektu projektu lub zabezpieczeń.  
  
 Domyślnie wszystkie typy publiczne wartości są widoczne dla modelu COM. Aby zmniejszyć liczbę fałszywych alarmów, ta reguła wymaga widoczność COM typu, który ma być jawnie określony. Muszą być oznaczone zawierające zestaw <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> równa `false` i typ musi być oznaczony przez <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `true`.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady i zachować pole ukryte, Zmień typ wartości typu odwołania lub usuń <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutów z typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli ujawnienia pola.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje typ, który narusza regułę.  
  
 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Kwalifikowanie typów .NET do międzyoperacyjności](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



