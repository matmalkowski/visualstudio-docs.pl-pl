---
title: Przycisk elementu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5af5dce3edf1ac2910af5f8d593ed8e316cff721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="button-element"></a>Button Element
Definiuje element, który użytkownik może interakcyjnie przeprowadzić. Przyciski może być różnego rodzaju: przycisk, przycisk menu i SplitDropDown.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikator GUID/identyfikator polecenia.|  
|identyfikator|Wymagany. Identyfikator GUID/identyfikator identyfikator polecenia.|  
|priorytet|Opcjonalny. Wartość liczbowa określa priorytet.|  
|— typ|Opcjonalny. Wartość wyliczenia, która określa rodzaj przycisku.<br /><br /> Jeśli nie zostanie podany, używa przycisku.<br /><br /> Przycisk<br /> Standardowe polecenia pojawi się na paskach narzędzi (zazwyczaj jako przycisk odpowiednikiem), menu i menu kontekstowego.<br /><br /> Przycisk menu<br /> Element menu, który nie należy wykonywać polecenia, ale tworzy innym menu.<br /><br /> SplitDropDown<br /> Formanty, takie jak przyciski Cofnij i ponów na standardowym pasku narzędzi w programie Microsoft Word.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Parent, element](../extensibility/parent-element.md)|Opcjonalny. Elementu nadrzędnego przycisku.|  
|[Icon, element](../extensibility/icon-element.md)|Opcjonalny. Ikony skojarzone z przyciskiem.|  
|[Command Flag, element](../extensibility/command-flag-element.md)|Wymagany. Poniżej znajdują się prawidłowe wartości CommandFlag dla przycisku.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly.|  
|[Strings, element](../extensibility/strings-element.md)|Wymagany. Obiekt podrzędny [ButtonText elementu](../extensibility/buttontext-element.md) musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje elementy przycisku.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano przycisku w pliku vsct.  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)