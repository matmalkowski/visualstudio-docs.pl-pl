---
title: 'Porady: modyfikowanie punktu obrotu modelu 3-D | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19864f98df2b10d06362969d82752b68b6ba26c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42691722"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Porady: modyfikowanie punktu obrotu modelu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: modyfikowanie punktu obrotu modelu 3-D](https://docs.microsoft.com/visualstudio/designers/how-to-modify-the-pivot-point-of-a-3-d-model).  
  
W tym dokumencie przedstawiono sposób używania edytora modelu do modyfikowania *punkt obrotu* modelu 3-D. Punkt obrotu jest punktem w miejscu, definiująca środek matematyczne obiektu dla obrotu i skalowania.  
  
 W tym dokumencie przedstawiono to działanie:  
  
-   Modyfikowanie punktu obrotu obiektu  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Modyfikowanie punktu obrotu modelu 3-D  
 Pochodzenie modelu 3-D można zmienić, modyfikując jego punktu obrotu.  
  
 Upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>Aby zmodyfikować punktu obrotu modelu 3-D  
  
1.  Zacznij od istniejącego modelu 3-w, takiego jak opisany w [porady: Tworzenie podstawowego modelu 3-D](../designers/how-to-create-a-basic-3-d-model.md).  
  
2.  Wprowadź tryb obrotu. Na **tryb edytora modelu** narzędzi, wybierz **tryb obrotu** przycisk, aby uaktywnić tryb obrotu. Zostanie wyświetlone okno z całym **tryb obrotu** przycisk, aby wskazać, że edytor modelu jest teraz tryb obrotu. W tryb obrotu operacji, takich jak tłumaczenia wpływają na punkt obrotu obiektu zamiast struktury obiektów w przestrzeni świata.  
  
3.  Modyfikowanie punktu obrotu obiektu. W **wybierz** tryb, wybierz obiekt, a następnie na **przeglądarka modelu** narzędzi, wybierz **Translate** narzędzia. Pole, który reprezentuje punkt obrotu jest wyświetlany na powierzchni projektowej. Przenieś pole, aby zmodyfikować punkt obrotu obiektu.  
  
     Przenosząc pole, możesz przenieść punkt obrotu we wszystkich trzech wymiarach. Do translacji punktu obrotu wzdłuż osi, Przenieś strzałkę, która odnosi się do tej osi. Strzałki i pole Zmień kolor żółty, aby wskazać osi, który jest zależna od tłumaczenia.  
  
     Można również określić przy użyciu punktu obrotu **Translacja punktu centralnego** właściwość **właściwości** okna.  
  
    > [!TIP]
    >  Aby wyświetlić efekt nowego punktu obrotu, obracanie obiektu. Aby obrócić go, należy użyć **Obróć** narzędzia lub zmodyfikować **obrotu** właściwości.  
  
 Oto modelu, który ma punkt obrotu zmodyfikowane:  
  
 ![Model DOM, zawierający punkt obrotu zmodyfikowane](../designers/media/digit-modified-model.png "cyfrę modyfikacji — Model")  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie podstawowego modelu 3-D](../designers/how-to-create-a-basic-3-d-model.md)   
 [Edytor modelu](../designers/model-editor.md)



