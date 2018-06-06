---
title: 'Porady: modyfikowanie punktu obrotu 3W modelu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a2d25029455f3e263013c4d6063ee7453a283b6
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747108"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Porady: modyfikowanie punktu obrotu 3W modelu

W tym artykule przedstawiono sposób użycia w edytorze modeli, aby zmodyfikować *punktu przestawnego* modelu 3D. Punkt pivot jest punktem przestrzeni definiująca środek matematyczne obiektu obrotu i skalowania.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Modyfikowanie punktu obrotu modelu 3D

Punkt początkowy modelu 3D można zmienić, modyfikując punktu obrotu.

Upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1.  Zaczyna się od istniejącego modelu 3D, takie jak opisany w [porady: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md).

2.  Tryb pivot. Na **tryb edytorze modeli** narzędzi wybierz **tryb Pivot** przycisk, aby aktywować tryb pivot. Zostanie wyświetlone okno z wokół **tryb Pivot** przycisk, aby wskazać, że edytor modelu jest teraz w trybie pivot. W trybie pivot operacji, takich jak tłumaczenia wpływa na punktu obrotu obiektu zamiast struktury obiektów w przestrzeni świata.

3.  Modyfikowanie punktu obrotu obiektu. W **wybierz** tryb, wybierz obiekt, a następnie na **podglądu modelu** narzędzi wybierz **Przetłumacz** narzędzia. Pole, który reprezentuje punktu obrotu pojawia się na powierzchni projektu. Przenieś okno można zmodyfikować punktu obrotu obiektu.

     Przenosząc pole, można przenieść punktu obrotu we wszystkich trzech wymiarach. Tłumaczenie punktu obrotu na jednej osi, przesuń strzałkę, która odpowiada na tej osi. Pole i strzałki Zmień kolor żółty, aby wskazać osi, których dotyczy tłumaczenia.

     Można również określić przy użyciu punktu obrotu **tłumaczenia Pivot** właściwości w **właściwości** okna.

    > [!TIP]
    > Możesz wyświetlić efekt nowego punktu obrotu przez obrócenie obiektu. Aby obrócić go, należy użyć **Obróć** narzędzie lub zmodyfikować **obrotu** właściwości.

Oto modelu, który ma punkt pivot zmodyfikowane:

![Modelu DOM, zawierający punkt zmodyfikowane pivot](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Zobacz także

- [Porady: Tworzenie podstawowego modelu 3D](../designers/how-to-create-a-basic-3-d-model.md)
- [Edytor modelu](../designers/model-editor.md)