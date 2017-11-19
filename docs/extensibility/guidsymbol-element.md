---
title: GuidSymbol Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcad9882b1c72c15837529d736eeabff58f3826
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="guidsymbol-element"></a>GuidSymbol Element
`GuidSymbol` Element zawiera identyfikator GUID pary GUID:ID, który reprezentuje menu, grupy lub polecenie. Identyfikator pochodzi z `IDSymbol` element `GuidSymbol` elementu. `GuidSymbol` Element ma `name` atrybut, który udostępnia przyjazną nazwę dla identyfikatora GUID, który jest zawarty w `value` atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagany. Nazwa symbolu identyfikatora GUID.|  
|value|Wymagany. Identyfikator GUID symbolu identyfikatora GUID.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[IDSymbol Element](../extensibility/idsymbol-element.md)|Zawiera identyfikator pary GUID:ID, który reprezentuje menu, grupy lub polecenie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element symboli](../extensibility/symbols-element.md)|Grupy `GuidSymbol` elementów w pliku vsct.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle zawiera trzy pliku vsct `GuidSymbol` elementów w jego `Symbols` sekcji, jeden dla tego samego pakietu dla zestawu poleceń (kolekcja menu, grup i poleceń, które udostępnia pakiet) i jeden dla mapy bitowe, które zapewniają ikony dla przycisków i inne składniki wizualne. Każdy `IDSymbol` elementu w danym `GuidSymbol` element musi mieć unikatową `value`. Jednak `IDSymbol` elementów, które mają identyczne wartości może istnieć w pakiecie tak długo, jak długo mają różnych elementów nadrzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)