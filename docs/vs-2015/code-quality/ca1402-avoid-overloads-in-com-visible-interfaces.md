---
title: 'CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM | Dokumentacja firmy Microsoft'
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
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ece9a444ac308003c56da1bd4f2ecf4433e2b4a9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900529"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM](https://docs.microsoft.com/visualstudio/code-quality/ca1402-avoid-overloads-in-com-visible-interfaces).

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Component Object Model (COM) deklaruje widoczne interfejsu przeciążone metody.

## <a name="rule-description"></a>Opis reguły
 Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia "_" i liczba całkowita, która odpowiada kolejności deklaracji przeciążeń przeciążeń. Na przykład należy wziąć pod uwagę następujące metody.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Te metody są widoczne dla klientów modelu COM jako poniżej.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Klienci Visual Basic 6 COM nie może implementować metody interfejsu za pomocą znaku podkreślenia w nazwie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić nazwy przeciążonych metod, aby nazwy są unikatowe. Alternatywnie ukrywanie interfejs dla modelu COM, zmieniając ułatwień dostępu do `internal` (`Friend` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) lub przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawioną wartość atrybutu `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia interfejs, który narusza regułę określającą, a interfejsem, który spełnia reguły.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z niezarządzanego kodu](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long — typ danych](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



