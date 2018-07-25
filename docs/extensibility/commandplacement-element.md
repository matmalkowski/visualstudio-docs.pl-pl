---
title: CommandPlacement, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5da750b3f33127fdcfdf2e2a76d4df1556561b2
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232432"
---
# <a name="commandplacement-element"></a>CommandPlacement, element
CommandPlacement, element umożliwia przyciski, grup i menu, mają zostać uwzględnione w więcej niż jednej grupie lub menu. Przy użyciu elementu CommandPlacement, nie trzeba całkowicie ponownie zdefiniować te elementy, aby zmodyfikować wygląd interfejsu użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie wielokrotnego użytku grup przycisków](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagane. Identyfikator guid zestawu poleceń, zgodnie z definicją w [Symbols, element](../extensibility/symbols-element.md).|  
|identyfikator|Wymagane. Identyfikator menu, grupy lub polecenie, aby umieścić zgodnie z definicją w `Symbols Element`.|  
|priorytet|Wymagane. Określa położenie visual elementu w jego elementu nadrzędnego.|  
|Warunek|Opcjonalna. Zobacz [warunkowego Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Wymagane. Menu lub grupy, która hostuje element które mają być umieszczone.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Określa grupy CommandPlacements i CommandPlacement elementów.|  
  
## <a name="example"></a>Przykład  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [CommandPlacements, element](../extensibility/commandplacements-element.md)   
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
