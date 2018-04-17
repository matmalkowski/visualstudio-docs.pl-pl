---
title: 'Porady: Tworzenie podstawowego modelu 3 | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b61ebe27209b80873ba5e7f751c70c106f6aab0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-basic-3-d-model"></a>Porady: tworzenie podstawowego modelu 3-D
Ten dokument pokazuje, jak można użyć do utworzenia podstawowego modelu 3-w edytorze modeli.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Dodawanie obiektów do sceny  
  
-   Wybieranie krojów i krawędzi.  
  
-   Opcje tłumaczenia  
  
-   Przy użyciu **podzielić krój** i **wyciągnięcie krój** narzędzia  
  
-   Przy użyciu **Triangulate** polecenia  
  
## <a name="creating-a-basic-3-d-model"></a>Tworzenia podstawowego modelu 3-w  
 Edytor modelu do tworzenia i modyfikowania 3-modeli i sceny gry lub aplikacji. Poniższe kroki pokazują, jak utworzyć uproszczony model 3-w domu za pomocą edytora modelu. Uproszczony model może służyć jako elementu zastępczego dla zasobów graficznych końcowego, które są nadal tworzone, jako siatkę wykrywanie kolizji, lub można użyć, gdy obiekt, który reprezentuje jest zbyt daleko do korzystania z renderowania bardziej szczegółowe przy użyciu modelu szczegółów niskiego.  
  
 Po zakończeniu modelu powinien wyglądać następująco:  
  
 ![Ukończone modelu DOM uproszczony](../designers/media/gfx_model_demo_house_final.png "gfx_model_demo_house_final")  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Aby utworzyć uproszczony model 3-w domu  
  
1.  Utwórz do pracy z 3-w modelu. Aby uzyskać informacje o sposobie dodawania modelu do projektu, w sekcji wprowadzenie w [edytorze modeli](../designers/model-editor.md).  
  
2.  Dodaj moduł do sceny. W **przybornika** okna, w obszarze **kształtów**, wybierz pozycję **modułu** i przenieść ją na powierzchnię projektu.  
  
3.  Przełącza do zaznaczenia twarzy na obrazie. Na pasku narzędzi w edytorze modeli, wybierz **wybierz krój**.  
  
4.  Podzielić na początku modułu. W trybie wyboru krój wybierz modułu raz, aby aktywować go do wyboru, a następnie wybierz górnej części modułu wybierz krój top. Na pasku narzędzi w edytorze modeli, wybierz **podzielić krój**. Spowoduje to dodanie nowego wierzchołki na początku modułu podziel go na partycje równej wielkości.  
  
     ![Dzieli się na początku modułu](../designers/media/gfx_model_demo_house_subdiv.png "gfx_model_demo_house_subdiv")  
  
5.  Wyciągnięcie dwóch sąsiadujących ze sobą stronach moduł — na przykład przodu i prawej krawędzi modułu. W trybu wyboru pierwszego planu wybierz moduł raz Aktywuj ją do wyboru, a następnie wybierz pozycję jednej stronie modułu. Naciśnij i przytrzymaj klawisz kontroli, wybierz inny po stronie modułu, która jest przyległa do strony, musisz najpierw wybrać, a następnie na pasku narzędzi edytora modelu wybierz **wyciągnięcie krój**.  
  
     ![Strony moduł został wyrzucane](../designers/media/gfx_model_demo_house_extrude.png "gfx_model_demo_house_extrude")  
  
6.  Jeden z extrusions rozszerzenie. Wybierz jedną z powierzchni, które właśnie usunąć, a następnie na pasku narzędzi w edytorze modeli, wybierz **Przetłumacz** narzędzia i Przenieś manipulatora tłumaczenia w tym samym kierunku co wytłoczenie.  
  
     ![Po jednej stronie modułu ma zostały usunąć dodatkowe. ] (../designers/media/gfx_model_demo_house_extend.png "gfx_model_demo_house_extend")  
  
7.  Przeprowadzić triangulację modelu. Na pasku narzędzi w edytorze modeli, wybierz **zaawansowane**, **narzędzia**, **Triangulate**.  
  
8.  Utwórz dachu domu. Przełącz do trybu wyboru krawędzi, wybierając **wybierz krawędzi** na pasku narzędzi w edytorze modeli, a następnie wybierz moduł, aby aktywować go. Naciśnij i przytrzymaj klawisz Control, jak wybrać krawędzi, które są wyświetlane tutaj:  
  
     ![Krawędzie tworzących piku dachu](../designers/media/gfx_model_demo_house_edges.png "gfx_model_demo_house_edges")  
  
     Po wybraniu krawędzi, na pasku narzędzi w edytorze modeli, wybierz **Przetłumacz** narzędzia, a następnie przenieść manipulatora tłumaczenia góry, aby utworzyć dachu domu.  
  
 Modelu DOM uproszczony zostało ukończone. Oto ponownie ostatecznego modelu z płaskim cieniowaniem stosowane:  
  
 ![Ukończone modelu DOM uproszczony](../designers/media/gfx_model_demo_house_final.png "gfx_model_demo_house_final")  
  
 Jako kolejny krok można zastosować do tego modelu 3-programu do cieniowania. Aby uzyskać informacje, zobacz [porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Model terenu 3-w](../designers/how-to-model-3-d-terrain.md)   
 [Edytor modelu](../designers/model-editor.md)   
 [Projektant cieniowania](../designers/shader-designer.md)