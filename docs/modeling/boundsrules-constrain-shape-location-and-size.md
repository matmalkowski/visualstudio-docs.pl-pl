---
title: BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 69e189b8348b7c68c7a778f00975d5d1475223ab
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu

A *zasada granic* jest klasa, która definiuje limit na rozmiar i położenie kształtu. Zapewnia on metodę, który jest wywoływany cyklicznie, gdy użytkownik przeciąga kształtu lub narożniki lub krawędzi kształtu.

Poniższy przykład ogranicza prostokątnego kształtu jako pasek o stałym rozmiarze, pozioma lub pionowa. Gdy użytkownik przeciąga narożniki lub stron, konturu Przerzuca między dwie konfiguracje dozwolonych wysokość i szerokość.

Zasada granic jest klasa pochodna od <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. W kształcie tworzone jest wystąpienie reguły:

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

Należy zauważyć, że lokalizacja i rozmiar może być ograniczona, jeśli chcesz.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Odpowiadanie na i Propaguj zmiany](../modeling/responding-to-and-propagating-changes.md)