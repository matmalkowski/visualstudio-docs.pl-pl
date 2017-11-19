---
title: EndCapture | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f587b10fea4b593234be2a536baa13cf7b3db66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="endcapture"></a>EndCapture
Kończy się interwał przechwytywania, który został uruchomiony z `BeginCapture`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał Przechwytywanie obejmuje zazwyczaj podzbiór jedną ramkę, takie jak kiedy zachodzi potrzeba przechwytywania grafiki tylko informacje dotyczące rodzaju wywołanie rysowania. Jeśli interwał Przechwytywanie obejmuje wywołania do prezentowania, dwie ramki informacji graficznych są przechwytywane. Pierwsza ramka obejmuje odstęp między wywołanie `BeginCapture` i wywołania w celu przedstawienia; drugiej ramki obejmuje odstęp między pierwsze zdarzenie Direct3D po wywołaniu metody do prezentowania i wywołania w celu `EndCapture`.  
  
 Aby przechwycić interwał, należy przygotować aplikację przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `BeginCapture` lub `EndCapture`.  
  
## <a name="see-also"></a>Zobacz też  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)