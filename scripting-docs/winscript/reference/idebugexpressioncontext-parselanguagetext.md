---
title: IDebugExpressionContext::ParseLanguageText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Tworzy wyrażenie debugowania dla określonego tekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Zawiera tekst wyrażenia lub instrukcji.  
  
 `nRadix`  
 [in] Podstawa do użycia.  
  
 `pstrDelimiter`  
 [in] Ogranicznik zakończenia z skryptu bloku. Gdy `pstrCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec bloku skryptu. Ten parametr określa ogranicznik używany hosta, dzięki czemu aparat skryptów w celu zapewnienia przetworzenia warunkowego wstępnego pierwotnych (na przykład, zastępując pojedynczego cudzysłowu ['] dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik). Dokładnie, jak (i jeśli) skryptów używa aparatu tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr, `NULL` Jeśli host nie użyto ogranicznik można oznaczyć końca bloku skryptu.  
  
 `dwFlags`  
 [in] Kombinacja następujące flagi tekst debugowania:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Wskazuje, że tekst jest wyrażenie w przeciwieństwie do instrukcji. Ta flaga może mieć wpływ na sposób analizowania tekstu w niektórych językach.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Jeśli wartość zwracana jest dostępna, będzie używany przez obiekt wywołujący.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nie zezwalaj efekty uboczne. Jeśli ta flaga jest ustawiona, obliczania wyrażenia powinien zmienić nie stan czasu wykonywania.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Umożliwia punktów przerwania podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona punkty przerwania są ignorowane podczas obliczania tekstu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Umożliwia raportów o błędach podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona. następnie błędów nie są zgłaszane do hosta podczas obliczania.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Wskazuje wyrażenie, które ma zostać obliczone dla kontekstu kodu, a nie z wyrażenia.|  
  
 `ppe`  
 [out] Zwraca wyrażenie debugowania dla określonego tekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy wyrażenia debugowania dla określonego tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)