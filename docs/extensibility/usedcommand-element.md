---
title: UsedCommand Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4888733abf142f6582706406decbea0bf84ce519
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139071"
---
# <a name="usedcommand-element"></a>UsedCommand Element
Włącza pakiet VSPackage umożliwiające dostęp do polecenia, który jest zdefiniowany w innym pliku vsct. Na przykład, jeśli VSPackage korzysta ze standardu **kopiowania** polecenia, który jest zdefiniowany przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłoki, można dodać polecenie menu lub pasek narzędzi bez ponownego wprowadzania.  
  
## <a name="syntax"></a>Składnia  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID pary identyfikator GUID, który identyfikuje polecenie.|  
|identyfikator|Wymagany. Identyfikator pary identyfikator GUID, który identyfikuje polecenie.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Grupuje elementy UsedCommand i inne grupy UsedCommands.|  
  
## <a name="remarks"></a>Uwagi  
 Dodając polecenie do `<UsedCommands>` informuje pakiet VSPackage elementu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska, że pakiet VSPackage wymaga polecenia. Należy dodać `<UsedCommand>` elementu dla dowolnego polecenia pakietu wymaga, aby nie może znajdować się w wszystkie wersje i konfiguracje programu Visual Studio. Na przykład, jeśli pakiet wymaga polecenia, które są specyficzne dla języka Visual C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że uwzględniasz `<UsedCommand>` elementu dla polecenia.  
  
## <a name="example"></a>Przykład  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [UsedCommands Element](../extensibility/usedcommands-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)