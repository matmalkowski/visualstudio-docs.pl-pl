---
title: ToggleHUD | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8839e41048a68adf09380e6fa428087299a12801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="togglehud"></a>ToggleHUD
Włącza/wyłącza diagnostyki grafiki *HUD* (wyświetlanie Head w górę) nakładki lub wyłączyć.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona pod nadzorem diagnostyki grafiki. Wyświetla informacje czasu wykonywania dotyczące aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie metody [AddMessage](addmessage.md) funkcję elementu członkowskiego.  
  
 Aby włączyć HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — czyli może być ich za pośrednictwem wystąpienia `VsgDbg` klasy, ale [Init](init.md) funkcji członkowskiej nie ma zostać wywołane najpierw.