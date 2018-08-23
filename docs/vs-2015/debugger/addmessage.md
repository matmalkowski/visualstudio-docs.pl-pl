---
title: AddMessage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a81dda4564d87fe33d9d8e9c497e4aa040b8830e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629806"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [AddMessage](https://docs.microsoft.com/visualstudio/debugger/graphics/addmessage).  
  
Dodaje niestandardowy komunikat do diagnostyki grafiki *HUD* (wyświetlanie Head-Up).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szMessage`  
 Komunikat, który ma zostać dodany do HUD.  
  
## <a name="remarks"></a>Uwagi  
 HUD diagnostyki grafiki jest wyświetlany w lewym górnym rogu aplikacji, która jest uruchomiona w ramach diagnostyki grafiki. Wyświetla informacje czasu wykonywania dotyczące aplikacji i przechwytywanie informacji graficznych i komunikaty, które są dodawane przez wywołanie tej funkcji.  
  
 Aby dodać komunikat HUD, nie trzeba być aktywnie przechwytywanie informacji graficznych — oznacza to, że można dodać komunikat za pośrednictwem wystąpienia `VsgDbg` klasy, ale [Init](../debugger/init.md) funkcji składowej nie jest wywoływany jako pierwszy. Komunikaty są wyświetlane tylko w HUD, nie są rejestrowane w pliku dziennika grafiki.



