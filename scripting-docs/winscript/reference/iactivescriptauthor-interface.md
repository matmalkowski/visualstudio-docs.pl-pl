---
title: Interfejs IActiveScriptAuthor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793324"
---
# <a name="iactivescriptauthor-interface"></a>Interfejs IActiveScriptAuthor
Reprezentuje tworzenia usług, w tym IntelliSense i sortowanie danych.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IActiveScriptAuthor` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Dodaje nazwę elementu głównego poziomu do skryptu tworzenia aparatu przestrzeni nazw. A *elementu poziomu głównego* jest obiektem, który może zawierać właściwości i metody, a zawierających można również źródłem zdarzenia.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Dodaje skryptlet kodu jako element podrzędny elementu poziomu głównego `IScriptNode` obiektu. Na hoście w pełni kwalifikowanej nazwy skryptletu może mieć tylko dwa poziomy.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Dodaje bibliotekę typów do przestrzeni nazw dla skryptu.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Zwraca zestaw znaków wykonania dla kontekstu żądanego ukończenia.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Zwraca skryptletu, który ma określone atrybuty.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Zwraca typu informacji i pozycji zakotwiczenia dla danego znaku w bloku kodu. IntelliSense, wykazy globalne i porady parametru zapewnia informacje dla elementu członkowskiego.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Zwraca informacje o języku.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Zwraca `IScriptNode` korzeń drzewa skryptu autora.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Zwraca atrybuty tekstu skryptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Zwraca atrybuty tekstu w bloku skryptu.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Zwraca wartość wskazującą, czy dany znak należy zatwierdzić uzupełniania instrukcji przez aplikację.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizuje tekst skryptu, dodaje tekst do tworzenia skryptu tworzenia aparatu i tworzy `IScriptEntry` obiekt, który odpowiada blok skryptu.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Usuwa `NamedItem` obiektu z przestrzeni nazw, tworzenia aparatu skryptu.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Usuwa bibliotekę typów w skrypcie tworzenia aparatu przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)