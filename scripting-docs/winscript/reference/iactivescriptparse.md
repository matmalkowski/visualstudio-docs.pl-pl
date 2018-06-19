---
title: IActiveScriptParse | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793342"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Jeśli skrypt Windows aparat umożliwia nieprzetworzony tekst skryptlety kodu do dodania do skryptu lub umożliwia tekst wyrażenia do obliczenia w czasie wykonywania, implementuje `IActiveScriptParse` interfejsu. Dla interpretowany języków skryptów, które mają nie niezależne środowisko tworzenia raportów, takich jak VBScript, zapewnia alternatywny mechanizm (inne niż `IPersist*`) można pobrać kodu skryptu do aparatu skryptów i dołączyć fragmenty skryptu do różnych obiektów zdarzenia.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicjuje aparatu skryptów.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Dodaje skryptlet kodu do skryptu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analizuje skryptlet podanego kodu, dodawanie deklaracji w obszarze nazw i oceny kodu zależnie od potrzeb.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)