---
title: "Porady: Użyj projektanta argumentów | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7fe9e4f7a3f4bc603d3f2661b91c5807bea8e4a6
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-the-argument-designer"></a>Porady: Użyj projektanta argumentów
W porównaniu z poprzednimi wersjami [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], projektanta argumentów ułatwia umożliwiają przepływ do i z działania danych. Projektant jest dostępne po kliknięciu **argumenty** przycisk w lewym dolnym rogu obszaru projektowania. Projektant zawiera listę argumentów, które znajdują się w formie tabelarycznej i można sortować według poszczególnych nagłówków kolumn, z wyjątkiem **wartość domyślna** kolumny. Każdy argument zawiera nazwa, kierunek w/out/w out/właściwości, typ i domyślne wyrażenie wartości (jeśli istnieją). Nazwa i wartość domyślną, wyrażenia są pola edycji, a typie i kierunku są listach rozwijanych. Aby uzyskać więcej informacji, zobacz [zmiennych i argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

### <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument

1.  Otwórz rozwiązanie przepływu pracy lub działania w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Otwórz projektanta argumentów, klikając przycisk **argumenty** przycisk w lewym dolnym rogu obszaru projektowania. Zostanie wyświetlona projektanta argumentów.

3.  Kliknij pusty wiersz z etykietą **utworzyć Argument**. Spowoduje to dodanie nowego wiersza z argumentem nowe przy użyciu następujących wartości domyślnych: argumentx dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany można utworzyć nazwy argumentu unikatowy **w**  dla **kierunek**, i **ciąg** dla **typ argumentu**. Wartość nie jest dodawany do **wartość domyślna**. Te wartości można zmienić w dowolnym momencie podczas tworzenia projektu przepływu pracy.

    > [!NOTE]
    > Aby usunąć argumentu, zaznacz argument, klikając go, a następnie naciśnij klawisz **usunąć** klucza.

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)
- [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)