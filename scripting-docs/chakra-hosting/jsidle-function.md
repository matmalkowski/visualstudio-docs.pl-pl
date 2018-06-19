---
title: Jsidle — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsIdle
helpviewer_keywords:
- JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788542"
---
# <a name="jsidle-function"></a>JsIdle — Funkcja
Informuje, czy przetwarzanie w stanie bezczynności należy wykonać środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nextIdleTick`  
 Następny systemu znaczników podczas będzie więcej bezczynności pracy. Może być równa zeru. Zwraca maksymalną liczbę znaczników jeśli tam nie nadchodzących pracy w stanie bezczynności.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli przetwarzanie w stanie bezczynności została włączona dla bieżącego środowiska uruchomieniowego, wywoływania `JsIdle` poinformuje bieżącego środowiska uruchomieniowego, że host jest w stanie bezczynności i że środowiska uruchomieniowego można wykonać zadania oczyszczania pamięci.  
  
 `JsIdle`można także wrócić liczbę taktów systemu, dopóki nie będzie więcej pracy bezczynności środowiska uruchomieniowego w celu. Wywoływanie `JsIdle` przed tym liczbę taktów ma wykona żadne czynności.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)