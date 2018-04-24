---
title: AddMessage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3460a345dba21e3a8f481adb510b9e3bdd4990
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="addmessage"></a>AddMessage
Dodaje niestandardowy komunikat do diagnostyki grafiki *HUD* (wyświetlanie Head-Up).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szMessage`  
 Komunikat, który ma zostać dodany do HUD.  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona pod nadzorem diagnostyki grafiki. Wyświetla informacje czasu wykonywania o aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie tej funkcji.  
  
 Aby dodać komunikat do HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — czyli komunikat można dodać za pomocą wystąpienia `VsgDbg` klasy, ale [Init](init.md) funkcji członkowskiej nie można wywołać najpierw. Komunikaty są wyświetlane tylko w HUD, nie są rejestrowane w pliku dziennika grafiki.