---
title: Wyliczenie SOURCE_TEXT_ATTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796453"
---
# <a name="sourcetextattr-enumeration"></a>Wyliczenie SOURCE_TEXT_ATTR
Opisuje atrybuty pojedynczego znaku w tekście źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0X0001|Znak jest częścią słowem kluczowym języka, na przykład słowa kluczowego VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0X0002|Znak jest częścią blok komentarza.|  
|SOURCETEXT_ATTR_NONSOURCE|0X0004|Znak nie jest częścią tekst źródłowy skompilowanych języka. Na przykład HTML otaczającego blok skryptu.|  
|SOURCETEXT_ATTR_OPERATOR|0X0008|Znak jest częścią operator języka. Na przykład:, operatora arytmetycznego  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Znak jest częścią języka stałej liczbowej.  Na przykład stała 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Znak jest częścią stałą typu string języka. Na przykład ciąg "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Wskazuje znak początek bloku funkcji|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, i `IActiveScriptDebug::GetScriptTextAttributes` metody zwracają jeden atrybut tekstu na znak, chyba że:  
  
-   Flaga GETATTRTYPE_DEPSCAN jest ustawiona, w którym to przypadku metoda może zwracać flagi SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP  
  
-   Flaga GETATTRFLAG_THIS jest ustawiona, w którym to przypadku metoda może zwracać flagi SOURCETEXT_ATTR_THIS  
  
-   Ustawiona flaga GETATTRFLAG_HUMANTEXT, w którym to przypadku metoda może zwracać flagi SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)