---
title: Funkcja JsParseSerializedScriptWithCallback | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15f531783c7a1018340be8033261a58418d0f515
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788551"
---
# <a name="jsparseserializedscriptwithcallback-function"></a>Funkcja JsParseSerializedScriptWithCallback
Analizuje serializacji skryptu i zwraca funkcję reprezentujący skryptu.     Zapewnia możliwość ładowania opóźnionego źródła skryptu tylko jeśli się jest wymagana.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptLoadCallback`  
 Wywołanie zwrotne wywoływane, gdy kod źródłowy skryptu musi być załadowany.  
  
 `scriptUnloadCallback`  
 Wywołanie zwrotne wywoływane, gdy skrypt serializacji i kod źródłowy nie są już potrzebne.  
  
 `buffer`  
 Skrypt serializacji.  
  
 `sourceContext`  
 Plik cookie identyfikowanie skrypt, który może służyć kontekstów możliwością debugowania skryptu.     Ten kontekst zostanie przekazany scriptLoadCallback i scriptUnloadCallback.  
  
 `sourceUrl`  
 Lokalizacja skryptu pochodzi z.  
  
 `result`  
 Funkcja reprezentującą kod skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs API nie jest jeszcze dostępna dla aplikacji ze sklepu.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
 Środowisko uruchomieniowe będą przechowywane w buforze, dopóki wszystkie wystąpienia utworzone na podstawie buforu funkcji są bezużytecznych.  Następnie zostanie wywołany scriptUnloadCallback informują wywołującego bezpieczeństwa do zwolnienia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)