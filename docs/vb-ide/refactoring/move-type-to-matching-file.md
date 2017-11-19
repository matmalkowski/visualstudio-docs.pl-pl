---
title: "Przenieś typ do dopasowania pliku - refaktoryzacji (Visual Basic) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e0b3fd-d1d9-4e3f-b0f6-9f8ffbbc6297
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b5d42bf01f8979cb52ea4fb4f89f16a78d78024
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Typ przenoszenia do odpowiedniego pliku w Visual Basic
**Co:** umożliwia przenoszenie wybranego typu do osobnego pliku o tej samej nazwie.

**Kiedy:** ma wiele klasy, struktury, interfejsy, itp. w tym samym pliku, który chcesz oddzielić.  

**Dlaczego:** umieszczenie wiele typów w tym samym pliku może utrudnić można znaleźć następujących typów.  Przenosząc typy plików o takiej samej nazwie, kod będzie bardziej czytelny i łatwiej Przejdź.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz nazwę typu, aby przenieść:

   ![Wyróżniony kod](media/movetype_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś typu *TypeName*.vb** z menu podręcznego okna podglądu gdzie *TypeName* to nazwa wybranego typu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Przenieś typu *TypeName*.vb** z menu podręcznego okna podglądu gdzie  *Właściwość TypeName* to nazwa wybranego typu.

   Typ zostanie natychmiast przenieść do nowego pliku o tej nazwie w ramach rozwiązania.

   ![Wynik wbudowany](media/movetype_result.png)

## <a name="see-also"></a>Zobacz też
[Refaktoryzacji (Visual Basic)](../refactoring-vb.md)