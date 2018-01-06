---
title: Element grupy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec5ff5f5bafec14099e5b10b9861be5936b75009
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="group-element"></a>Elementu grupy
Definiuje grupę polecenia pakiet VSPackage.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikator GUID/identyfikator polecenia.|  
|identyfikator|Wymagany. Identyfikator GUID/identyfikator identyfikator polecenia.|  
|priorytet|Opcjonalny. Wartość liczbowa określa priorytet.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalny. Elementu nadrzędnego przycisku.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy polecenia pakiet VSPackage.|  
  
## <a name="example"></a>Przykład  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>  
</Group>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)