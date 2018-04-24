---
title: 'CA1412: Oznacz interfejsy ComSource jako IDispatch'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e4c446f1838120afd1dbcdf21ce9710982d38c0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Oznacz interfejsy ComSource jako IDispatch
|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybut i co najmniej jeden określony interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> ustawić atrybutu `InterfaceIsDispatch` wartość.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Służy do identyfikowania interfejsów zdarzeń, które udostępnia klasy do klientów modelu COM (Component Object). Te interfejsy musi być udostępniany jako `InterfaceIsIDispatch` aby umożliwić klientom Visual Basic 6 COM otrzymywać powiadomienia o zdarzeniach. Domyślnie, jeśli interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutu jest uwidaczniany jako interfejs podwójny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, dodawania lub modyfikowania <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutu, dzięki czemu jego wartość jest równa InterfaceIsIDispatch dla wszystkich interfejsów, które są określane za pomocą <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono klasę, w którym jednego z interfejsów naruszają tę regułę.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)