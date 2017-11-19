---
title: IActiveScriptParse32 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Jeśli skrypt Windows aparat umożliwia nieprzetworzony tekst skryptlety kodu do dodania do skryptu lub umożliwia tekst wyrażenia do obliczenia w czasie wykonywania, implementuje `IActiveScriptParse32` interfejsu. Dla interpretowany języków skryptów, które mają nie niezależne środowisko tworzenia raportów, takich jak VBScript, zapewnia alternatywny mechanizm (inne niż `IPersist*`) można pobrać kodu skryptu do aparatu skryptów i dołączyć fragmenty skryptu do różnych obiektów zdarzenia.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Dodaje skryptlet kodu do skryptu.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicjuje aparatu skryptów.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analizuje skryptlet podanego kodu, dodawanie deklaracji w obszarze nazw i oceny kodu zależnie od potrzeb.|