---
title: IDiaSession::findSymbolByVAEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3fad26dfd43057f02105e867c5f1f0add57b20d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
Pobiera typ określony symbol, który zawiera lub najbliższy określony wirtualny adres (VA) i przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 [in] Określa VA.  
  
 `symtag`  
 [in] Typ symbolu, który ma zostać odnaleziona. Wartości są pobierane z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenia.  
  
 `ppSymbol`  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) pobrać obiekt reprezentujący symbol.  
  
 `displacement`  
 [out] Zwraca wartość określa przesunięcie od wirtualnego adresu określonego przez `va`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)