---
title: CommandPlacements Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7757716dc3f4c9e327a6145642e169c23e895c0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="commandplacements-element"></a>CommandPlacements Element
CommandPlacements element grupuje elementy CommandPlacement i inne grupy CommandPlacements.  
  
 CommandPlacements element jest opcjonalne. Nie polecenia, grupy lub menu muszą być zawarte w lokalizacji dodatkowej, nie trzeba umieścić w tej sekcji w pliku vsct.  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
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
|CommandPlacements|Grupuje elementy CommandPlacement i inne grupy CommandPlacements.|  
|[CommandPlacement Element](../extensibility/commandplacement-element.md)|Włącza przyciski, grup i menu do uwzględnienia w więcej niż jedną grupę lub menu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable Element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń.|  
  
## <a name="example"></a>Przykład  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CommandPlacement Element](../extensibility/commandplacement-element.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)