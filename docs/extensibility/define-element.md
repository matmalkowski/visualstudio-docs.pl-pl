---
title: Zdefiniuj Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b435c4e44391bbf477ed94fa96ee382613290530
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="define-element"></a>Zdefiniuj Element
Określa symbol pary nazw i wartości. Ten symbol oceną atrybuty warunkowe. Aby uzyskać więcej informacji, zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md). Zobacz też [symbole elementu](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagany. Nazwa symbolu:<br /><br /> Nazwa = "Tryb"|  
|value|Wymagany. Wartość symbolu:<br /><br /> wartość = "Standard"|  
|Warunek|Opcjonalny. Aby uzyskać więcej informacji, zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable Element](../extensibility/commandtable-element.md)|Definiuje wszystkich elementów, które reprezentują poleceń, które zawiera pakiet VSPackage zintegrowane środowisko programistyczne (IDE). Na przykład elementów menu, menu Paski narzędzi i pola kombi.|  
  
## <a name="example"></a>Przykład  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)