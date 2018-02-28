---
title: "Jserrorcode — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsErrorCode
helpviewer_keywords:
- JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jserrorcode-enumeration"></a>JsErrorCode — Wyliczenie
Zwrócony kod błędu z Chakra hosting interfejsu API.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|Kontekst nie można umieścić w stan debugowania, ponieważ jest on już w stanie debugowania.|  
|`JsErrorAlreadyProfilingContext`|Kontekst nie można uruchomić profilowania, ponieważ jest już profilowania.|  
|`JsErrorArgumentNotObject`|Hostingu interfejs API, który działa na wartości obiektu została wywołana z wartości niebędących obiektami.|  
|`JsErrorBadSerializedScript`|Użyto nieprawidłowy skrypt serializacji lub serializacji skryptu została wykonana serializacja przy użyciu innej wersji aparatu Chakra.|  
|`JsErrorCannotDisableExecution`|Środowisko uruchomieniowe nie obsługuje skryptów niezawodny przerwania.|  
|`JsErrorCannotSerializeDebugScript`|Nie można zserializować skryptów w kontekstach debugowania.|  
|`JsErrorCategoryEngine`|Kategoria błędów odnosi się do błędów występujących w ramach samego aparatu.|  
|`JsErrorCategoryFatal`|Kategoria błędów, które są krytyczne i oznaczają błąd aparatu.|  
|`JsErrorCategoryScript`|Kategorii błędów, które odnoszą się do błędów w skrypcie.|  
|`JsErrorCategoryUsage`|Kategoria błędów odnosi się do niepoprawne użycie interfejsu API samej siebie.|  
|`JsErrorFatal`|Wystąpił błąd krytyczny w aparacie.|  
|`JsErrorHeapEnumInProgress`|Wyliczenie sterty jest obecnie przetwarzane w kontekście skryptu.|  
|`JsErrorIdleNotEnabled`|Powiadomienie bezczynności przy hosta nie włączono przetwarzanie w stanie bezczynności.|  
|`JsErrorInDisabledState`|Środowisko wykonawcze jest w stanie wyłączenia.|  
|`JsErrorInExceptionState`|Aparat jest w stanie wyjątku i dopóki nie zostanie wyczyszczona wyjątku nie można wywołać nie interfejsów API.|  
|`JsErrorInObjectBeforeCollectCallback`|Operacja nie jest obsługiwana w obiekcie przed zbieranie wywołania zwrotnego.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsErrorInProfileCallback`|Kontekst skryptu jest w trakcie wywołania zwrotnego profilu.|  
|`JsErrorInThreadServiceCallback`|Wywołanie zwrotne wątku usługi jest obecnie przetwarzane.|  
|`JsErrorInvalidArgument`|Nieprawidłowy argument hostingu interfejsu API.|  
|`JsErrorNoCurrentContext`|Hostingu API wymaga, aby kontekst bieżącego, ale nie jest bieżący kontekst.|  
|`JsErrorNotImplemented`|Hostingu API nie została jeszcze zaimplementowana.|  
|`JsErrorNullArgument`|Argument hostingu API miał wartość null w kontekście, których nie jest dozwolone wartości null.|  
|`JsErrorObjectNotInspectable`|Obiekt nie może być odkodowany do `IInspectable` wskaźnika.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsErrorOutOfMemory`|Aparat Chakra zabrakło pamięci.|  
|`JsErrorPropertyNotSymbol`|Hostingu interfejs API, który działa na symbol identyfikatory właściwości, ale została wywołana z identyfikatorem właściwości z systemem innym niż symbol. Kod błędu został zwrócony przez `JsGetSymbolFromPropertyId` Jeśli funkcja jest wywoływana z identyfikatorem właściwości bez symboli.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsErrorPropertyNotString`|Hostingu interfejs API, który działa na identyfikatory właściwości ciągów, ale została wywołana z identyfikatorem właściwości innych niż ciąg. Kod błędu został zwrócony przez istniejące `JsGetPropertyNamefromId` Jeśli funkcja jest wywoływana z identyfikatorem właściwości innych niż ciąg.<br /><br /> Ta wartość wyliczenia jest obsługiwana tylko w trybie krawędzi.|  
|`JsErrorRuntimeInUse`|Nie można usunąć środowiska uruchomieniowego, który jest używany.|  
|`JsErrorScriptCompile`|Nie można skompilować kodu JavaScript.|  
|`JsErrorScriptEvalDisabled`|Skrypt został zakończony, ponieważ próbowano zastosować `eval` lub `function` i eval została wyłączona.|  
|`JsErrorScriptException`|JavaScript Wystąpił wyjątek podczas uruchamiania skryptu.|  
|`JsErrorScriptTerminated`|Skrypt został zakończony z powodu żądanie wstrzymania środowiska wykonawczego.|  
|`JsErrorWrongRuntime`|Hostingu API została wywołana z obiektu utworzonego na różne środowiska wykonawczego języka JavaScript.|  
|`JsErrorWrongThread`|Hostingu API została wywołana w złym wątku.|  
|`JsNoError`|Powodzenie kod błędu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)