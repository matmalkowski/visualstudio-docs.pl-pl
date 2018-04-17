---
title: 'Porady: Model 3-terenu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec1cf2d86ddb052b1f12310fb80d192aee080596
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-model-3-d-terrain"></a>Porady: model terenu 3-D
Ten dokument przedstawia sposób umożliwiają utworzenie modelu terenu 3-w edytorze modeli.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Dodawanie obiektów do sceny  
  
-   Wybieranie krojów i punkty  
  
-   Opcje tłumaczenia  
  
-   Przy użyciu **podzielić krój** narzędzia  
  
-   Framing obiektu w powierzchnię projektu  
  
## <a name="creating-a-3-d-terrain-model"></a>Tworzenie modelu terenu 3-w  
 Można utworzyć 3-terenu podziału na płaszczyźnie dokonanie kroje dodatkowe, a następnie manipulowanie ich wierzchołków do utworzenia ciekawe funkcje terenu.  
  
 Po zakończeniu modelu powinien wyglądać następująco:  
  
 ![3&#45;sceny D, pokazujący model terenu](../designers/media/digit-terrain-model.png "cyfrę terenu modelu")  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>Aby utworzyć model terenu 3-w  
  
1.  Utwórz do pracy z 3-w modelu. Aby uzyskać informacje o sposobie dodawania modelu do projektu, w sekcji wprowadzenie w [edytorze modeli](../designers/model-editor.md).  
  
2.  Dodaj płaszczyźnie do sceny. W **przybornika**w obszarze **kształtów**, wybierz pozycję **płaszczyzny** i przenieść ją na powierzchnię projektu.  
  
    > [!TIP]
    >  Aby ułatwić obiektu płaszczyzny do pracy z, można go ramek na powierzchni projektu. W **wybierz** tryb, wybierz obiekt płaszczyzny, a następnie na pasku narzędzi w edytorze modeli, wybierz **ramki obiektu** przycisku.  
  
3.  Wprowadź trybu wyboru pierwszego planu. Na pasku narzędzi w edytorze modeli, wybierz **wybierz krój**.  
  
4.  Podzielić płaszczyzny. W trybie wyboru krój wybierz płaszczyzny raz, aby aktywować go do wyboru, a następnie wybierz go ponownie, aby wybrać jej tylko powierzchni. Na pasku narzędzi w edytorze modeli, wybierz **podzielić krój**. Spowoduje to dodanie nowego wierzchołków płaszczyzny podziel go na partycje równej wielkości.  
  
5.  Utwórz więcej podziałów podrzędnych. Powierzchnie nadal zaznaczony, wybierz polecenie **podzielić krój** dwa razy. Spowoduje to utworzenie Suma powierzchnie 64. Tworząc więcej podziałów podrzędnych, można nadać terenu jeszcze więcej szczegółów.  
  
6.  Wprowadź trybu wyboru punktu. Na pasku narzędzi w edytorze modeli, wybierz **wybierz punkt**.  
  
7.  Modyfikowanie punktu w celu tworzenia funkcji terenu. W trybie wyboru punktu, wybierz jeden z punktów, a następnie na pasku narzędzi w edytorze modeli, wybierz **Przetłumacz** narzędzia. Pole, który reprezentuje punkt pojawia się na powierzchni projektu. Umożliwia zieloną strzałkę Przenieś okno i tym samym zmodyfikować wysokość punktu. Powtórz ten krok dla różnych punktów w celu utworzenia ciekawe funkcje terenu.  
  
    > [!TIP]
    >  Możesz wybrać kilka punktów jednocześnie z ich w jednolity sposób.  
  
 Model terenu zostało ukończone. Oto ponownie ostatecznego modelu z cieniowaniem Phong stosowane:  
  
 ![3&#45;sceny D, pokazujący model terenu](../designers/media/digit-terrain-model.png "cyfrę terenu modelu")  
  
 Ten model terenu można użyć do zaprezentowania efekt gradientu programu do cieniowania, które jest opisane w [porady: tworzenie do cieniowania gradientu geometrii](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor modelu](../designers/model-editor.md)