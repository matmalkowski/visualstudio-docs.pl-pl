---
title: "Ogranicz BoundsRules kształtu lokalizacja i rozmiar | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 8a611bd18cb06b712f671d370bfc26d4dc8cf4f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu
A *zasada granic* jest klasa, która definiuje limit na rozmiar i położenie kształtu. Zapewnia on metodę, który jest wywoływany cyklicznie, gdy użytkownik przeciąga kształtu lub narożniki lub krawędzi kształtu.  
  
 Poniższy przykład ogranicza prostokątnego kształtu jako pasek o stałym rozmiarze, pozioma lub pionowa. Gdy użytkownik przeciąga narożniki lub stron, konturu Przerzuca między dwie konfiguracje dozwolonych wysokość i szerokość.  
  
 Zasada granic jest klasa pochodna od <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. W kształcie tworzone jest wystąpienie reguły:  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Odpowiada na żądania i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)