---
title: 'CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b2a7157c405eba52a2a7dc5de3b290a7ff26dc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia
|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ referencyjny, w szczególności oznaczony jako widoczna do składnika modelu COM (Object) zawiera publicznym parametryzowanym konstruktorem, ale nie ma domyślnego (bezparametrowego) konstruktora publicznego.

## <a name="rule-description"></a>Opis reguły
 Klienci COM nie można utworzyć typu bez publicznego konstruktora domyślnego. Jednak typ można nadal będą dostępne dla klientów modelu COM, jeśli inny oznacza, że jest dostępny do utworzenia typu i przekaż go do klienta (na przykład za pomocą wartość zwracana wywołania metody).

 Reguła ignoruje typów pochodzących z <xref:System.Delegate?displayProperty=fullName>.

 Domyślnie widoczne dla modelu COM są następujące: zestawy, typy publiczne elementów członkowskich wystąpienia publicznego w publicznych typach i wszystkie elementy członkowskie typów publicznych wartości.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj publicznego konstruktora domyślnego lub usunąć <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> z typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli inne sposoby służą do tworzenia i przekazany obiekt do klienta COM.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [współpracy z niezarządzany kod](/dotnet/framework/interop/index)