---
title: "Porady: wyszukiwanie tematów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ec4ec1c06d6c64a344e9e39d01c850b901534af8
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-search-for-topics"></a>Porady: wyszukiwanie tematów
Funkcja wyszukiwania pełnotekstowego zlokalizować wszystkie tematy zawierające określonego wyrazu. Można również dostosować i dostosować wyszukiwanie przy użyciu symboli wieloznacznych wyrażenia, operatorów logicznych i operatory wyszukiwania zaawansowanego.  
  
Aby otworzyć kartę Wyszukiwanie, wybierz **wyszukiwania** karty w oknie Podgląd pomocy, lub jeśli użytkownik jest użytkownikiem klawiatury, wybierz **Ctrl + E**.  
  
## <a name="to-perform-a-full-text-search"></a>Aby wykonać wyszukiwanie pełnotekstowe 
1.  W polu wyszukiwania wpisz wyraz, który ma zostać znaleziona.  
  
2.  W zapytaniu wyszukiwania określić które operatorów logicznych lub Zaawansowane wyszukiwanie do zastosowania do wyszukiwania, ile. Aby wyszukać wszystkie dostępne pomocy, nie należy używać operatorów.  
  
    > [!NOTE]
    >  W **Opcje aplikacji Viewer** okno dialogowe, można określić dodatkowe preferencje, takie jak maksymalna liczba wyników wyszukiwania do wyświetlenia w czasie i czy ma być uwzględniane zawartości w języku angielskim, jeśli ustawienia regionalne podstawowy nie jest język angielski.  
  
3.  Wybierz **Enter** klucza.  
  
     Wyszukiwanie zwraca maksymalnie 200 trafień domyślnie i wyświetla je w obszarze wyniki wyszukiwania. Informacje o dodatkowych wersji dla każdego wyniku może pojawić się w zależności od zawartości.  
  
4.  Aby wyświetlić tematu, wybierz swój tytuł z listy wyników.

## <a name="full-text-search-tips"></a>Porady dotyczące wyszukiwania pełnotekstowego
Można utworzyć więcej docelowe wyszukiwania, które zwraca tylko tymi tematami, które są potrzebne, jeśli znasz wpływ Składnia kwerendy. Składnia zawiera znaki specjalne, wyrazy zastrzeżone i filtry. Ten temat zawiera wskazówki, procedury i składni szczegółowe informacje ułatwiające lepsze jednostki zapytań.
  
### <a name="general-guidelines"></a>Ogólne wskazówki  
W poniższej tabeli przedstawiono niektóre podstawowe zasady i wytyczne dotyczące tworzenia zapytania wyszukiwania w Pomocy.  
  
|Składnia|Opis|  
|------------|-----------------|  
|Uwzględniana wielkość liter|Wyszukiwanie nie jest rozróżniana wielkość liter. Tworzenie kryteriów wyszukiwania przy użyciu wielkich i małych znaków. Na przykład "OLE" i "ole" zwracają takie same wyniki.|  
|Kombinacji znaków|Nie można przeszukiwać tylko dla poszczególnych litery (a – z) i cyfr (0 – 9). Jeśli spróbujesz wyszukiwania dla niektórych wyrazów zastrzeżonych, takich jak "i", "od" i "z" zostanie zignorowany. Aby uzyskać więcej informacji, zobacz [wyrazy ignorowane w wyszukiwaniach](#stopwords) dalszej części tego tematu.|  
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
  
### <a name="stopwords">Wyrazy ignorowane podczas wyszukiwania (wyrazy)</a>
Najczęściej występujące słowa lub numery, które są nazywane wyrazy, automatycznie są ignorowane podczas wyszukiwania pełnotekstowego. Na przykład jeśli możesz wyszukać frazę "przekazywania" wyniki wyszukiwania wyświetli tematy zawierające słowo "przebiegu" ale nie "do".  
  
## <a name="see-also"></a>Zobacz także
[Operatory logiczne i zaawansowane](../ide/logical-operators-in-search-expressions.md)  
[Porady: znajdowanie tematów w indeksie](../ide/how-to-find-topics-in-the-index.md)  
[Porady: znajdowanie tematów w spisie treści](../ide/how-to-find-topics-in-the-table-of-contents.md)  
[Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)