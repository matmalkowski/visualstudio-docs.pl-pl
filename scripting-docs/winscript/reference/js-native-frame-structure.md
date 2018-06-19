---
title: Struktura JS_NATIVE_FRAME | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e93041a6dec767cb3bb11382abfb562068c925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796306"
---
# <a name="jsnativeframe-structure"></a>Struktura JS_NATIVE_FRAME
Reprezentuje ramkę stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `InstructionOffset`  
 Wskaźnik instrukcji.  
  
 `ReturnOffset`  
 Adres zwrotny.  
  
 `FrameOffset`  
 Wskaźnik ramki.  
  
 `StackOffset`  
 Wskaźnik stosu.  
  
## <a name="remarks"></a>Uwagi  
 `JS_NATIVE_FRAME` Struktury jest używany przez `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)