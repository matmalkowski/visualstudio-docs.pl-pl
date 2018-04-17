---
title: Ciągi elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5994144f07b8af84f61d7833737f45593c551b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="strings-element"></a>Element ciągów
Element ciągi musi zawierać co najmniej **ButtonText** element podrzędny. Wszystkie elementy podrzędne są opcjonalne. Nieprawidłowy kod XML znaków, takich jak "&" i "<" musi być zakodowane jako jednostki ("&amp;"i"&lt;" i tak dalej).  
  
 Znak w ciągu tekstowego określa skrótu klawiaturowego dla polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|język|Opcjonalny. Język = ".".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|ButtonText|To pole i pięć następujących pól tekstowych w definicji poleceń umożliwiają określenie tekstu wyświetlanego w różnych menu. Domyślnie `ButtonText` pole jest wyświetlane w menu kontrolerów. `ButtonText` Pola staje się również domyślnie Jeśli pola tekstowe są puste. `ButtonText` Pola nie może być pusta, nawet jeśli nie określono innych pól tekstowych.|  
|ToolTipText|`ToolTipText` Pole określa tekst wyświetlany w etykietce narzędzia elementu menu.<br /><br /> Jeśli `ToolTipText` pole jest puste, `ButtonText` pole jest używane.|  
|MenuText|`MenuText` Pole określa tekst, który jest wyświetlany dla polecenia, jeśli znajduje się w menu głównym pasku narzędzi, w menu skrótów lub w podmenu. Jeśli `MenuText` pole jest puste, zintegrowane środowisko programistyczne (IDE) używa `ButtonText` pola. `MenuText` Pole może także służyć do lokalizacji.<br /><br /> Menu skrótów `MenuText` pole jest nazwa, która jest wyświetlana na pasku menu skrótów, co umożliwia dostosowywanie menu skrótów w IDE. W związku z tym można określonych w co nazwa z menu skrótów. na przykład użyć "Widget Menu skrótów pakietu" zamiast "Skrótów".<br /><br /> Jeśli `MenuText` pole nie zostanie określony, `ButtonText` pole jest używane.|  
|CommandName|`CommandName` Pole określa tekst wyświetlany w kategorii klawiatury w **polecenia** karcie **Dostosuj** okno dialogowe (dostępne, klikając **Dostosuj**na **narzędzia** menu).|  
|canonicalName|Angielski `CanonicalName` pole określa nazwę polecenia w angielskiej wersji językowej tekstu, który można wpisać w **polecenia** okno, aby wykonać elementu menu. Usuwa wszystkie znaki, które nie są litery, cyfry, podkreślenia i kropki osadzonego IDE. Ten tekst jest następnie łączony do `ButtonText` Aby zdefiniować polecenia. Na przykład **nowy projekt** na **pliku** polecenie File.NewProject staje się menu.<br /><br /> Jeśli język angielski `CanonicalName` pole nie zostanie określony, używa IDE `ButtonText` pola i pasków limit wszystkie z wyjątkiem litery, cyfry, podkreślenia i kropki osadzonego. Na przykład tekst przycisku "& Definiowanie polecenia..." staje się DefineCommands, gdzie handlowego "i", miejsce i wielokropek zostaną usunięte.<br /><br /> Jeśli `TextChanges` określono flagę i tekst polecenia jest zmieniany, odpowiadające jej polecenie, które są rozpoznawane przez **polecenia** okna nie zmienia; pozostaje forma kanoniczna oryginalnej `ButtonText` lub wjęzykuangielskim`CanonicalName` pól.|  
|LocCanonicalName|`LocCanonicalName` Pola zachowuje się tak samo język angielski `CanonicalName` pola umożliwia jednak tekst polecenia zlokalizowanych należy określić. Można określić obu pól kanonicznej. Ponieważ IDE analizuje tylko tekst wprowadzony w **polecenia** okno i skojarzone z poleceniem, zarówno w języku angielskim, jak i w innej niż angielska tekst może być skojarzony z tym samym poleceniu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Button, element](../extensibility/button-element.md)|Definiuje element, który użytkownik może interakcyjnie przeprowadzić.|  
|[Menu, element](../extensibility/menu-element.md)|Określa pojedynczy element menu.|  
|[Combo, element](../extensibility/combo-element.md)|Definiuje polecenia, które są wyświetlane w polu kombi.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)