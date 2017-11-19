---
title: "Jssetruntimememoryallocationcallback — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords: JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememoryallocationcallback-function"></a>JsSetRuntimeMemoryAllocationCallback — Funkcja
Ustawia wywołanie zwrotne alokacji pamięci dla określonego środowiska wykonawczego  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtime`  
 Środowisko uruchomieniowe, dla którego ma zostać zarejestrowany wywołania zwrotnego alokacji.  
  
 `callbackState`  
 Użytkownik podał stanu, który zostanie przekazany do wywołania zwrotnego.  
  
 `allocationCallback`  
 Alokacja pamięci wywołanie zwrotne ma być wywoływana dla zdarzenia alokacji pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Rejestrowanie wywołanie zwrotne alokacji pamięci spowoduje, że środowisko wykonawcze do wywołania zwrotnego do hosta, zawsze, gdy uzyskuje pamięci z lub zwalnia pamięć do systemu operacyjnego. Procedura wywołania zwrotnego jest wywoływana przed Menedżer pamięci środowiska uruchomieniowego przydziela bloku pamięci. Alokacja zostanie odrzucone, jeśli wywołanie zwrotne zwraca wartość false. Menedżer pamięci środowiska wykonawczego również wywoła procedura wywołania zwrotnego po uwolnieniu blok pamięci, a także po błędów alokacji.  
  
 Wywołanie zwrotne jest wywoływana w bieżącym wątku wykonywania środowiska uruchomieniowego, dlatego wykonywanie jest zablokowana do momentu ukończenia wywołania zwrotnego.  
  
 Wartość zwracana wywołania zwrotnego nie są przechowywane; wcześniej odrzucone alokacje nie uniemożliwi środowiska uruchomieniowego wywoływania wywołania zwrotnego później dla nowej alokacji pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)