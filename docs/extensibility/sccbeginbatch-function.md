---
title: Funkcja SccBeginBatch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5350484294d02356301839e38b97bea1d40ec27c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccbeginbatch-function"></a>Funkcja SccBeginBatch
Ta funkcja zostanie uruchomiony sekwencji operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołana w celu zakończenia wykonywania zadania wsadowego. Partie te nie mogą być zagnieżdżone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Wsadowe operacji zostało uruchomione pomyślnie.|  
|SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Partie kontroli źródła są używane do wykonywania operacji w wielu projektów lub wielu kontekstów. Partie można wyeliminować projektu nadmiarowe okien dialogowych z środowisko użytkownika podczas operacji wsadowej. `SccBeginBatch` Funkcji i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako para funkcja wskazująca początek i koniec operacji. Nie można zagnieżdżać ich. `SccBeginBatch` Ustawia flagę wskazującą, czy operacja partii jest w toku.  
  
 Podczas operacji zbiorczej jest włączone, wtyczkę kontroli źródła należy co najwyżej jedno okno dialogowe dla pytań użytkownik widzi i stosować odpowiedzi z tego okna dialogowego na wszystkie kolejne operacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)