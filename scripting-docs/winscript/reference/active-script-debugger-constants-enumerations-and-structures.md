---
title: Stałe debugera aktywnego skryptu, wyliczenia i struktury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bd41fe91fdf030b957d800248343198f2617018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792154"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury debugera aktywnego skryptu
Interfejsy funkcji aktywnego debugowania używają następujących stałych, wyliczeń i struktur.  
  
## <a name="constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury  
  
|Stałe|Opis|  
|---------------|-----------------|  
|[Stałe APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Wskazuje bieżący stan debugowania aplikacji i wątków.|  
|[Stałe DEBUG_TEXT](../../winscript/reference/debug-text-constants.md)|Flagi używane podczas opcji [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[Stałe TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)|Opisuje atrybuty dokumentu.|  
  
|Wyliczenia|Opis|  
|------------------|-----------------|  
|[Stałe APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Wskazuje bieżący stan debugowania aplikacji i wątków.|  
|[Wyliczenie APPLICATION_NODE_EVENT_FILTER](../../winscript/reference/application-node-event-filter-enumeration.md)|Wskazuje węzły, które mają być wykluczone za pomocą filtra.|  
|[Wyliczenie BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)|Wskazuje stan punktu przerwania.|  
|[Wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md)|Wskazuje powód przerwania.|  
|[Wyliczenie BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)|Opisuje sposób kontynuowania pracy po punkcie przerwania.|  
|[Wyliczenie DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)|Wskazuje, który typ ma zostać pobrany dla dokumentu.|  
|[Wyliczenie ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)|Opisuje sposób kontynuowania pracy po błędzie czasu wykonywania.|  
|[Wyliczenie JS_PROPERTY_ATTRIBUTES](../../winscript/reference/js-property-attributes-enumeration.md)|Określa atrybuty właściwości.|  
|[Wyliczenie JS_PROPERTY_MEMBERS](../../winscript/reference/js-property-members-enumeration.md)|Flagi określające typ informacji, które będą zwracane w żądaniu o dane elementów członkowskich obiektu.|  
|[Wyliczenie JsDebugReadMemoryFlags](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Flagi określające zachowanie podczas odczytu pamięci.|  
|[Wyliczenie SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md)|Wskazuje zestaw opcji lub funkcji dołączonego debugera.|  
|[Wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Wskazuje rodzaj zgłaszanego wyjątku.|  
|[Stałe SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)|Opisuje atrybuty pojedynczego znaku w tekście źródłowym.|  
  
|Struktury|Opis|  
|----------------|-----------------|  
|[Struktura DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)|Wylicza ramki stosu i scala dane wyjściowe z kilku modułów wyliczających w tym samym wątku.|  
|[Struktura JS_NATIVE_FRAME](../../winscript/reference/js-native-frame-structure.md)|Reprezentuje ramkę stosu.|  
|[Struktura JsDebugPropertyInfo](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Zawiera informacje o właściwości.|  
|[Struktura TEXT_DOCUMENT_ARRAY](../../winscript/reference/text-document-array-structure.md)|Zawiera zestaw dokumentów.|