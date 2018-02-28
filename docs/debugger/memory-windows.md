---
title: "Wyświetl pamięci dla zmiennych w debugerze | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 96a4dc22f4f5c96d3dd9d40a565c2656ffe6e283
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger"></a>Używanie okien pamięci w debugerze programu Visual Studio
**Pamięci** okna zapewnia wgląd do obszaru pamięci, która jest używana przez aplikację. **Czujki** okna, **QuickWatch** okno dialogowe **automatycznych** okno i **zmiennych lokalnych** okna Pokaż zawartość zmiennych, które są przechowywane w określonych lokalizacjach w pamięci. Ale **pamięci** okno zawiera obraz na dużą skalę. Ten widok może być wygodną metodą badanie dużej części danych (buforów lub dużych ciągów, na przykład), które nie są wyświetlane poprawnie w innych oknach. Jednak **pamięci** okno nie jest ograniczona do wyświetlania danych. Wyświetla wszystkie elementy w obszarze pamięci, czy zawartość jest danych, kodu lub losowych bity pamięci w pamięci nieprzypisane.  
  
 **Pamięci** okno jest dostępne tylko wtedy, gdy w włączone jest debugowanie poziomie adresu **opcje** okno dialogowe **debugowanie** węzła. **Pamięci** okno nie jest dostępna dla skryptu lub SQL, które języki, które nie rozpoznają pojęcie pamięci.  
  
## <a name="opening-a-memory-window"></a>Otwieranie okna pamięci  
  
#### <a name="to-open-a-memory-window"></a>Aby otworzyć okno pamięci  
  
1.  Rozpocznij debugowanie, jeśli nie jesteś już w trybie debugowania.  
  
2.  W **debugowania** menu wskaż **Windows**. Następnie wskaż **pamięci** , a następnie kliknij przycisk **1 pamięci**, **2 pamięci**, **3 pamięci**, lub **4 pamięci**. (Wersje niższe [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mieć tylko jeden **pamięci** okna. Jeśli używasz jednego z tych wersji, wystarczy kliknąć **pamięci**.)  
  
## <a name="paging-in-the-memory-window"></a>Stronicowanie w oknie pamięci  
 **Pamięci** okno ma pionowy pasek przewijania, który działa w sposób niestandardowe. Przestrzeń adresowa nowoczesnych komputera jest bardzo duży, a można łatwo uzyskać utracie Przechwytywanie przycisku przewijania suwaka i przeciągając go do losowo wybranej lokalizacji. Z tego powodu uchwytu jest "obciążony" i zawsze pozostaje w Centrum pasek przewijania. W aplikacjach kodu natywnego może strona w górę lub w dół, ale nie Przewiń o za darmo.  
  
 Wyższy adresów pamięci są wyświetlane w dolnej części okna. Aby wyświetlić adres wyższej, przewiń w dół, nie długości.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Stronę w górę lub w dół w pamięci  
  
1.  Aby stronę w dół (przejście do wyższych adres pamięci), kliknij w obszarze przycisku przewijania w pionowy pasek przewijania.  
  
2.  Stronę w górę (przejście do dolnej adres pamięci), kliknij powyżej stronie przycisku suwaka pionowy pasek przewijania.  
  
## <a name="selecting-a-memory-location"></a>Wybieranie lokalizacji w pamięci  
 Jeśli chcesz przechodzić bezpośrednio do wybranej lokalizacji w pamięci, możesz to zrobić przy użyciu operacji przeciągania i upuszczania lub edytując wartości w **adres** pole. **Adres** w polu można nie tylko wartości liczbowe, ale także wyrażeń określających adresów. Domyślnie **pamięci** traktuje okna **adres** wyrażenie jako wyrażenie na żywo jest ponownie oceniane, gdy program jest wykonywana. Wyrażenia na żywo może być bardzo przydatne. Na przykład można je wyświetlić pamięci, która jest korzystały wskaźnik.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Aby wybrać lokalizację pamięci przez przeciąganie i upuszczanie  
  
1.  W dowolnym oknie Wybierz pamięci adres lub wskaźnik zmienna, która zawiera adres pamięci.  
  
2.  Przeciągnij adres lub wskaźnik do **pamięci** okna.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Aby wybrać lokalizację pamięci, edytując  
  
1.  W **pamięci** wybierz **adres** pole.  
  
2.  Wpisz lub wklej adres, który chcesz wyświetlić, a następnie naciśnij klawisz **ENTER**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Zmienia sposób Wyświetla informacje okno pamięci  
 Można dostosować sposób **pamięci** okno zawiera zawartość pamięci. Domyślnie zawartość pamięci są wyświetlane jako jedna bajtowych liczb całkowitych w formacie szesnastkowym, a liczba kolumn jest ustalany automatycznie przez bieżący szerokość okna.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Aby zmienić format zawartości pamięci  
  
1.  Kliknij prawym przyciskiem myszy **pamięci** okna.  
  
2.  Wybierz format, który ma.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Aby zmienić liczbę kolumn w oknie pamięci  
  
1.  Na pasku narzędzi u góry **pamięci** okna, zlokalizuj **kolumn** listy.  
  
2.  W **kolumn** , wybierz liczbę kolumn, które chcesz wyświetlić, lub wybierz na liście **automatycznie** automatycznego dostosowania do dopasowania do szerokości okna.  
  
 Jeśli nie chcesz, aby zawartość **pamięci** wykonuje okno, aby zmienić jako programu, można wyłączyć Obliczanie wyrażenia na żywo.  
  
#### <a name="to-toggle-live-evaluation"></a>Aby przełączyć oceny na żywo  
  
1.  Kliknij prawym przyciskiem myszy **pamięci** okna.  
  
2.  W menu skrótów kliknij **obliczyć ponownie automatycznie**.  
  
     Jeśli oceny na żywo jest włączona, zostanie wybrana opcja, a jej kliknięcie spowoduje wyłączenie oceny na żywo. Jeśli oceny na żywo jest wyłączony, nie wybrano opcji i klikając go włącza oceny na żywo.  
  
 Można ukrywać lub wyświetlać element toolbar na górze **pamięci** okna. Nie będzie mieć dostęp do adresu pola lub innych narzędzi, tak długo, jak pasek narzędzi jest ukryty.  
  
#### <a name="to-toggle-the-toolbar"></a>Aby przełączyć na pasku narzędzi  
  
1.  Kliknij prawym przyciskiem myszy **pamięci** okna.  
  
2.  W menu skrótów kliknij **Pokaż pasek narzędzi**.  
  
     Pasek narzędzi pojawi się lub znika, w zależności od jego poprzedniego stanu.  
  
## <a name="following-a-pointer-through-memory"></a>Śledzenie wskaźnika za pośrednictwem pamięci  
 W aplikacjach kodu natywnego nazw rejestru można użyć jako wyrażenia na żywo. Na przykład umożliwia wskaźnik stosu postępuj zgodnie ze stosu.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Do wykonania wskaźnik do pamięci  
  
1.  W **pamięci** okna **adres** wpisz wyrażenie wskaźnika. Zmienna wskaźnika musi być w bieżącym zakresie. W zależności od języka może być konieczne odwołania do niego.  
  
2.  Naciśnij klawisz **ENTER**.  
  
     Teraz, używając polecenia wykonywania takich jak **krok**, automatycznie zmieni adres pamięci, która jest wyświetlana jako wskaźnika zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)