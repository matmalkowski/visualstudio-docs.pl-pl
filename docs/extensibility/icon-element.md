---
title: Ikona elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f15dcfec5c89c6bf2b2ae68ea29e18890dc9187e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126880"
---
# <a name="icon-element"></a>Icon — Element
Atrybut guid tagu ikona jest identyfikatorem guid zdefiniowanych mapy bitowej.  Atrybut id zaznacza gniazda paska mapy bitowej. Ten element jest opcjonalny.  W przypadku pominięcia tego elementu wartość **guidOfficeIcon:msotcidNoIcon** będzie niejawnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator guid zdefiniowanych mapy bitowej.|  
|identyfikator|Wymagany. Wybiera gniazda paska mapy bitowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak.|Brak.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)