---
title: Interfejs IActiveScriptParseProcedureOld | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interfejs IActiveScriptParseProcedureOld
Umożliwia tekst kod źródłowy dla procedury do dodania do skryptu. Interpretowany języków skryptów, które nie mają niezależne środowisko tworzenia raportów, takich jak VBScript, zapewnia alternatywny mechanizm (inne niż `IActiveScriptParse` lub `IPersist*`) można dodać skrypt procedury z przestrzenią nazw.  
  
> [!NOTE]
>  Ten interfejs jest przestarzały uzyskać `IActiveScriptParseProcedure` interfejsu.  
  
## <a name="methods"></a>Metody  
 Oprócz dziedziczone z metody `IUnknown`, `IActiveScriptParseProcedureOld` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizuje procedury podanego kodu i dodaje procedurę do przestrzeń nazw.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)