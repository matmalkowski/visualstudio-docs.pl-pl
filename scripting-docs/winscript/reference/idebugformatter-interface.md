---
title: Interfejs IDebugFormatter | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97f95aa1ecb91f6caca187939a79a6f09cd2108f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformatter-interface"></a>Interfejs IDebugFormatter
Umożliwia języka lub IDE dostosować konwersji wartości z WARIANTU lub typy VARTYPE i ciągów.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugFormatter` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Zwraca ciąg reprezentujący wartość VARIANT.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Zwraca typ VARIANT zawierający dany ciąg znaków.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Zwraca ciąg reprezentujący podana wartość VARTYPE.|