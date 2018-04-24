---
title: ToggleHUD | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
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