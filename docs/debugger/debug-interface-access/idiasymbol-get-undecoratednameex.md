---
title: IDiaSymbol::get_undecoratedNameEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 82d0b25b2306cc957015ec4c205a22cd44660357
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Pobiera część lub całość bez nazwy dla języka C++ dekorowane nazwy (połączenie).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `undecoratedOptions`  
 [in] Określa kombinację flag tego formantu, co jest zwracany. Zobacz sekcję uwag dla określonych wartości i ich działania.  
  
 `pRetVal`  
 [out] Zwraca nazwę bez C++ dekorowane nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 `undecorateOptions` Może być kombinacją następujące flagi.  
  
> [!NOTE]
>  Nazwy flagi nie są zdefiniowane w DIA SDK, więc należy dodać deklaracji w kodzie albo użyj wartości w wierszach.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Włącza pełne undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0X0001|Usuwa wiodące znaki podkreślenia z rozszerzone słowa kluczowe firmy Microsoft.|  
|UNDNAME_NO_MS_KEYWORDS|0X0002|Wyłącza rozszerzenia rozszerzone słowa kluczowe firmy Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0X0004|Wyłącza rozszerzenia zwracanego typu dla deklaracji podstawowej.|  
|UNDNAME_NO_ALLOCATION_MODEL|0X0008|Wyłącza rozszerzenia modelu deklaracji.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Wyłącza rozszerzenia specyfikator języka deklaracji.|  
|UNDNAME_RESERVED1|0x0020|ZASTRZEŻONE.|  
|UNDNAME_RESERVED2|0x0040|ZASTRZEŻONE.|  
|UNDNAME_NO_THISTYPE|0x0060|Powoduje wyłączenie wszystkich modyfikatorów na `this` typu.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Wyłącza rozszerzenia specyfikatory dostępu dla członków.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Wyłącza rozszerzenia "throw podpisów" dla funkcji i wskaźniki do funkcji.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Wyłącza rozszerzenia `static` lub `virtual` elementów członkowskich.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Wyłącza rozszerzenia modelu firmy Microsoft dla zwraca UDT.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates nazwy ozdobione 32-bitowych.|  
|UNDNAME_NAME_ONLY|0x1000|Pobiera nazwę głównej deklaracji; Zwraca tylko [zakres::] nazwa.  Rozwija parametry szablonu.|  
|UNDNAME_TYPE_ONLY|0x2000|Dane wejściowe są po prostu typu kodowania; Redaguj deklarator abstrakcyjny.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Parametry szablonu rzeczywistych są dostępne.|  
|UNDNAME_NO_ECSU|0x8000|Pomija enum/klasy/struktury/Unii.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Pomija Sprawdź, czy znaki prawidłowego identyfikatora.|  
|UNDNAME_NO_PTR64|0x20000|Nie ma ptr64 w danych wyjściowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)