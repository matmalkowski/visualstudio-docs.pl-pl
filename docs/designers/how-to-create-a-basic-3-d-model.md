---
title: 'Porady: Tworzenie podstawowego modelu 3D'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6627bac92221d66bd2cc1ab32efe10d0588c3b7e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745688"
---
# <a name="how-to-create-a-basic-3d-model"></a>Porady: Tworzenie podstawowego modelu 3D

W tym artykule przedstawiono sposób użycia w edytorze modeli do utworzenia podstawowego modelu 3D. Omówiono następujące działania:

-   Dodawanie obiektów do sceny

-   Wybieranie krojów i krawędzi.

-   Opcje tłumaczenia

-   Przy użyciu **podzielić krój** i **wyciągnięcie krój** narzędzia

-   Przy użyciu **Triangulate** polecenia

## <a name="create-a-basic-3d-model"></a>Tworzenie podstawowego modelu 3D
 Edytor modelu do tworzenia i modyfikowania modeli 3D i sceny gry lub aplikacji. Poniższe kroki pokazują, jak utworzyć uproszczony model 3D domu za pomocą edytora modelu. Uproszczony model może służyć jako elementu zastępczego dla zasobów graficznych końcowego, które są nadal tworzone, jako siatkę wykrywanie kolizji, lub można użyć, gdy obiekt, który reprezentuje jest zbyt daleko do korzystania z renderowania bardziej szczegółowe przy użyciu modelu szczegółów niskiego.

 Po zakończeniu modelu powinien wyglądać następująco:

 ![Ukończone modelu DOM uproszczony](../designers/media/gfx_model_demo_house_final.png)

 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

### <a name="to-create-a-simplified-3d-model-of-a-house"></a>Aby utworzyć uproszczony model 3D domu

1.  Tworzenie modelu 3D do pracy z. Aby uzyskać informacje o sposobie dodawania modelu do projektu, w sekcji wprowadzenie w [edytorze modeli](../designers/model-editor.md).

2.  Dodaj moduł do sceny. W **przybornika** okna, w obszarze **kształtów**, wybierz pozycję **modułu** i przenieść ją na powierzchnię projektu.

3.  Przełącza do zaznaczenia twarzy na obrazie. Na pasku narzędzi w edytorze modeli, wybierz **wybierz krój**.

4.  Podzielić na początku modułu. W trybie wyboru krój wybierz modułu raz, aby aktywować go do wyboru, a następnie wybierz górnej części modułu wybierz krój top. Na pasku narzędzi w edytorze modeli, wybierz **podzielić krój**. Spowoduje to dodanie nowego wierzchołki na początku modułu podziel go na partycje równej wielkości.

     ![Dzieli się na początku modułu](../designers/media/gfx_model_demo_house_subdiv.png)

5.  Wyciągnięcie dwóch sąsiadujących ze sobą stronach moduł — na przykład przodu i prawej krawędzi modułu. W trybu wyboru pierwszego planu wybierz moduł raz Aktywuj ją do wyboru, a następnie wybierz pozycję jednej stronie modułu. Naciśnij i przytrzymaj klawisz kontroli, wybierz inny po stronie modułu, która jest przyległa do strony, musisz najpierw wybrać, a następnie na pasku narzędzi edytora modelu wybierz **wyciągnięcie krój**.

     ![Strony moduł został wyrzucane](../designers/media/gfx_model_demo_house_extrude.png)

6.  Jeden z extrusions rozszerzenie. Wybierz jedną z powierzchni, które właśnie usunąć, a następnie na pasku narzędzi w edytorze modeli, wybierz **Przetłumacz** narzędzia i Przenieś manipulatora tłumaczenia w tym samym kierunku co wytłoczenie.

     ![Po jednej stronie modułu ma zostały usunąć dodatkowe.](../designers/media/gfx_model_demo_house_extend.png)

7.  Przeprowadzić triangulację modelu. Na pasku narzędzi w edytorze modeli, wybierz **zaawansowane**, **narzędzia**, **Triangulate**.

8.  Utwórz dachu domu. Przełącz do trybu wyboru krawędzi, wybierając **wybierz krawędzi** na pasku narzędzi w edytorze modeli, a następnie wybierz moduł, aby aktywować go. Naciśnij i przytrzymaj klawisz Control, jak wybrać krawędzi, które są wyświetlane tutaj:

     ![Krawędziach tworzących piku dachu](../designers/media/gfx_model_demo_house_edges.png)

     Po wybraniu krawędzi, na pasku narzędzi w edytorze modeli, wybierz **Przetłumacz** narzędzia, a następnie przenieść manipulatora tłumaczenia góry, aby utworzyć dachu domu.

 Modelu DOM uproszczony zostało ukończone. Oto ponownie ostatecznego modelu z płaskim cieniowaniem stosowane:

 ![Ukończone modelu DOM uproszczony](../designers/media/gfx_model_demo_house_final.png)

 Jako kolejny krok programu do cieniowania można zastosować do tego modelu 3D. Aby uzyskać informacje, zobacz [porady: dotyczą programu do cieniowania modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Porady: Model terenu 3D](../designers/how-to-model-3-d-terrain.md)
- [Edytor modelu](../designers/model-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)