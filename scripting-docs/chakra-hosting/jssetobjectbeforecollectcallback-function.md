---
title: Jssetobjectbeforecollectcallback — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a472e63afd909ee7bcb74cb2fdd1ae98d6a2938
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788578"
---
# <a name="jssetobjectbeforecollectcallback-function"></a>JsSetObjectBeforeCollectCallback — funkcja
Ustawia funkcję wywołania zwrotnego, która jest wywoływana przez środowisko wykonawcze przed wyrzucanie elementów bezużytecznych obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ref`  
 Obiekt, dla którego ma zostać zarejestrowany wywołania zwrotnego.  
  
 `callbackState`  
 Stan użytkownika, który zostanie przekazany do wywołania zwrotnego.  
  
 `objectBeforeCollectCallback`  
 Funkcja wywołania zwrotnego ustawiany. Użyj wartości null, aby wyczyścić wcześniej zarejestrowane wywołanie zwrotne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne jest wywoływana w bieżącym wątku wykonywania środowiska uruchomieniowego, dlatego wykonywanie jest zablokowana do momentu ukończenia wywołania zwrotnego.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)