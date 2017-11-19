---
title: "Operatory logiczne i operatorzy zaawansowani w wyszukiwania wyrażenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3378a554a9e576bde011a70916c48597218bb512
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operatory logiczne i zaawansowanego w wyrażeniach wyszukiwania
Operatory logiczne i operatory wyszukiwania zaawansowanego umożliwia wyszukiwanie zawartości pomocy w Podglądzie pomocy.

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
|Termin w tytuł artykułu|Nazwa:|title: binaryreader|Tematy zawierające "binaryreader" w ich tytułów.|  
|Termin w przykładzie kodu|Kod:|Kod: readdouble|Tematy zawierające "readdouble" w przykładzie kodu.|  
|Termin w przykładzie określonego języka programowania|Kod: vb:|Kod: vb:string|Tematy zawierające "string" w przykładzie kodu języka Visual Basic.|  
|Artykuł, w którym jest skojarzony ze słowem kluczowym określonego indeksu|słowa kluczowe:|słowo kluczowe: readbyte|Tematy, które są skojarzone ze słowem kluczowym "readbyte" indeksu.|  

> [!IMPORTANT]
> Należy wprowadzić operatory wyszukiwania zaawansowanego z dwukropkiem końcowego i nie pośredniczące spację przed dwukropkiem dla aparatu wyszukiwania rozpoznać ich.    

### <a name="programming-languages-for-code-examples"></a>Języki programowania, przykłady kodu
Można użyć **kodu:** operatora, aby znaleźć zawartości o wielu języków programowania. Aby przywrócić przykłady dla określonego języka programowania, użyj jednej z następujących wartości język programowania:  

|Język programowania|Składnia poleceń wyszukiwania — operator|  
|--------------------|---------|  
|Visual Basic|Kod: vb<br/>Kod: języka Visual Basic|  
|C#|Kod: c#<br/>Kod: csharp|  
|C++|Kod: cpp<br/>Kod: c ++<br/>Kod: cplusplus|  
|F#|Kod: f #<br/>Kod: języka fsharp|  
|JavaScript|Kod: javascript<br/>Kod: js|  
|XAML|Kod: xaml|

> [!NOTE]
> **Kodu:** operator znajduje tylko zawartości oznaczonej z etykietą języka programowania, w przeciwieństwie do zawartości, ogólnie oznaczony jako kod. 
  
## <a name="see"></a>Zobacz 
[Porady: wyszukiwanie tematów](how-to-search-for-topics.md)  
[Podgląd Pomocy firmy Microsoft](microsoft-help-viewer.md)