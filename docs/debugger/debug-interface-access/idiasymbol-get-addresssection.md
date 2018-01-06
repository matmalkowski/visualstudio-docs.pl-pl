---
title: IDiaSymbol::get_addressSection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: af030d63c79901a41ea2704000de5b4d62e70e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
Pobiera część adresu w sekcji. Używany, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsStatic`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca część sekcji adresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Dla statycznych elementów członkowskich znajdujących się w bibliotece DLL zewnętrznych sekcji zwracane przez tę metodę może być 0, zgodnie z tej metody polega na uzyskaniu elementu członkowskiego wirtualnego adresu. Wirtualne adresy są prawidłowe tylko wtedy, gdy [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metody w [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu została wywołana z parametrem różną od zera, określając adres ładowania biblioteki dll.  
  
 Aby uzyskać przesunięcia część adresu, należy wywołać [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) metody.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)