---
title: 'Projektant przepływu pracy — porady: Użyj projektanta argumentów'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 868fc13474e90be219cf1acebc00074641df142e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755525"
---
# <a name="how-to-use-the-argument-designer"></a>Porady: Użyj projektanta argumentów

W porównaniu do poprzednich wersji programu .NET Framework, projektanta argumentów ułatwia umożliwiają przepływ do i z działania danych. Projektant jest dostępne po kliknięciu **argumenty** przycisk w lewym dolnym rogu obszaru projektowania. Projektant zawiera listę argumentów, które znajdują się w formie tabelarycznej i można sortować według poszczególnych nagłówków kolumn, z wyjątkiem **wartość domyślna** kolumny. Każdy argument zawiera nazwa, kierunek w/out/w out/właściwości, typ i domyślne wyrażenie wartości (jeśli istnieją). Nazwa i wartość domyślną, wyrażenia są pola edycji, a typie i kierunku są listach rozwijanych. Aby uzyskać więcej informacji, zobacz [zmiennych i argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument

1.  Otwórz rozwiązanie przepływu pracy lub działania w programie Visual Studio.

2.  Otwórz projektanta argumentów, klikając przycisk **argumenty** przycisk w lewym dolnym rogu obszaru projektowania. Zostanie wyświetlona projektanta argumentów.

3.  Kliknij pusty wiersz z etykietą **utworzyć Argument**. Spowoduje to dodanie nowego wiersza z argumentem nowe przy użyciu następujących wartości domyślnych: argumentx dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany można utworzyć nazwy argumentu unikatowy **w**  dla **kierunek**, i **ciąg** dla **typ argumentu**. Wartość nie jest dodawany do **wartość domyślna**. Te wartości można zmienić w dowolnym momencie podczas tworzenia projektu przepływu pracy.

    > [!NOTE]
    > Aby usunąć argumentu, zaznacz argument, klikając go, a następnie naciśnij klawisz **usunąć** klucza.

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)
- [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)