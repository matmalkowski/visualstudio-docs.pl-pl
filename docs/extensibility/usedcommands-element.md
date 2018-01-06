---
title: UsedCommands Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 35b8821a76926da6ea9cab8ca61ef8f62e5ec72d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="usedcommands-element"></a>UsedCommands Element
UsedCommands element grupuje elementy UsedCommand i inne grupy UsedCommands.  
  
 UsedCommands element jest opcjonalne. Nie wywołuj poleceń zdefiniowanych poza pakietu, nie trzeba umieścić w tej sekcji w pliku vsct.  
  
## <a name="syntax"></a>Składnia  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
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
|[UsedCommand, element](../extensibility/usedcommand-element.md)|Polecenie, które jest implementowany przez inny kod.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkich elementów, które reprezentują polecenia (na przykład elementów menu, menu Paski narzędzi i pola kombi), które zawiera pakiet VSPackage zintegrowane środowisko programistyczne (IDE).|  
  
## <a name="example"></a>Przykład  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [UsedCommand Element](../extensibility/usedcommand-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)