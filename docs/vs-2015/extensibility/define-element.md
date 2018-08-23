---
title: Zdefiniuj Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76e44ccc221b0f11f30ed63de63f82634f726b79
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681423"
---
# <a name="define-element"></a>Define, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zdefiniować Element](https://docs.microsoft.com/visualstudio/extensibility/define-element).  
  
Definiuje symbol pary nazw i wartości. Ten symbol może zostać oceniony przez atrybuty warunkowe. Aby uzyskać więcej informacji, zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md). Zobacz też [symboli elementu](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Wymagane. Nazwa symbolu:<br /><br /> Nazwa = "Tryb"|  
|value|Wymagane. Wartość symbolu:<br /><br /> wartość = "Standardowy"|  
|Warunek|Opcjonalna. Aby uzyskać więcej informacji, zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń, które zapewnia pakietu VSPackage do zintegrowanego środowiska programistycznego (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|  
  
## <a name="example"></a>Przykład  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

