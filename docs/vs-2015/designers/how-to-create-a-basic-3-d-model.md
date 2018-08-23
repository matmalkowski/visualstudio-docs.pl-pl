---
title: 'Porady: Tworzenie podstawowego modelu 3-D | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf8180f13328c198131ee3d5fca3884dcd20be2c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630507"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Porady: tworzenie podstawowego modelu 3-D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Tworzenie podstawowego modelu 3-D](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-3-d-model).  
  
W tym dokumencie przedstawiono sposób używania edytora modelu do tworzenia podstawowego modelu 3-D.  
  
 Ten dokument przedstawia te działania:  
  
-   Dodawanie obiektów do sceny  
  
-   Wybieranie powierzchni i krawędzi  
  
-   Opcje przekształcania  
  
-   Za pomocą **Podziel pierwszy plan** i **wyciągnij** narzędzia  
  
-   Za pomocą **triangulacja** polecenia  
  
## <a name="creating-a-basic-3-d-model"></a>Tworzenie podstawowego modelu 3-D  
 Edytor modelu do tworzenia i modyfikowania modeli 3D i sceny gry lub aplikacji. Poniższe kroki pokazują jak utworzyć uproszczony model 3-w domu za pomocą edytora modelu. Uproszczony model może służyć jako elementu zastępczego dla końcowego artystycznych, które są nadal tworzone, jako siatkę wykrywanie kolizji lub niska Szczegóły modelu ma być używany, gdy obiekt, który reprezentuje jest zbyt daleko do korzystania z renderowania bardziej szczegółowe.  
  
 Gdy skończysz, model powinien wyglądać następująco:  
  
 ![Ukończone modelu DOM uproszczone](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Aby utworzyć uproszczony model 3-w domu  
  
1.  Tworzenie modelu 3-D chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modelu do swojego projektu, zobacz sekcję pierwsze kroki w [edytora modelu](../designers/model-editor.md).  
  
2.  Dodaj moduł do sceny. W **przybornika** okna, w obszarze **kształty**, wybierz opcję **modułu** i przenieś go do powierzchni projektowej.  
  
3.  Przełącz się do wyboru twarzy. Na pasku narzędzi edytora modelu wybierz **wybierz krój**.  
  
4.  Należy podzielić górnej części modułu. W przypadku trybu wyboru pierwszego planu wybierz moduł raz go uaktywnić dla zaznaczenia, a następnie wybierz górnej części modułu, aby zaznacz powierzchnię, najważniejsze. Na pasku narzędzi edytora modelu wybierz **Podziel pierwszy plan**. Spowoduje to dodanie nowe wierzchołki na początku modułu, który podzielić ją na cztery partycje równej wielkości.  
  
     ![Górnej części modułu zostały podzielone](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")  
  
5.  Wyciągnięcie dwóch sąsiednich boków modułu — na przykład frontonu i prawej stronie modułu. W trybu wyboru pierwszego planu wybierz moduł raz go uaktywnić dla zaznaczenia, a następnie wybierz polecenie po jednej stronie modułu. Naciśnij i przytrzymaj klawisz Control, wybierz inny boku modułu, która jest przyległa do strony, należy najpierw wybrać, a następnie na pasku narzędzi edytora modelu, wybierz **wyciągnij**.  
  
     ![Boków modułu została wyrzucane.](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")  
  
6.  Jedną z extrusions rozszerzyć. Wybierz jedną z twarzy, które właśnie, usunąć, a następnie na pasku narzędzi edytora modelu wybierz **Translate** narzędzia i Przenieś manipulator tłumaczenia w tym samym kierunku co wytłaczanie metali.  
  
     ![Dodatkowo ma zostały wyrzucane po jednej stronie modułu. ](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")  
  
7.  Przeprowadzić triangulację modelu. Na pasku narzędzi edytora modelu wybierz **zaawansowane**, **narzędzia**, **triangulacja**.  
  
8.  Utwórz dachu domu. Przełącz do trybu wyboru krawędzi, wybierając **krawędzi wybierz pozycję** na pasku narzędzi edytora modelu, a następnie wybierz moduł, aby ją uaktywnić. Naciśnij i przytrzymaj klawisz Control, podczas zaznaczania krawędzi, które przedstawiono poniżej:  
  
     ![Krawędzie, tworzące Szczyt dachu](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")  
  
     Po wybraniu krawędzie, na pasku narzędzi edytora modelu, wybierz **Translate** narzędzia, a następnie przenieść manipulator tłumaczenia w górę, aby utworzyć dachu domu.  
  
 Model DOM uproszczone zostało ukończone. Oto ponownie końcowego modelu z płaskim cieniowaniem stosowane:  
  
 ![Ukończone modelu DOM uproszczone](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Kolejnym krokiem może stosowanie cieniowania do modelu 3-D. Aby uzyskać informacje, zobacz [porady: stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: modelowanie terenu 3D](../designers/how-to-model-3-d-terrain.md)   
 [Edytor modelu](../designers/model-editor.md)   
 [Projektant cieniowania](../designers/shader-designer.md)



