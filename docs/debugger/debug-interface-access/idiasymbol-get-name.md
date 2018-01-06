---
title: IDiaSymbol::get_name | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_name method
ms.assetid: 050ec02f-b7b3-48fc-8e35-58bdf7d938b0
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ab58c34dabcd98b4608a37e59be0c2e4fab14161
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetname"></a>IDiaSymbol::get_name
Pobiera nazwę symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_name (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca nazwę symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaSymbol* pType;  
BSTR        name;  
pType->get_name( &name );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)