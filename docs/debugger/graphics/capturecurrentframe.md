---
title: CaptureCurrentFrame | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41169494424310427e5a8ae6a0af533bdf4be834
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471236"
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
 [init](init.md)   
 [BeginCapture](begincapture.md)