---
title: "Jsdisableruntimeexecution — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsdisableruntimeexecution-function"></a>JsDisableRuntimeExecution — Funkcja
Wstrzymuje wykonywanie skryptu i kończy skrypty uruchomione w środowisku uruchomieniowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtime`  
 Środowisko uruchomieniowe zostanie zawieszona.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania zawieszone środowiska uruchomieniowego zakończy się niepowodzeniem, dopóki `JsEnableRuntimeExecution` jest wywoływana.  
  
 Ten interfejs API nie trzeba można wywołać w wątku, środowisko wykonawcze jest na nim aktywna. Mimo że środowisko wykonawcze zostanie ustawiona w stanie wstrzymanym, wykonywanie skryptu nie może być zawieszone natychmiast; Uruchamianie skryptu zostanie zakończona z powodu wyjątku niemożliwy do przechwycenia tak szybko, jak to możliwe.  
  
 Wstrzymanie wykonywania w czasie wykonywania, który jest już zawieszony jest pusta.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)