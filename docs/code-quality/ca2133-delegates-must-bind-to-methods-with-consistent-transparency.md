---
title: 'CA2133: Delegatów należy powiązać z metodami ze spójną jawnością'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 389de424c3d9e2cd0e12431e857983b267213f9c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920922"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegatów należy powiązać z metodami ze spójną jawnością
|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

> [!NOTE]
>  To ostrzeżenie jest stosowana tylko do kodu, który działa środowisko CoreCLR (wersja środowiska CLR, która jest specyficzna dla aplikacji sieci Silverlight Web).

## <a name="cause"></a>Przyczyna
 To ostrzeżenie generowane na metodę wiążąca delegata, która jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> do metody przezroczysty lub który jest oznaczony atrybutem <xref:System.Security.SecuritySafeCriticalAttribute>. Ostrzeżenie jest także uruchamiane na metodzie wiążącej obiekt delegowany, który jest przezroczysty lub bezpieczny-krytyczny dla metody krytycznej.

## <a name="rule-description"></a>Opis reguły
 Typy delegatów i metod, które wiążą się one na muszą mieć spójną jawność. Przezroczysty i bezpieczne krytyczne delegatów mogą powiązać tylko z innych metod przezroczystego lub bezpieczne krytyczne. Podobnie krytyczne delegatów mogą powiązać tylko z krytycznych metod. Te reguły powiązanie upewnij się, że tylko kod, który można wywołać metodę za pośrednictwem pełnomocnika może mieć również wywołana tej samej metody bezpośrednio. Na przykład powiązanie reguły uniemożliwić wywoływania kodu krytycznego bezpośrednio za pomocą przezroczystego obiektu delegowanego kod przezroczysty.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie to ostrzeżenie, zmień przezroczystość delegata lub metody, która tworzy ona powiązanie, tak aby przezroczystość dwa są równoważne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]