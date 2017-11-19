---
title: CommandTable Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4f1a906f545dcdbaefca7f5a38824a1f3259c97
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
|[Extern — Element](../extensibility/extern-element.md)|Opcjonalny. Zawiera dyrektywy preprocesora dla kompilatora.|  
|[Umieść Element](../extensibility/include-element.md)|Opcjonalny. Zawiera ścieżki do plików do uwzględnienia w kompilacji.|  
|[Zdefiniuj Element](../extensibility/define-element.md)|Opcjonalny. Określa symbol podanej nazwy i wartości.|  
|[Element poleceń](../extensibility/commands-element.md)|Opcjonalny. Definiowanie wszystkie polecenia dla pakiet VSPackage, który zawiera wszystkie elementy z elementu nadrzędnego.|  
|[CommandPlacements Element](../extensibility/commandplacements-element.md)|Opcjonalny. Określa, gdzie na pasku poleceń, polecenia zostaną umieszczone.|  
|[VisibilityConstraints Element](../extensibility/visibilityconstraints-element.md)|Opcjonalny. Określa statyczne widoczności poleceń i pasków narzędzi.|  
|[Element powiązania klawiszy](../extensibility/keybindings-element.md)|Opcjonalny. Określa kombinacje klawiszy skrótu dla polecenia.|  
|[UsedCommands Element](../extensibility/usedcommands-element.md)|Opcjonalny. Umożliwia opcjonalnie implementacji wersja funkcji pierwotnie oferowanych przez inne pakiety VSPackage pakiet VSPackage.|  
|[Element symboli](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcjonalny. Zawiera wszystkie dane symbol — identyfikatory GUID, identyfikatory i tak dalej — dla kompilatora.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)