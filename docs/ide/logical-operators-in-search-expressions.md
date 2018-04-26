---
title: Operatory logiczne i operatorzy zaawansowani w wyrażeniach wyszukiwania
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de351e019c4daacc61bbbdd2757b0f0d9a46e584
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operatory logiczne i zaawansowanego w wyrażeniach wyszukiwania

Operatory logiczne i operatory wyszukiwania zaawansowanego można użyć uściślić wyszukiwanie zawartości pomocy w **podglądu pomocy**.

## <a name="logical-operators"></a>Operatory logiczne

Operatory logiczne Określ, jak wiele terminy wyszukiwania powinny być łączone w zapytania wyszukiwania. W poniższej tabeli nie zawiera operatorów logicznych AND, OR i w pobliżu.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|
|-------------------|---------|-------------|------------|
|Oba warunki, w tym samym artykule|AND|dib i palety|Tematów zawierających "dib" i "palety".|
|Albo termin w artykule|LUB|rastrowe lub wektora|Tematy zawierające "rastrowe" lub "wektorów".|
|Pierwszy okres bez drugi warunek, w tym samym artykule|NIE|"system operacyjny" nie DOS|Tematy zawierające "system operacyjny", ale nie "DOS".|
|Oba warunki, zamknij razem w artykule|W POBLIŻU|Użytkownik NIEMAL jądra|Tematy zawierające "użytkownika" w pobliżu "jądra".|

> [!IMPORTANT]
> Operatory logiczne wprowadź wielkimi literami dla aparatów wyszukiwania rozpoznać ich.

## <a name="advanced-operators"></a>Operatorzy zaawansowani

Operatory wyszukiwania zaawansowanego Uściślij kryteria wyszukiwania dla zawartości, określając where w artykule, aby wyszukać terminu wyszukiwania. W poniższej tabeli opisano cztery operatory wyszukiwania zaawansowanego dostępne.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|
|-------------------|---------|-------------|------------|
|Termin w tytuł artykułu|`title:`|`title:binaryreader`|Tematy zawierające "binaryreader" w ich tytułów.|
|Termin w przykładzie kodu|`code:`|`code:readdouble`|Tematy zawierające "readdouble" w przykładzie kodu.|
|Termin w przykładzie określonego języka programowania|`code:vb:`|`code:vb:string`|Tematy zawierające "string" w przykładzie kodu języka Visual Basic.|
|Artykuł, w którym jest skojarzony ze słowem kluczowym określonego indeksu|`keyword:`|`keyword:readbyte`|Tematy, które są skojarzone ze słowem kluczowym "readbyte" indeksu.|

> [!IMPORTANT]
> Należy wprowadzić operatory wyszukiwania zaawansowanego z dwukropkiem końcowego i nie pośredniczące spację przed dwukropkiem dla aparatu wyszukiwania rozpoznać ich.

### <a name="programming-languages-for-code-examples"></a>Języki programowania, przykłady kodu

Można użyć `code:` operatora, aby znaleźć zawartości o wielu języków programowania. Aby przywrócić przykłady dla określonego języka programowania, użyj jednej z następujących wartości język programowania:

|Język programowania|Składnia poleceń wyszukiwania — operator|
|--------------------|---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:` Operator znajduje tylko zawartości oznaczonej z etykietą języka programowania, w przeciwieństwie do zawartości, ogólnie oznaczony jako kod.

## <a name="see-also"></a>Zobacz także

- [Porady: wyszukiwanie tematów](how-to-search-for-topics.md)
- [Podgląd Pomocy firmy Microsoft](microsoft-help-viewer.md)
