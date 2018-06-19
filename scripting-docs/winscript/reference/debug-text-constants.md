---
title: Stałe DEBUG_TEXT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791830"
---
# <a name="debugtext-constants"></a>Stałe DEBUG_TEXT
Używane podczas [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Wskazuje, że tekst jest wyrażenie w przeciwieństwie do instrukcji. Ta flaga może mieć wpływ na sposób analizowania tekstu w niektórych językach.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Jeśli wartość zwracana jest dostępna, będzie używany przez obiekt wywołujący.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nie zezwalaj na efekty uboczne. Jeśli ta flaga jest ustawiona, obliczania wyrażenia powinien zmienić nie stan czasu wykonywania.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Zezwalaj punktów przerwania podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona, punkty przerwania zostaną zignorowane podczas obliczania tekstu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Zezwalaj raportów o błędach podczas obliczania tekstu. Jeśli ta flaga nie jest ustawiona, następnie błędów nie jest informowany o hosta podczas obliczania.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Wskazuje, że wyrażenie, które ma zostać obliczone dla kontekstu kodu, a nie z wyrażenia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)