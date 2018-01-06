---
title: CommandPlacement Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6a5c8d9220b0cd2c0dddfee283d222f4efb9ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="commandplacement-element"></a>CommandPlacement Element
CommandPlacement element włącza przyciski, grup i menu do uwzględnienia w więcej niż jedną grupę lub menu. Za pomocą elementu CommandPlacement, nie trzeba całkowicie ponownie zdefiniować te elementy, aby zmodyfikować wygląd interfejsu użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie wielokrotnego użytku grup przycisków](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator guid zestawu poleceń, zgodnie z definicją w [Element symbole](../extensibility/symbols-element.md).|  
|identyfikator|Wymagany. Identyfikator menu, grupy lub polecenie, aby umieścić zgodnie z definicją w `Symbols Element`.|  
|priorytet|Wymagany. Określa położenie visual elementu w jego elementu nadrzędnego.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Wymagany. Menu lub grupy, która hostuje element do umieszczenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Określa grupę CommandPlacements i CommandPlacement elementów.|  
  
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
 [CommandPlacements Element](../extensibility/commandplacements-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)