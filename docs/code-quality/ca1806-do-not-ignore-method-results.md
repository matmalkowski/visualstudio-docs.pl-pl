---
title: 'CA1806: Nie ignoruj wyników metod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6b0d5870b29fea9d6ef99a3951ef12d938b0eab3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914669"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Nie ignoruj wyników metod
|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Istnieje kilka możliwych przyczyn tego ostrzeżenia:

-   Nowy obiekt utworzony, ale nigdy używane.

-   Wywoływana jest metoda, która tworzy i zwraca nowy ciąg i nowy ciąg nie jest nigdy używane.

-   Metodę COM lub P/Invoke, która zwraca kod HRESULT lub błędu, który nie jest nigdy używane. Opis reguły

 Tworzenie obiektu niepotrzebnych i skojarzone wyrzucanie elementów bezużytecznych nieużywane obiektu obniżyć wydajność.

 Ciągi są niezmienne i metod, takich jak String.ToUpper zwraca nowe wystąpienie ciągu zamiast modyfikowanie wystąpienie ciągu w przypadku wywołania metody.

 Ignorowanie HRESULT lub kodu błędu może prowadzić do nieoczekiwanego zachowania w warunkach błędu lub warunków zasobów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli metoda tworzy nowe wystąpienie obiektu B, który nie jest nigdy używana, przekaż wystąpienie jako argument do innej metody lub Przypisz wystąpienie do zmiennej. Jeśli nie jest konieczne tworzenie obiektów, usuń go.- lub -

 Jeśli metoda wywołuje metodę B, ale nie używa nowego wystąpienia ciągu, która zwraca metodę B. Przekaż wystąpienie jako argument do innej metody, przypisz wystąpienie do zmiennej. Lub Usuń wywołanie, jeśli nie jest konieczne.

 —lub—

 Jeśli metoda wywołuje metodę B, ale nie używa HRESULT lub kodu błędu, który zwraca metodę. Użyj wyniku w instrukcji warunkowej, przypisz wynik do zmiennej lub przekaż go jako argument do innej metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenie od tej reguły, chyba że utworzenie obiektu pełni niektóre funkcje.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono klasę, która ignoruje wynik wywołania String.Trim.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Przykład
 Poniższy przykład poprawki poprzedniej naruszenie przez przypisanie wynik String.Trim zmienną, która została wywołana w.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę, która nie używa obiektu, który tworzy.

> [!NOTE]
>  W języku Visual Basic nie można odtworzyć to naruszenie.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład poprawki poprzedniej naruszenie przez usunięcie niepotrzebnych utworzenia obiektu.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->