---
title: Nadrzędny Element | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9a66f9fff773fb9a9542de13ceb97ad8732c319b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39635859"
---
# <a name="parent-element"></a>Element nadrzędny
Element nadrzędny przycisk lub pola kombi mogą być tylko grupy. Nadrzędny menu lub grupa może być dowolnego menu lub grupę. W [CommandPlacement, element](../extensibility/commandplacement-element.md), ten element jest wymagany; w innych wystąpieniach jest opcjonalne. W przypadku pominięcia tego elementu nadrzędnego `Group_Undefined:0` będzie wynikać.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagane. Identyfikator polecenia dla identyfikatora GUID/identyfikator GUID.|  
|identyfikator|Wymagane. Identyfikator polecenia identyfikator GUID/ID.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń, które zapewnia pakietu VSPackage do zintegrowanego środowiska programistycznego (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupy [Button element](../extensibility/button-element.md) elementów.|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakietu VSPackage.|  
|[Element grupy](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy polecenia pakietu VSPackage.|  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)