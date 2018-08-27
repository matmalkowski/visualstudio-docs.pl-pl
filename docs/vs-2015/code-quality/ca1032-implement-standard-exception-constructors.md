---
title: 'CA1032: Zaimplementuj standardowe konstruktory wyjątku | Dokumentacja firmy Microsoft'
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
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4d8c2f4439cf63f0bab7294898c96b2acb742e7d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902410"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementowanie standardowych konstruktorów wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1032: zaimplementuj standardowe konstruktory wyjątku](https://docs.microsoft.com/visualstudio/code-quality/ca1032-implement-standard-exception-constructors).

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Rozszerza typ <xref:System.Exception?displayProperty=fullName> i nie deklaruje wymagane konstruktorów.

## <a name="rule-description"></a>Opis reguły
 Typy wyjątków należy zaimplementować następujących konstruktorów:

-   NewException() publiczne

-   NewException(string) publiczne

-   publiczne NewException (ciąg, wyjątku)

-   NewException chroniona lub prywatnej (SerializationInfo, StreamingContext)

 Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. Na przykład konstruktora, który ma podpis `NewException(string, Exception)` służy do tworzenia wyjątków, które są spowodowane przez inne wyjątki. Bez tego konstruktora nie może utworzyć i zgłosić wystąpienie usługi niestandardowy wyjątek, który zawiera wewnętrzny wyjątek (zagnieżdżona) czyli jakich kodu zarządzanego, należy wykonać w takiej sytuacji. Pierwsze konstruktory wyjątku trzech są publiczne przez Konwencję. Czwarty Konstruktor jest chronione niezapieczętowanych klas i prywatny w klasach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [CA2229: zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Dodaj brakujące konstruktory wyjątek i upewnij się, że poprawne ułatwień dostępu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli naruszenie jest spowodowany przez przy użyciu poziomu różny dostęp dla konstruktorów publicznych.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ wyjątku, który narusza tę regułę i typ wyjątku, który jest implementowana prawidłowo.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



