---
title: IDSymbol Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d05dd013be9a3d6c4a173a5c7abc7a01ef2d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idsymbol-element"></a>IDSymbol Element
`IDSymbol` Element zawiera identyfikator pary GUID:ID, który reprezentuje menu, grupy lub polecenie. Identyfikator GUID pochodzi z obiektu nadrzędnego `GuidSymbol` elementu. `IDSymbol` Element ma `name` atrybut, który udostępnia przyjazną nazwę dla Identyfikatora, który jest zawarty w `value` atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagany. Nazwa symbolu identyfikator.|  
|value|Wymagany. Wartość liczbowa identyfikator ID symbolu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[GuidSymbol Element](../extensibility/guidsymbol-element.md)|Zawiera unikatowy identyfikator GUID pary GUID:ID, który reprezentuje menu, grupy lub polecenie. Grupy `IDSymbol` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `IDSymbol` elementu w danym `GuidSymbol` element musi mieć unikatową `value`. Jednak `IDSymbol` elementów, które mają identyczne wartości może istnieć w pakiecie tak długo, jak długo mają różnych elementów nadrzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)