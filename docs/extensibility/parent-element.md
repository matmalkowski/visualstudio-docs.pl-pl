---
title: Element nadrzędny elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 795654925a92f3e9ac0718e070e85c0f4f7f21c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137108"
---
# <a name="parent-element"></a>Element nadrzędny
Element nadrzędny, przycisk lub pola kombi mogą być tylko grupy. Element nadrzędny menu lub grupy może być innych menu lub grupy. W [CommandPlacement Element](../extensibility/commandplacement-element.md), ten element jest wymagany; w innych przypadkach jest opcjonalna. W przypadku pominięcia tego elementu nadrzędnego `Group_Undefined:0` będzie niejawnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator polecenia dla identyfikatora GUID/identyfikator GUID.|  
|identyfikator|Wymagany. Identyfikator GUID/ID identyfikator polecenia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkich elementów, które reprezentują poleceń, które zawiera pakiet VSPackage zintegrowane środowisko programistyczne (IDE). Na przykład elementów menu, menu Paski narzędzi i pola kombi.|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupy [Button Element](../extensibility/button-element.md) elementów.|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakiet VSPackage.|  
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy polecenia pakiet VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)