---
title: Symbole elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87e9159e1e392ff242407b105589f4f33341b45b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="symbols-element"></a>Element symboli
Definiuje identyfikatory GUID oraz identyfikatorów, które są używane przez inne elementy VSCT. Dla niezarządzanego kodu, te informacje zazwyczaj pochodzą z pliki nagłówkowe, które są określone przez [zewnętrzny Element](../extensibility/extern-element.md). Zarządzany kod używa elementów podrzędnych elementu symbole, aby zdefiniować te informacje.  
  
 Po utworzeniu pliku vsct z istniejącego pliku .cto symbole zostanie wygenerowana jako elementy podrzędne elementu symboli. Aby uzyskać więcej informacji, zobacz [porady: tworzenie. Plik Vsct z istniejącego. Pliku Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
 Element symboli nie należy mylić z [zdefiniować Element](../extensibility/define-element.md), który definiuje pary nazwa wartość do użycia przez preprocesora.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Brak||  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|GuidSymbol|Określa symbol identyfikatora GUID. GuidSymbol ma dwa wymaganych atrybutów: nazwy i wartości. Nazwa jest nazwą symbolu, a wartość jest wartością identyfikatora GUID jako ciąg.<br /><br /> Na przykład:\<GuidSymbol name = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|IDSymbol|Określa symbol. IDSymbol ma dwa wymaganych atrybutów: nazwy i wartości. Nazwa jest nazwą symbolu, a wartość jest wartością symbolu jako ciąg.<br /><br /> Na przykład:\<IDSymbol name = "MyMenuGroup" value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Element główny pliku vsct.|  
  
## <a name="example"></a>Przykład  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)