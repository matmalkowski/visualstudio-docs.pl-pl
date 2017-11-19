---
title: IActiveScriptParseProcedure32 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Jeśli aparat skryptu systemu Windows zezwala na tekst kod źródłowy dla procedury do dodania do skryptu, implementuje `IActiveScriptParseProcedure32` interfejsu. Dla interpretowany języków skryptów, które mają nie niezależne środowisko tworzenia raportów, takich jak VBScript, zapewnia alternatywny mechanizm (inne niż `IActiveScriptParse32` lub `IPersist`*) można dodać skrypt procedury do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analizuje procedury podanego kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)