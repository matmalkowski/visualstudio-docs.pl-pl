---
title: BeginCapture | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1c7c0f57b919271c4880c9c1f2fbd8ca1dc964f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="begincapture"></a>BeginCapture
Rozpoczyna się interwał przechwytywania, który będzie kończyć się `EndCapture`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał Przechwytywanie obejmuje zazwyczaj podzbiór jedną ramkę, takie jak kiedy zachodzi potrzeba przechwytywania grafiki tylko informacje dotyczące rodzaju wywołanie rysowania. Jeśli interwał Przechwytywanie obejmuje wywołania do prezentowania, dwie ramki informacji graficznych są przechwytywane. Pierwsza ramka obejmuje odstęp między wywołanie `BeginCapture` i wywołania w celu przedstawienia; drugiej ramki obejmuje odstęp między pierwsze zdarzenie Direct3D po wywołaniu metody do prezentowania i wywołania w celu `EndCapture`.  
  
 Aby przechwycić interwał, należy przygotować aplikację przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `BeginCapture` lub `EndCapture`.  
  
## <a name="see-also"></a>Zobacz też  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)