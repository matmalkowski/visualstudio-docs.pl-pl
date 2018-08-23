---
title: Szybkie wykonywanie akcji dzięki żarówkom | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9cd00bf08a48c1763ab72e6b30579e81e870c1a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630362"
---
# <a name="perform-quick-actions-with-light-bulbs"></a>Szybkie wykonywanie akcji dzięki żarówkom
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [dokumentacja programu Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Ikony żarówek są nową funkcją produktywność w programie Visual Studio 2015. Są one ikon wyświetlanych w edytorze programu Visual Studio i można kliknąć, aby wykonać szybkie akcje w tym refaktoryzacji naprawienie błędów. Żarówki przenieść naprawianie błędów i refaktoryzacji pomocy w pojedynczy punkt centralny często prawym przyciskiem myszy w wierszu, gdzie wpisujesz.  
  
 ![Ikona mała ikona żarówki](../ide/media/vs2015-lightbulbsmall.png "VS2015_LightBulbSmall")  
  
 W języku C# i Visual Basic zobaczysz, że żarówki, jeśli czerwona fala i programu Visual Studio zawiera sugestię dotyczącą sposobu rozwiązania problemu. Na przykład w przypadku błędu wskazywanym przez czerwona fala żarówka pojawi się po poprawki są dostępne dla tego błędu. W języku C++ po dodaniu nowej funkcji do pliku nagłówka, zobaczysz żarówki, która umożliwia tworzenie szkieletu stosowania tej funkcji. W dowolnym języku innych firm może zapewnić Diagnostyka niestandardowa i sugestie, na przykład jako część zestawu SDK i żarówki programu Visual Studio zostanie podświetlony, zależnie od tych zasad.  
  
## <a name="to-see-a-light-bulb"></a>Aby wyświetlić żarówka  
  
1.  W wielu przypadkach żarówki spontanicznie są wyświetlane po umieszczeniu wskaźnika myszy punkcie błąd lub w lewy margines edytora, gdy Przesuń karetkę do wiersza, który zawiera błąd. Gdy pojawi się czerwona fala, możesz umieścić kursor go, aby wyświetlić żarówki. Może również spowodować żarówki wyświetlić, gdy używasz myszy lub klawiatury, aby przejść do dowolnego miejsca w wierszu miejsce wystąpienia problemu.  
  
2.  Naciśnij klawisz **Ctrl +.** gdziekolwiek w wierszu wywołuje żarówki i przejść bezpośrednio do listy potencjalne rozwiązania.  
  
 ![Ikona żarówki z kursor](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")  
  
## <a name="to-see-potential-fixes"></a>Aby wyświetlić potencjalne rozwiązania  
 Kliknij strzałkę w dół lub potencjalne Pokaż poprawki łącze, aby wyświetlić listę szybkie akcje, które można wykonać żarówki.  
  
 ![Ikona żarówki rozwinięte](../ide/media/vs2015-lightbulb-hover-expanded.png "VS2015_LightBulb_hover_expanded")  
  
## <a name="to-do-a-refactoring"></a>Aby zrobić, Refaktoryzacja  
 Można wykonywać operacji refaktoryzacji, klikając prawym przyciskiem myszy, aby wyświetlić menu kontekstowe, ale można również nacisnąć klawisze Ctrl +. Aby wyświetlić opcje refaktoryzacji. Na poniższej ilustracji, refaktoryzacji Wyodrębnij metodę jest oferowana po naciśnięciu klawisza Ctrl +. gdzieś w wierszu, który zawiera `Math.Abs` wywołania:  
  
 ![Ikona żarówki przedstawiający opcje refaktoryzacji](../ide/media/vs2015-lightbulbs-refactor.png "VS2015_LightBulbs_refactor")



