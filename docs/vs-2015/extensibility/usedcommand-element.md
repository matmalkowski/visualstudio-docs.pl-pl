---
title: UsedCommand, Element | Dokumentacja firmy Microsoft
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
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78ab46c4524bb25563d407514aa0590e75feffaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684028"
---
# <a name="usedcommand-element"></a>UsedCommand, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [UsedCommand, Element](https://docs.microsoft.com/visualstudio/extensibility/usedcommand-element).  
  
Umożliwia pakietu VSPackage w celu dostępu do poleceń, która jest zdefiniowana w innym pliku vsct. Na przykład, jeśli Twoja pakietu VSPackage używa standardu **kopiowania** polecenia, która jest zdefiniowana przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] powłoki, możesz dodać polecenie menu lub pasek narzędzi bez jej ponownego wdrażania.  
  
## <a name="syntax"></a>Składnia  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagane. Identyfikator GUID pary identyfikator GUID, który identyfikuje polecenie.|  
|identyfikator|Wymagane. Identyfikator pary identyfikator GUID, który identyfikuje polecenie.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Grupuje elementy UsedCommand i inne grupy UsedCommands.|  
  
## <a name="remarks"></a>Uwagi  
 Dodając polecenie do `<UsedCommands>` informuje pakietu VSPackage elementu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiska, że pakietu VSPackage wymaga polecenia. Należy dodać `<UsedCommand>` elementu dla dowolnego polecenia wymaga pakietu nie została uwzględniona we wszystkich wersjach i konfiguracji programu Visual Studio. Na przykład, jeśli pakiet wywołuje polecenie, które są specyficzne dla języka Visual C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że dodasz `<UsedCommand>` elementu dla polecenia.  
  
## <a name="example"></a>Przykład  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [UsedCommands, Element](../extensibility/usedcommands-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

