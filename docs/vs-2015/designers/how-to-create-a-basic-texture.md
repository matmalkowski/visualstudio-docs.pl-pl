---
title: 'Porady: tworzenie tekstury podstawowej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1fd26ddef0e4076603ef22589bcbd59e472bf9d9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681291"
---
# <a name="how-to-create-a-basic-texture"></a>Porady: tworzenie tekstury podstawowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: tworzenie tekstury podstawowej](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-texture).  
  
W tym dokumencie pokazano, jak utworzyć teksturę podstawową za pomocą edytora obrazu.  
  
 Ten dokument przedstawia te działania:  
  
-   Ustawianie rozmiaru tekstury  
  
-   Ustawianie pierwszego planu i tła kolorów  
  
-   Za pomocą kanału alfa (przezroczystości)  
  
-   Za pomocą **wypełnienia** i **elipsy** narzędzia  
  
-   Ustawianie właściwości narzędzia  
  
## <a name="creating-a-basic-texture"></a>Tworzenie tekstury podstawowej  
 Edytor obrazu do tworzenia i modyfikowania obrazów i tekstur dla Twojej gry lub aplikacji.  
  
 Poniższe kroki pokazują jak utworzyć teksturę, która reprezentuje element docelowy "bullseye". Gdy skończysz, Tekstura powinno wyglądać jak na poniższym obrazie. Aby zademonstrować lepiej przezroczystości tekstury, edytora obrazów skonfigurowano do korzystania z wzorca zielony, szachownicą, aby go wyświetlić.  
  
 ![Docelowy "Bullseye" z przezroczystością na zielono](../designers/media/digit-bullseye-texture-in-editor.png "cyfry-Bullseye-tekstury-edytora")  
  
 Przed rozpoczęciem upewnij się, że **właściwości** zostanie wyświetlone okno. Możesz użyć **właściwości** okna, aby ustawić rozmiar obrazu, zmień właściwości narzędzia i określić kolory, podczas pracy.  
  
#### <a name="to-create-a-bullseye-target-texture"></a>Aby utworzyć teksturę target "bullseye"  
  
1.  Utwórz teksturę do pracy. Aby uzyskać informacje dotyczące sposobu dodawania tekstury do projektu, zobacz sekcję pierwsze kroki w [edytora obrazów](../designers/image-editor.md).  
  
2.  Ustaw wielkość obrazu do 512 x 512 pikseli. W **właściwości** okna, ustaw wartości **szerokość** i **wysokość** właściwości `512`.  
  
3.  Na pasku narzędzi edytora obrazów, wybierz **wypełnienia** narzędzia. **Właściwości** oknie zostaną wyświetlone właściwości **wypełnienia** narzędzie wraz z właściwości obrazu.  
  
4.  Ustaw kolor pierwszego planu, aby całkowicie przezroczysty czarny. W **właściwości** okna w **kolory** grupie właściwości, wybierz opcję **pierwszego planu**. Ustaw wartości **R**, **G**, **B**, i **A** właściwości obok selektor kolorów do `0`.  
  
5.  Na pasku narzędzi edytora obrazów, wybierz **wypełnienia** narzędzia, a następnie naciśnij i przytrzymaj klawisz Shift i wybierz dowolny punkt na obrazie. Przy użyciu klawisza Shift powoduje, że wartość alfa odpowiadającą koloru wypełnienia zastąpić kolor obrazu. w przeciwnym razie wartość alfa odpowiadającą umożliwia mieszanie kolor wypełnienia wraz z kolorów na obrazie.  
  
    > [!IMPORTANT]
    >  Ten krok, wraz z wybór koloru w poprzednim kroku gwarantuje, że podstawowy obraz jest gotowy do "bullseye" docelową teksturę będzie rysowania. Gdy obraz jest wypełniany przezroczysty czarny — i dlatego jest czarny, obramowania docelowy — nie będzie żadnych artefaktów wygładzania wokół obiektu docelowego.  
  
6.  Na pasku narzędzi edytora obrazów, wybierz **elipsy** narzędzia.  
  
7.  Ustaw kolor pierwszego planu na całkowicie nieprzezroczysty czarny. Ustaw wartości **R**, **G**, i **B** właściwości `0` i wartość **A** właściwość `255`.  
  
8.  Na biały całkowicie nieprzezroczysty, ustaw kolor tła. W **właściwości** okna w **kolory** grupie właściwości, wybierz opcję **tła**. Ustaw wartości **R**, **G**, **B**, i **A** właściwości `255`.  
  
9. Ustaw szerokość konturu elipsy. W **właściwości** okna w **wygląd** grupy właściwość, ustaw wartość **szerokość** właściwość `8`.  
  
10. Upewnij się, że wygładzanie jest włączony. W **właściwości** okna w **wygląd** właściwości grupy, upewnij się, że **wygładzanie** właściwość jest ustawiona.  
  
11. Za pomocą **elipsy** narzędzie, narysuj okręg z współrzędnych pikseli `(3, 3)` do współrzędnej pikseli `(508, 508)`. Rysowanie okręgów więcej łatwo możesz można naciśnij i przytrzymaj klawisz Shift podczas rysowania.  
  
    > [!NOTE]
    >  Współrzędne bieżącej lokalizacji wskaźnika w pikselach są wyświetlane na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pasek stanu.  
  
12. Umożliwia zmianę koloru tła. Ustaw **R** do `44`, **G** do `165`, **B** do `211`, i **A** do `255`.  
  
13. Rysowanie okrąg inny od współrzędnych pikseli `(64, 64)` do współrzędnej pikseli `(448, 448)`.  
  
14. Zmienić kolor tła na całkowicie nieprzezroczysty biały. Ustaw **R**, **G**, **B**, i **A** do `255`.  
  
15. Rysowanie okrąg inny od współrzędnych pikseli `(128, 128)` do współrzędnej pikseli `(384, 384)`.  
  
16. Umożliwia zmianę koloru tła. Ustaw **R** do `255`, **G** i **B** do `64`, i **A** do `255`.  
  
17. Rysowanie okrąg inny od współrzędnych pikseli `(192, 192)` do współrzędnej pikseli `(320, 320)`.  
  
 Docelową teksturę "bullseye" zostało zakończone. Oto finalnego obrazu, przedstawiono przezroczystości.  
  
 ![Ukończone "bullseye" docelowej tekstury](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")  
  
 Kolejnym krokiem może wygenerować poziomy MIP dla tej tekstury. Aby uzyskać informacje, zobacz [instrukcje: tworzenie i poziomy MIP Modyfikuj](../designers/how-to-create-and-modify-mip-levels.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor obrazów](../designers/image-editor.md)



