---
title: IDiaEnumTables::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9cdd57eea5d6c70086eb258841a091cd70eddca4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
 [out] Zwraca [idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md) obiekt, który zawiera zduplikowane modułu wyliczającego. Tabele nie są duplikowane, tylko moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)