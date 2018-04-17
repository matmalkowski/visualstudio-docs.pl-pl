---
title: Element kombi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca91102467755610144e4d24405e89ace5a013b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="combo-element"></a>Element kombi
Definiuje polecenia, które są wyświetlane w polu kombi. Istnieją cztery rodzaje pola kombi, w następujący sposób: typu pole kombi, DynamicCombo IndexCombo i MRUCombo.  
  
## <a name="syntax"></a>Składnia  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikator GUID/identyfikator polecenia.|  
|identyfikator|Wymagany. Identyfikator GUID/identyfikator identyfikator polecenia.|  
|defaultWidth|Wymagany. Liczba całkowita, która określa szerokość piksela dla pola kombi.|  
|idCommandList|Wymagany. Identyfikator, który jest wysyłany do docelowego polecenie active można pobrać listy elementów, które mają być wyświetlane w polu kombi. Identyfikator będzie w tym samym zakresie GUID jako formant.|  
|priorytet|Opcjonalny. Wartość liczbowa określa priorytet.|  
|— typ|Opcjonalny. Wartość wyliczany określający typ przycisku.<br /><br /> Jeśli nie zostanie podany, używa przycisku.<br /><br /> Typu pole kombi<br /> Pakiet VSPackage jest odpowiedzialny za wypełnianie zawartość tego pola kombi. Użytkownik nie może niczego wpisywać w polu tekstowym w tym listy rozwijanej.<br /><br /> DynamicCombo<br /> Pakiet VSPackage jest odpowiedzialny za wypełnianie zawartość tego pola kombi. Użytkownik może edytować ten kombi i również zaznaczyć w niej elementów.<br /><br /> IndexCombo<br /> Taki sam jak DynamicCombo, ale wywołuje indeksu elementu zamiast jego tekstu.<br /><br /> MRUCombo<br /> Wypełniony przez zintegrowane środowisko programistyczne (IDE) imieniu pakiet VSPackage.  Użytkownik może edytować w tym polu kombi. IDE pamięta maksymalnie 16 ostatnie wpisy dla pola kombi.<br /><br /> Gdy użytkownik wybiera element w polu kombi lub wprowadza inną, IDE powiadamia odpowiedni pakiet VSPackage.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalny. Elementu nadrzędnego przycisku.|  
|CommandFlag|Wymagany. Zobacz [polecenia Element flagi](../extensibility/command-flag-element.md). Poniżej znajdują się prawidłowe wartości CommandFlag dla przycisku.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -KlawiszeFiltru<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Ciągi|Wymagany. Zobacz [ciągi elementu](../extensibility/strings-element.md). Element podrzędny ButtonText musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Commands, element](../extensibility/commands-element.md)|Reprezentuje kolekcję poleceń na pasku narzędzi pakiet VSPackage.|  
  
## <a name="example"></a>Przykład  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)