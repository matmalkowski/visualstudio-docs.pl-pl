---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
Tytuł: "zaawansowani operatorzy wyszukiwania w wyrażeniach wyszukiwania | Ms.custom dokumentacja firmy Microsoft":" "ms.date: ms.reviewer"2017-06/02":" "ms.suite:" "ms.technology: 
  - ms.tgt_pltfrm "vs-help viewer": "" ms.topic: "artykuł" helpviewer_keywords: 
  - "Help Viewer, wyszukiwanie słów kluczowych"
  - "Help Viewer, wyszukiwanie kodu"
  - "Help Viewer, wyszukiwanie kodu według języka programowania"
  - "Help Viewer, wyszukiwanie tytułów"
  - "Wyszukiwanie kodu [podglądu pomocy]"
  - "Wyszukiwanie tytuły [podglądu pomocy]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 Autor: ms.author "gewarren": "gewarren" Menedżer: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatory wyszukiwania zaawansowanego w wyrażeniach wyszukiwania
Przy użyciu operatorów wyszukiwania zaawansowanego w Podglądzie pomocy, można uściślić wyszukiwanie zawartości, określając where w temacie, aby wyszukać terminu wyszukiwania. W poniższej tabeli opisano cztery operatory wyszukiwania zaawansowanego dostępne.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|  
|-------------------|---------|-------------|------------|  
|Termin w tytule tematu|Nazwa:|title: binaryreader|Tematy zawierające "binaryreader" w ich tytułów.|  
|Termin w przykładzie kodu|Kod:|Kod: readdouble|Tematy zawierające "readdouble" w przykładzie kodu.|  
|Termin w przykładzie określonego języka programowania|Kod: vb:|Kod: vb:string|Tematy zawierające "string" w przykładzie kodu języka Visual Basic.|  
|Temat, który jest skojarzony ze słowem kluczowym określonego indeksu|słowa kluczowe:|słowo kluczowe: readbyte|Tematy, które są skojarzone ze słowem kluczowym "readbyte" indeksu.|  

> [!WARNING]
>  Należy wprowadzić operatory wyszukiwania zaawansowanego z dwukropkiem końcowego i nie pośredniczące spację przed dwukropkiem dla aparatu wyszukiwania rozpoznać ich.    

## <a name="programming-languages-for-code-examples"></a>Języki programowania, przykłady kodu
Można użyć kodu: operator można znaleźć zawartości o wielu języków programowania, ale zwraca wyniki tylko dla zawartości, która jest oznaczone etykietą języka programowania. Aby przywrócić przykłady dla określonych język programowania, użyj jednej z następujących wartości język programowania:  

|Język programowania|Składnia poleceń wyszukiwania — operator|  
|--------------------|---------|  
|Visual Basic|Kod: vb<br/>Kod: języka Visual Basic|  
|C#|Kod: c#<br/>Kod: csharp|  
|C++|Kod: cpp<br/>Kod: c ++<br/>Kod: cplusplus|  
|F#|Kod: f #<br/>Kod: języka fsharp|  
|JavaScript|Kod: javascript<br/>Kod: js|  
|XAML|Kod: xaml|
