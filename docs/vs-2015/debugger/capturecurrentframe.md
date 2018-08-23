---
title: CaptureCurrentFrame | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2fcb05d63370f8f40ab09f0978e0f49dbe7d6a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682544"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CaptureCurrentFrame](https://docs.microsoft.com/visualstudio/debugger/graphics/capturecurrentframe).  
  
Rejestruje pozostałą część bieżącej ramki w pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli inny przechwytywania jest obecnie w toku — takich jak przechwytywanie, które zostało uruchomione przez `BeginCapture` funkcji — tego przechwytywania jest zakończone i rejestrowane w dzienniku grafiki jako odrębne ramki. Natychmiast po tym dniu diagnostyki grafiki rozpoczyna się, przechwytywania w pozostałej części bieżącej ramki, który jest zarejestrowany jako odrębne ramki. Koniec bieżącej ramki jest oznaczona przez wywołanie do przedstawienia.  
  
 Aby przechwycić ramki, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](../debugger/init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)



