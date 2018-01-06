---
title: AddMessage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0841e622b0fe7c0d01d374da21a12a151c59021d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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