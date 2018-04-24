---
title: IDiaSymbol::get_isLTCG | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a799cf16dbf603f75cd810f9c249f4c0e8ba49ec
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
Pobiera flagę określającą, czy [Compiland](../../debugger/debug-interface-access/compiland.md) została połączona z przełącznikiem konsolidatora [opcję/LTCG (Generowanie kodu w czasie Link)](/cpp/build/reference/ltcg-link-time-code-generation), która pomaga w optymalizacja całego programu. Ta opcja dotyczy tylko kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pFlag  
 [out] Zwraca `TRUE` Jeśli `compiland` został połączony z przełącznikiem konsolidatora opcję/LTCG; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|DIA SDK w wersji 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)