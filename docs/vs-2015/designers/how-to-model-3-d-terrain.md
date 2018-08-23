---
title: 'Instrukcje: modelowanie terenu 3D | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93bce3336a4ccb8731730616d36191fdf83c5241
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690848"
---
# <a name="how-to-model-3-d-terrain"></a>Porady: model terenu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [instrukcje: modelowanie terenu 3D](https://docs.microsoft.com/visualstudio/designers/how-to-model-3-d-terrain).  
  
Ten dokument przedstawia sposób tworzenia modelu terenu 3D za pomocą edytora modelu.  
  
 Ten dokument przedstawia te działania:  
  
-   Dodawanie obiektów do sceny  
  
-   Zaznaczanie twarzy i punktów  
  
-   Opcje przekształcania  
  
-   Za pomocą **Podziel pierwszy plan** narzędzia  
  
-   Ramek na powierzchnię obiektu  
  
## <a name="creating-a-3-d-terrain-model"></a>Tworzenie modelu terenu 3D  
 Możesz utworzyć terenu 3D podpodział płaszczyzny zapewnienie dodatkowych twarzy, a następnie manipulowanie ich wierzchołki, aby tworzyć interesujące funkcje terenu.  
  
 Gdy skończysz, model powinien wyglądać następująco:  
  
 ![3&#45;sceny D, pokazujący model terenu](../designers/media/digit-terrain-model.png "cyfrę terenu modelu")  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>Aby utworzyć model terenu 3D  
  
1.  Tworzenie modelu 3-D chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modelu do swojego projektu, zobacz sekcję pierwsze kroki w [edytora modelu](../designers/model-editor.md).  
  
2.  Dodaj płaszczyznę do sceny. W **przybornika**w obszarze **kształty**, wybierz opcję **płaszczyzny** i przenieś go do powierzchni projektowej.  
  
    > [!TIP]
    >  Aby ułatwić obiektu płaszczyzny chcesz pracować, można ramki go na powierzchnię. W **wybierz** tryb, wybierz obiekt płaszczyzny, a następnie na pasku narzędzi edytora modelu, wybierz **obiekt w ramce** przycisku.  
  
3.  Wprowadź trybu wyboru pierwszego planu. Na pasku narzędzi edytora modelu wybierz **wybierz krój**.  
  
4.  Należy podzielić płaszczyzny. W przypadku trybu wyboru pierwszego planu wybierz płaszczyzny raz go uaktywnić dla zaznaczenia, a następnie wybierz ją ponownie, aby wybrać jej tylko twarzy. Na pasku narzędzi edytora modelu wybierz **Podziel pierwszy plan**. Spowoduje to dodanie nowe wierzchołki płaszczyzny i podziel go na partycje równej wielkości.  
  
5.  Utwórz więcej segmentami. Przy wciąż zaznaczonym nowe powierzchnie, wybierz polecenie **Podziel pierwszy plan** dwa razy. Spowoduje to utworzenie w sumie 64 twarzy. Tworząc więcej segmentami, można nadać terenu jeszcze więcej szczegółów.  
  
6.  Przejść do trybu wyboru punktu. Na pasku narzędzi edytora modelu wybierz **wybierz punkt**.  
  
7.  Zmodyfikuj punkt, aby utworzyć funkcję terenu. W trybie wyboru punktu, należy wybrać jeden z punktów, a następnie na pasku narzędzi edytora modelu wybierz **Translate** narzędzia. Pole, który reprezentuje punkt jest wyświetlany na powierzchni projektowej. Aby przenieść pole i tym samym zmodyfikować wysokość punktu, użyj zieloną strzałkę. Powtórz ten krok dla różnych punktów w celu utworzenia interesujące funkcje terenu.  
  
    > [!TIP]
    >  Możesz wybrać kilka punktów jednocześnie z ich w jednolity sposób.  
  
 Model terenu jest kompletny. Poniżej przedstawiono końcowego modelu ponownie przy użyciu cieniowanie Phong zastosowane:  
  
 ![3&#45;sceny D, pokazujący model terenu](../designers/media/digit-terrain-model.png "cyfrę terenu modelu")  
  
 Ten model terenu można użyć, aby zademonstrować efekt modułu cieniującego gradientu, który jest opisany w [porady: tworzenie cieniowania gradientu geometrycznego](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor modelu](../designers/model-editor.md)



