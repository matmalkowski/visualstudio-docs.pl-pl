---
title: Funkcja SccBeginBatch | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBeginBatch
helpviewer_keywords: SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e18eedcab133329f10064ef3dd6486beb2e1596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 Partie kontroli źródła są używane do wykonywania operacji w wielu projektów lub wielu kontekstów. Partie można wyeliminować projektu nadmiarowe okien dialogowych z środowisko użytkownika podczas operacji wsadowej. `SccBeginBatch` Funkcji i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako para funkcja wskazująca początek i koniec operacji. Nie można zagnieżdżać ich. `SccBeginBatch`Ustawia flagę wskazującą, czy operacja partii jest w toku.  
  
 Podczas operacji zbiorczej jest włączone, wtyczkę kontroli źródła należy co najwyżej jedno okno dialogowe dla pytań użytkownik widzi i stosować odpowiedzi z tego okna dialogowego na wszystkie kolejne operacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)