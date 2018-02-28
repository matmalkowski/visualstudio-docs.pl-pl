---
title: IActiveScriptParseProcedure | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77aaa60942855a71f7d71037fbefb06462336a13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Jeśli aparat skryptu systemu Windows zezwala na tekst kod źródłowy dla procedury do dodania do skryptu, implementuje `IActiveScriptParseProcedure` interfejsu. Dla interpretowany języków skryptów, które mają nie niezależne środowisko tworzenia raportów, takich jak VBScript, zapewnia alternatywny mechanizm (inne niż `IActiveScriptParse` lub `IPersist`*) można dodać skrypt procedury do przestrzeni nazw.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analizuje procedury podanego kodu i dodaje procedurę do przestrzeni nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)