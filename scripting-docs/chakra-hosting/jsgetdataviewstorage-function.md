---
title: "Jsgetdataviewstorage — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c2180e0-51d5-4cc8-ad21-8bf29ff7c583
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b405fc22e411c343dcd5214495deb0275f5db52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetdataviewstorage-function"></a>JsGetDataViewStorage — funkcja
Pobiera powiązany magazyn pamięci używane przez `DataView`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDAPI_(JsErrorCode) JsGetDataViewStorage(  
   _In_ JsValueRef dataView,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataView`  
 Wystąpienie DataView.  
  
 `buffer`  
 Bufor DataView. Okres istnienia zwróconego buforu jest taka sama jak okres istnienia `DataView`. Wskaźnika buforu nie liczy się jako odwołanie do `DataView` na potrzeby wyrzucanie elementów bezużytecznych.  
  
 `bufferLength`  
 Liczba bajtów w buforze.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)