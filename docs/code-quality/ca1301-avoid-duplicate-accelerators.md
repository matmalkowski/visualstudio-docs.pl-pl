---
title: 'CA1301: Należy unikać duplikowania akceleratorów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4dac6beddf43e88d47a54ddf2b0e0d56e387038
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547206"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Należy unikać duplikowania akceleratorów

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Rozszerza typ <xref:System.Windows.Forms.Control?displayProperty=fullName> i zawiera co najmniej dwóch najwyższego poziomu kontrolki, które mają identyczne klawiszy, które są przechowywane w pliku zasobów.

## <a name="rule-description"></a>Opis reguły

Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do kontrolki za pomocą **Alt** klucza. Kiedy wiele formantów ma ten sam klucz dostępu, zachowanie klucza dostępu nie jest dobrze zdefiniowane. Użytkownik może być mogli korzystać z zamierzonym kontroli przy użyciu klucza dostępu, i może być włączona kontrola innym niż ten, który jest przeznaczony.

Bieżąca implementacja parametru ta zasada powoduje ignorowanie elementów menu. Jednak elementy menu, w tym samym podmenu nie powinna mieć identyczny klawiszy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy określić klucze dostępu unikatowe dla wszystkich kontrolek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje minimalny formularz, który zawiera dwa formanty, które mają identyczne klawiszy. Klucze są przechowywane w pliku zasobów, która nie jest wyświetlany. Jednak ich wartości są wyświetlane w skomentowanej się `checkBox.Text` wierszy. Zachowanie duplikowania akceleratorów można sprawdzić przez wymianę `checkBox.Text` wiersze z ich odpowiedniki skomentowanej out. Jednak w takim przypadku przykład nie wygeneruje ostrzeżenia z reguły.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)