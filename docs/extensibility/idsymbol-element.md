---
title: IDSymbol, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d88acb221abfc26c45c9002abb92f704936334b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500384"
---
# <a name="idsymbol-element"></a>IDSymbol, element
`IDSymbol` Element zawiera identyfikator pary GUID:ID, który reprezentuje menu, grupy lub polecenia. Identyfikator GUID, który jest dostarczany z obiektu nadrzędnego `GuidSymbol` elementu. `IDSymbol` Element ma `name` atrybut, który zawiera przyjazną nazwę dla Identyfikatora, który jest zawarty w `value` atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagane. Nazwa symbolu identyfikator.|  
|value|Wymagane. Wartość liczbowa Identyfikatora symbolu identyfikator.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[GuidSymbol, element](../extensibility/guidsymbol-element.md)|Zawiera unikatowy identyfikator GUID pary GUID:ID, który reprezentuje menu, grupy lub polecenia. Grupy `IDSymbol` elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `IDSymbol` elementu w danym `GuidSymbol` element musi mieć unikatową `value`. Jednak `IDSymbol` elementy, które ma takie same wartości może znajdować się w pakiecie, tak długo, jak długo mają różne elementy nadrzędne.  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)