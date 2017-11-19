---
title: "Element nadrzędny elementu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc66e193b13ac6baf9d6089483a1281c2d6a59ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
|[CommandTable Element](../extensibility/commandtable-element.md)|Definiuje wszystkich elementów, które reprezentują poleceń, które zawiera pakiet VSPackage zintegrowane środowisko programistyczne (IDE). Na przykład elementów menu, menu Paski narzędzi i pola kombi.|  
|[Element przycisków](../extensibility/buttons-element.md)|Grupy [Button Element](../extensibility/button-element.md) elementów.|  
|[Element menu](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakiet VSPackage.|  
|[Element grupy](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy polecenia pakiet VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)