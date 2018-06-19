---
title: BeginCapture | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c04f199472afc516304f7a8f4f135174593b60
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473618"
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