---
title: 'CA1050: Deklaruj typy w przestrzeni nazw'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf38fde258a033fd4050e93d3ad69015f365dc60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Deklaruj typy w przestrzeni nazw
|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typu publiczne lub chronione jest zdefiniowany poza zakresem nazwanych przestrzeni nazw.

## <a name="rule-description"></a>Opis reguły
 Typ został zadeklarowany w przestrzeni nazw, aby uniknąć konfliktów nazw, jak i sposób organizowania powiązanych typów w hierarchii obiektów. Typy, które są poza nazwanych przestrzeni nazw znajdują się w globalnej przestrzeni nazw, która nie może być przywoływany w kodzie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, umieść typ w przestrzeni nazw.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Chociaż nie trzeba pominąć ostrzeżenie od tej reguły, jest bezpieczne, gdy zestaw nigdy nie będzie można używać razem z innych zestawów.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono biblioteki, która ma typ niepoprawnie zadeklarowany poza obszar nazw i typ, który ma taką samą nazwę zadeklarowana w przestrzeni nazw.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Przykład
 Biblioteka, która została zdefiniowana wcześniej aplikację. Należy pamiętać, że typ, który jest zadeklarowana poza przestrzeni nazw jest tworzone, gdy nazwa `Test` nie jest kwalifikowana przez przestrzeni nazw. Należy zauważyć, że dostęp do `Test` wpisz `Goodspace`, wymagana jest nazwa przestrzeni nazw.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]