---
redirect_url: /visualstudio/ide/how-to-search-for-topics
ms.openlocfilehash: a66c168ca81b22c32fc05afddd01266950791d1e
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
Tytuł: "porady dotyczące wyszukiwania pełnotekstowego | Ms.custom dokumentacja firmy Microsoft":" "ms.date: ms.reviewer"2016-11-04":" "ms.suite:" "ms.technology: 
  - ms.tgt_pltfrm "vs-help viewer": "" ms.topic: "artykuł" f1_keywords: 
  - helpviewer_keywords "hv_search": 
  - "Help Viewer, wskazówki dotyczące wyszukiwania pełnotekstowego"
  - "wyszukiwanie pełnotekstowe porady [podglądu pomocy]" ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b caps.latest.revision: 13 Autor: ms.author "gewarren": "gewarren" Menedżer: ghogen
---
# <a name="full-text-search-tips"></a>Porady dotyczące wyszukiwania pełnotekstowego
Jednym z bardziej użyteczne metody znajdowanie informacji pomocy jest wykonując wyszukiwania pełnotekstowego. Można utworzyć więcej docelowe wyszukiwania, które zwraca tylko tymi tematami, które są potrzebne, jeśli znasz wpływ Składnia kwerendy. Składnia zawiera znaki specjalne, wyrazy zastrzeżone i filtry. Ten temat zawiera wskazówki, procedury i składni szczegółowe informacje ułatwiające lepsze jednostki zapytań.
  
### <a name="general-guidelines"></a>Ogólne wskazówki  
W poniższej tabeli przedstawiono niektóre podstawowe zasady i wytyczne dotyczące tworzenia zapytania wyszukiwania w Pomocy.  
  
|Składnia|Opis|  
|------------|-----------------|  
|Uwzględniana wielkość liter|Wyszukiwanie nie jest rozróżniana wielkość liter. Tworzenie kryteriów wyszukiwania przy użyciu wielkich i małych znaków. Na przykład "OLE" i "ole" zwracają takie same wyniki.|  
|Kombinacji znaków|Nie można przeszukiwać tylko dla poszczególnych litery (a – z) i cyfr (0 – 9). Jeśli spróbujesz wyszukiwania dla niektórych wyrazów zastrzeżonych, takich jak "i", "od" i "z" zostanie zignorowany. Aby uzyskać więcej informacji, zobacz "Wyrazy ignorowany podczas wyszukiwania (wyrazy)" w dalszej części tego tematu.|  
|Kolejność obliczania|Zapytania wyszukiwania są oceniane od lewej do prawej.|  
  
### <a name="search-syntax"></a>Wyszukiwanie składni  
 Jeśli określisz ciąg wyszukiwania, która zawiera wiele słów, takich jak "word1 word2", ten ciąg jest odpowiednikiem wpisując "word1 word2 i", która zwraca tylko tematy zawierające wszystkie poszczególnych wyrazów w ciągu wyszukiwania.  
  
> [!IMPORTANT]
> - Wyszukiwania fraz nie są obsługiwane. Jeśli określisz więcej niż jedno słowo w wyszukiwanym ciągu zwrócony tematy będzie zawierać wszystkie słowa, które można określić, ale niekoniecznie dokładnej frazy określony.  
> - Operatory logiczne umożliwia określenie relacji między wyrazami Twojej frazę wyszukiwania. Można dołączyć operatorów logicznych, takich jak AND, OR, NOT i w pobliżu, w celu przeprowadzenia dalszej Uściślij kryteria wyszukiwania. Na przykład w przypadku wyszukiwania "deklarowania Unii w pobliżu" wyniki wyszukiwania zawierają tematy zawierające słowa "deklarowanie" i "union" ma więcej niż kilka wyrazów od siebie nawzajem. Aby uzyskać więcej informacji, zobacz [operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filtry  
 Wyniki wyszukiwania można bardziej ograniczyć przy użyciu operatorów wyszukiwania zaawansowanego. Pomoc zawiera trzy kategorie, które umożliwiają filtrowanie wyników wyszukiwania pełnotekstowego: tytuł, kodu i słów kluczowych.
  
### <a name="ranking-of-search-results"></a>Klasyfikacja wyników wyszukiwania  
 Algorytm wyszukiwania stosuje określone kryteria, aby ułatwić rangę wyniki wyższe lub niższe wyszukiwania na liście wyników. Ogólnie rzecz biorąc:  
  
1.  Zawartość, która zawiera słów kluczowych w tytule znajduje się wyżej niż zawartość, która nie.  
  
2.  Zawartość, która zawiera słów kluczowych w pobliżu znajduje się wyżej niż zawartość, która nie.  
  
3.  Zawartość, która zawiera zwiększeniu słów wyszukiwania znajduje się wyżej niż zawartość, która ma gęstość niższe słów kluczowych.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Wyrazy ignorowane podczas wyszukiwania (wyrazy)  
 Najczęściej występujące słowa lub numery, które są nazywane wyrazy, automatycznie są ignorowane podczas wyszukiwania pełnotekstowego. Na przykład jeśli możesz wyszukać frazę "przekazywania" wyniki wyszukiwania wyświetli tematy zawierające słowo "przebiegu" ale nie "do".  
  
## <a name="see-also"></a>Zobacz także
[Lokalizowanie informacji](../ide/locate-information.md)   
[Operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md)