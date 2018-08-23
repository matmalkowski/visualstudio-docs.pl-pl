---
title: 'Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5089ff81121e9390968fe7e3900eb28cededc27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631754"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](https://docs.microsoft.com/visualstudio/designers/how-to-export-a-texture-that-has-premultiplied-alpha).  
  
Potok zawartości obrazu może generować wstępnie przemnożone tekstury alfa z obrazu źródłowego. Mogą to być łatwiejszy w obsłudze i bardziej niezawodne niż tekstury, które nie zawierają wstępnie przemnożonego kanału alfa.  
  
 Ten dokument przedstawia te działania:  
  
-   Konfigurowanie obrazu źródłowego, który ma być przetwarzana przez potok zawartości obrazu.  
  
-   Konfigurowanie potoku zawartości obrazu tak, aby generować wstępnie przemnożonego kanału alfa.  
  
## <a name="premultiplied-alpha"></a>Wstępnie przemnożony kanał alfa  
 Wstępnie przemnożony kanał alfa oferuje więcej korzyści niż konwencjonalny, inne niż wstępnie przemnożony kanał alfa, ponieważ lepiej przedstawia rzeczywiste interakcje światła z fizycznymi materiałami przez oddzielenie wkładu koloru teksela (koloru, który teksel dodaje do sceny) od jego przezroczystości (ilość podstawowego koloru, który przepuszcza). Zalety korzystania z wstępnie przemnożonego kanału alfa, należą:  
  
-   Mieszanie z wstępnie przemnożonego kanału alfa jest operacją asocjacyjną; wynik mieszania wielu półprzezroczystych tekstur jest taki sam, niezależnie od kolejności, w jakiej tekstury są mieszane.  
  
-   Ze względu na charakter zespolony z wstępnie przemnożonego kanału alfa renderowanie przebiegu wielu obiektów przezroczystych jest uproszczone.  
  
-   Za pomocą wstępnie przemnożonego kanału alfa, zarówno czyste Mieszanie dodatków (przez ustawienie alfa na zero), jak i liniowo interpolowane mieszania można osiągnąć jednocześnie. Na przykład w systemie cząstek zmieszana addytywnie cząstka może stać się przezroczystą cząstką dymu, która jest zmieszana przy użyciu interpolacji liniowej. Bez wstępnie przemnożonego kanału alfa trzeba rysować cząsteczki pożaru oddzielnie od cząsteczek dymu i modyfikować stan renderowania między wywołaniami rysowania.  
  
-   Kompresować tekstury, które używają wstępnie przemnożonego kanału alfa, z wyższą jakością niż te, które nie i nie wykazują odbarwionych krawędzi — lub "efektu halo" — będących wynikiem mieszania tekstur, które nie używają wstępnie przemnożonego kanału alfa.  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Aby utworzyć tekstury wykorzystującej wstępnie przemnożony kanał alfa  
  
1.  Rozpocznij od podstawowej tekstury. Załaduj istniejący pliku obrazu lub utwórz je, zgodnie z opisem w [porady: tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md).  
  
2.  Skonfigurować pliku tekstury, jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku tekstury, a następnie wybierz **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potok zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **Wyłącz z kompilacji** ustawiono **nie**, a następnie wybierz  **Zastosuj** przycisku. **Potok zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.  
  
3.  Konfigurowanie potoku zawartości obrazu, aby generować wstępnie przemnożonego kanału alfa. Na **właściwości konfiguracji**, **potok zawartości obrazu**, **ogólne** ustaw **przekonwertować wstępnie przemnożonego alfa format** Właściwość **tak (/ generatepremultipliedalpha)**.  
  
4.  Wybierz **OK** przycisku.  
  
 Podczas budowania projektu potok zawartości obrazów konwertuje obraz źródłowy z formatu roboczego do formatu wyjściowego, który określiłeś, obejmuje to konwersję obrazu do wstępnie przemnożonego kanału alfa formatu — a wynik jest kopiowany do wyjściowego projektu katalog.



