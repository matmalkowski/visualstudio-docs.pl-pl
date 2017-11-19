---
title: IDiaSession::findFileById | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1996bed14323adeac794f12ed4307e96e3ba8b54
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Pobiera pliku źródłowego przez identyfikator pliku źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uniqueId`  
 [in] Określa identyfikator pliku źródłowego.  
  
 `ppResult`  
 [out] Zwraca [idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) pobrać obiekt, który reprezentuje plik źródłowy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Identyfikator pliku źródłowego jest używana wewnętrznie w celu DIA SDK, aby zapewnić, że wszystkie pliki źródłowe unikatowy unikatową wartość. Ta metoda jest zwykle używana wewnętrznie w celu DIA SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)