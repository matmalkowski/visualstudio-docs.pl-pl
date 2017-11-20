---
title: CaptureCurrentFrame | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcdeee28077f2c7affd1c4cd1f82d8c8cb29494b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Przechwytuje pozostałej części bieżącej ramki do pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kolejne przechwytywanie jest obecnie w toku — takie jak przechwytywania, które zostało uruchomione przez `BeginCapture` funkcja — ukończone i rejestrowane w dzienniku grafiki jako odrębne Ramka przechwytywania tego. Natychmiast po diagnostyki grafiki rozpoczyna przechwytywanie w pozostałej części bieżącej ramki, który jest zarejestrowany jako różne ramki. Końcowy bieżącej ramki jest oznaczona przez wywołanie do przedstawienia.  
  
 Aby przechwycić ramki, należy przygotować aplikację przechwytywanie i rejestrowanie informacji graficznych — to znaczy musi mieć wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](init.md)   
 [BeginCapture](begincapture.md)