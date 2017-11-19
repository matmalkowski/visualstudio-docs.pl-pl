---
title: IDiaSession::findInlineeLinesByLinenum | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c18b2919605e3b2de6f59303c304ffb3d8f05198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio w określonym źródle liczbę plików i wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compiland`  
 [in] [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który reprezentuje compiland, w których będą poszukiwane numerów wierszy. Ten parametr nie może być `NULL`.  
  
 `file`  
 [in] [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiekt, który reprezentuje plik źródłowy, w którym do wyszukiwania. Ten parametr nie może być `NULL`.  
  
 `linenum`  
 [in] Określa liczbę oparte na jeden wiersz.  
  
> [!NOTE]
>  Nie można użyć zero, aby określić wszystkie wiersze (Użyj [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) metody do znalezienia wszystkich wierszy).  
  
 `column`  
 [in] Określa liczbę kolumn. Użyj wartości zero, aby określić wszystkie kolumny. Kolumna jest Przesunięcie bajtów, w wierszu.  
  
 `ppResult`  
 [out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiekt, który zawiera listę numerów wierszy, które zostały pobrane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)