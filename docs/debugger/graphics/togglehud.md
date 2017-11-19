---
title: ToggleHUD | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bf1e27b9385257203653f3bff5241f6c3875373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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