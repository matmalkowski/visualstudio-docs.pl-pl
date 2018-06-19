---
title: CommandTable Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f2dd2ebd076d4225adc86e5ba0cdc9af6ca40df
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100419"
---
# <a name="commandtable-element"></a>CommandTable Element
CommandTable jest elementem głównym pliku vsct. To jest plik definiujący rzeczywisty układ i typ poleceń, które zawiera pakiet VSPackage do środowiska IDE. Polecenia może zawierać elementy menu, menu, paski narzędzi i pola kombi. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|xmlns|Wymagany. Przestrzenie nazw XML:<br /><br /> xmlns = "http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns:xs = "http://www.w3.org/2001/XMLSchema"|  
|język|Opcjonalny. Atrybut języka można określić domyślny język wszystkich \<ciągów > elementów w tabeli poleceń.  Jeśli język nie jest określona, zostanie użyty język bieżącego procesu:<br /><br /> język = "en-us"|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Extern, element](../extensibility/extern-element.md)|Opcjonalny. Zawiera dyrektywy preprocesora dla kompilatora.|  
|[Include, element](../extensibility/include-element.md)|Opcjonalny. Zawiera ścieżki do plików do uwzględnienia w kompilacji.|  
|[Define, element](../extensibility/define-element.md)|Opcjonalny. Określa symbol podanej nazwy i wartości.|  
|[Commands, element](../extensibility/commands-element.md)|Opcjonalny. Definiowanie wszystkie polecenia dla pakiet VSPackage, który zawiera wszystkie elementy z elementu nadrzędnego.|  
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Opcjonalny. Określa, gdzie na pasku poleceń, polecenia zostaną umieszczone.|  
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|Opcjonalny. Określa statyczne widoczności poleceń i pasków narzędzi.|  
|[KeyBindings, element](../extensibility/keybindings-element.md)|Opcjonalny. Określa kombinacje klawiszy skrótu dla polecenia.|  
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Opcjonalny. Umożliwia opcjonalnie implementacji wersja funkcji pierwotnie oferowanych przez inne pakiety VSPackage pakiet VSPackage.|  
|[Symbols, element](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcjonalny. Zawiera wszystkie dane symbol — identyfikatory GUID, identyfikatory i tak dalej — dla kompilatora.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)