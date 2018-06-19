---
title: Jssetruntimememorylimit — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788593"
---
# <a name="jssetruntimememorylimit-function"></a>JsSetRuntimeMemoryLimit — Funkcja
Ustawia bieżący limit pamięci dla programu obsługi.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtime`  
 Środowisko uruchomieniowe limit pamięci, których ma dotyczyć.  
  
 `memoryLimit`  
 Nowe środowisko uruchomieniowe limit pamięci, w bajtach lub wartość -1, brak limitu pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Limit pamięci spowoduje żadnych operacji, która przekracza limit się niepowodzeniem z powodu błędu "Brak pamięci". Ustawienie limitu pamięci środowiska uruchomieniowego na-1 oznacza, że środowisko wykonawcze nie ma żadnych ograniczeń pamięci. Nowym domyślnym środowisk uruchomieniowych mającej limitu pamięci. Jeśli nowy limit pamięci przekracza bieżące użycie, połączenie powiedzie się i przyszłych alokacje w tym środowisku uruchomieniowym zakończy się niepowodzeniem, dopóki użycie pamięci środowiska uruchomieniowego spadnie poniżej limitu.  
  
 Moduł wykonawczy limit pamięci może być zawsze ustawiony, niezależnie od tego, czy środowisko wykonawcze jest aktywny w innym wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)