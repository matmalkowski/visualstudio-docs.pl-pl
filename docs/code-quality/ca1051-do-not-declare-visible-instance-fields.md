---
title: "CA1051: Nie deklaruj widocznych pól wystąpień | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a6a22653abb4b7112e1778bf671f368e8ee28894
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nie deklaruj widocznych pól wystąpień
|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Widoczne na zewnątrz typ ma pola wystąpienia widoczne na zewnątrz.  
  
## <a name="rule-description"></a>Opis reguły  
 Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być `private` lub `internal` i powinien być udostępniany przy użyciu właściwości. Jest tak łatwe do dostępu do właściwości jest dostępu do pola, a w razie funkcji typu rozwiń bez wprowadzania istotne zmiany można zmienić kod w akcesorach właściwości. Właściwości zwracające tylko wartości pola prywatne lub wewnętrzne są optymalizowane w celu wykonania blokowego podczas uzyskiwania dostępu do pola; bardzo mało są bardziej wydajne jest skojarzony z pola widoczne na zewnątrz za pośrednictwem właściwości.  
  
 Widoczne na zewnątrz odwołuje się do `public`, `protected`, i `protected internal` (`Public`, `Protected`, i `Protected Friend` w języku Visual Basic) poziomów ułatwień dostępu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Przekształć pole `private` lub `internal` i pozostawić ją przy użyciu właściwości widoczne na zewnątrz.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Widoczne na zewnątrz pola nie udostępniają wszystkie korzyści, które są niedostępne dla właściwości. Ponadto pola publiczne nie mogą być chronione przez [Linkdemand](/dotnet/framework/misc/link-demands). Zobacz [CA2112: typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu (`BadPublicInstanceFields`), co narusza tę regułę. `GoodPublicInstanceFields`zawiera kod poprawiony.  
  
 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Żądania łączy](/dotnet/framework/misc/link-demands)