---
title: Element kombinacje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c729f92992ddea109a7024452457bd56d281b89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="combos-element"></a>Element kombinacje
Grupy [kombi Element](../extensibility/combo-element.md) elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element kombinacje](../extensibility/combos-element.md)|Grupuje elementy kombi.|  
|[Element kombi](../extensibility/combo-element.md)|Definiuje polecenia, które są wyświetlane w polu kombi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element poleceń](../extensibility/commands-element.md)|Reprezentuje kolekcję poleceń na pasku narzędzi pakiet VSPackage.|  
  
## <a name="example"></a>Przykład  
  
```  
<Combos>  
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
    defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    <Strings>  
      <ButtonText>Select Insert Options</ButtonText>  
    </Strings>  
  </Combo>  
  
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0500" type="DropDownCombo" defaultWidth="100"  
    idCommandList="cmdidGetInsertOptionsList">  
    <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    <Strings>  
      <ButtonText>Select Insert Options</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)