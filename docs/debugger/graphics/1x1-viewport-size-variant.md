---
title: Wariant rozmiaru okienka ekranu 1 x 1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 074cf7111108b7ae4f3b6866be19f0a12d3c429b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="1x1-viewport-size-variant"></a>Wariant rozmiaru okienka ekranu 1 x 1
Zmniejsza wymiary okienka ekranu na wszystkie elementy docelowe renderowania na 1 x 1 pikseli.  
  
## <a name="interpretation"></a>Interpretacja  
 Mniejsze okienka ekranu zmniejsza liczbę pikseli, które muszą być przyciemnione, ale nie zmniejszyć liczbę wierzchołków, które muszą zostać przetworzone. Ustawienie wymiary okienka ekranu 1 x 1 pikseli skutecznie eliminuje cieniowanie pikseli, który z aplikacji.  
  
 Jeśli ten wariant wyświetlane są bardziej wydajne duży, może to oznaczać, że aplikacja zużywa zbyt dużej ilości fillrate. Może to oznaczać, że rozdzielczość wybrano jest za duża dla platformy docelowej lub że aplikacja zużywa długiego czasu cieniowanie pikseli, które później zostaną zastąpione (overdraw). Tego wyniku sugeruje, że zmniejszaniu rozmiaru z obiektu lub ograniczenie liczby overdraw poprawi wydajność aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wymiary okienka ekranu są resetowane do 1 x 1 pikseli po każdym wywołaniu `ID3D11DeviceContext::OMSetRenderTargets` lub `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Przykład  
 Ten wariant można odtworzyć za pomocą kodu w następujący sposób:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```