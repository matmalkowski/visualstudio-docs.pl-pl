---
title: Polecenie Element flagi | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cc69edbe0865953d242967490a0852c9da4942b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="command-flag-element"></a>Polecenie flagi elementu
Modyfikuje jego elementu nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższej sekcji opisano wartości elementów prawidłową.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Wartość|Opis|  
|-----------|-----------------|  
|AllowParams|Wskazuje, czy użytkownicy mogą wprowadzać parametry polecenia w **polecenia** okna po wpisaniu nazwy kanonicznej polecenia.<br /><br /> Ważny do:`Button`|  
|AlwaysCreate|Menu jest tworzony, nawet jeśli go nie ma grup ani przycisków.<br /><br /> Ważny do:`Menu`|  
|CaseSensitive|Wpisy użytkownika jest rozróżniana wielkość liter.<br /><br /> Ważny do:`Combo`|  
|CommandWellOnly|Jeśli polecenie nie jest wyświetlany w menu najwyższego poziomu i ma być możliwe do dostosowania dodatkowe powłoki, na przykład dla powiązania go do skrótu klawiaturowego, należy zastosować tę flagę. Po zainstalowaniu pakietu VSPackage można dostosować tych poleceń, otwierając **opcje** okno dialogowe, a następnie edytując położenie polecenia w obszarze **środowiska klawiatury** kategorii. Ta flaga nie ma wpływu na umieszczanie w menu skrótów, paski narzędzi, kontrolerów menu i podmenu.<br /><br /> Dotyczy: `Button`,`Combo`|  
|DefaultDisabled|Domyślnie polecenie jest wyłączona, jeśli pakiet VSPackage, który implementuje on nie został załadowany lub `QueryStatus` nie zostanie wywołana metoda.<br /><br /> Dotyczy: `Button`,`Combo`|  
|DefaultDocked|Zadokowane domyślnie. To ustawienie nie ma zastosowanie do pasków narzędzi, ponieważ są one zawsze zadokowane.|  
|DefaultInvisible|Domyślnie to polecenie jest niewidoczny, jeśli pakiet VSPackage, który implementuje on nie został załadowany lub `QueryStatus` nie zostanie wywołana metoda.<br /><br /> Zaleca się połączyć z tym `DynamicVisibility` flagi.<br /><br /> Dotyczy: `Button`, `Combo`,`Menu`|  
|DontCache|Środowisko projektowe nie będzie buforować `QueryStatus` wyników metod dla tego polecenia.<br /><br /> Menu ta wartość informuje kontrolera menu nie do pamięci podręcznej tekst jego elementów menu. Użyj tej flagi, jeśli zawiera menu dynamiczne elementy lub elementy mające dynamiczny tekst.<br /><br /> Dotyczy: `Button`,`Menu`|  
|DynamicItemStart|Wskazuje początek listy dynamicznych. Dzięki temu środowiska do tworzenia listy kolejno wywołując `QueryStatus` metody dla elementów listy, dopóki nie zostanie zwrócona flagi OLECMDERR_E_UNSUPPORTED. Działa to również dla elementów, takich jak ostatnio używanych (MRU) listy i wyświetla okno.<br /><br /> Ważny do:`Button`|  
|DynamicVisibility|Widoczność polecenia można zmienić za pomocą `QueryStatus` metody lub za pomocą identyfikatora GUID, który znajduje się w kontekście `VisibilityConstraints` sekcji.<br /><br /> Ma zastosowanie do poleceń, które są wyświetlane w menu i pasków narzędzi okna narzędzia, ale nie na paski narzędzi najwyższego poziomu, które znajdują się w oknie głównym. Elementy paska narzędzi najwyższego poziomu można wyłączać, ale nie jest to ukryty, gdy flaga OLECMDF_INVISIBLE jest zwracany z `QueryStatus` metody. Może być ukryte poleceń narzędzi, które pojawiają się na paskach narzędzi okna narzędzia.<br /><br /> W menu ta flaga również oznacza, że go powinny w automatycznie ukryte, gdy jego elementy członkowskie są ukryte. Ta flaga jest zwykle przypisany do podmenu, ponieważ menu najwyższego poziomu już to zachowanie.<br /><br /> Ta flaga powinna być połączone z `DefaultInvisible` flagi.<br /><br /> Dotyczy: `Button`, `Combo`,`Menu`|  
|KlawiszeFiltru|Zobacz temat filtrowania klucze w obszarze [kombi Element](../extensibility/combo-element.md).<br /><br /> Ważny do:`Combo`|  
|FixMenuController|Jeśli w tym poleceniu znajduje się na kontrolerze menu, to polecenie jest zawsze domyślnie; oznacza to, że polecenie wybrano zawsze, gdy zaznaczony jest przycisk menu kontrolera. Jeśli kontroler menu ma `TextIsAnchorCommand` Flaga, a następnie kontroler menu przyjmuje również jego tekstu polecenia, który ma `FixMenuController` flagi.<br /><br /> Powinien mieć tylko jedno polecenie na kontrolerze menu `FixMenuController` flagi. Jeśli tak jest oznaczony jako więcej niż jednego polecenia, ostatniego polecenia w menu staje się polecenie domyślne.<br /><br /> Ważny do:`Button`|  
|IconAndText|Pokaż ikonę i tekst w menu i paska narzędzi.<br /><br /> Dotyczy: `Button`, `Combo`,`Menu`|  
|NoAutoComplete|Funkcja automatycznego zakończenia jest wyłączona.<br /><br /> Ważny do:`Combo`|  
|NoButtonCustomize|Nie umożliwiają użytkownikowi Dostosowywanie tego przycisku.<br /><br /> Dotyczy: `Button`,`Combo`|  
|NoKeyCustomize|Nie należy włączać Dostosowywanie klawiatury.<br /><br /> Dotyczy: `Button`,`Combo`|  
|NoShowOnMenuController|To polecenie znajduje się na kontrolerze menu, polecenia nie są wyświetlane na liście rozwijanej.<br /><br /> Ważny do:`Button`|  
|NotInTBList|Nie ma na liście dostępnych pasków narzędzi. Jest to prawidłowa tylko dla typów menu paska narzędzi.<br /><br /> Ważny do:`Menu`|  
|NoToolbarClose|Użytkownik nie może zamknąć paska narzędzi. Jest to prawidłowa tylko dla typów menu paska narzędzi.<br /><br /> Ważny do:`Menu`|  
|PICT|Pokaż tylko ikonę na pasku narzędzi, ale tylko tekst w menu. Jeśli brak określonych ikon, pokazuje puste miejsce aktywne na pasku narzędzi.<br /><br /> Ważny do:`Button`|  
|PostExec|Powoduje, że polecenie bez blokowania. Środowisko projektowe różni się wykonanie do momentu zakończenia wszystkich zapytań przetwarzania wstępnego.<br /><br /> Ważny do:`Button`|  
|RouteToDocs|Polecenie jest kierowany do aktywnego dokumentu.<br /><br /> Ważny do:`Button`|  
|StretchHorizontally|Ta flaga jest ustawiona, szerokość staje się minimalną szerokość pola kombi, a jeśli ma miejsca na pasku narzędzi, pola kombi zostanie rozciągnięty w celu wypełnienia dostępnego miejsca. Dzieje się tak tylko wtedy, gdy pasek narzędzi w poziomie jest zadokowany, i tylko jedno pole kombi na pasku narzędzi można użyć flagi (flaga jest ignorowana na wszystkich oprócz pierwszego pola kombi).<br /><br /> Ważny do:`Combo`|  
|TextMenuUseButton|Użyj `ButtonText` pole menu. W polu domyślny jest `MenuText` jeśli je określono.<br /><br /> Ważny do:`Button`|  
|TextChanges|Tekst polecenia lub menu można zmieniać w czasie wykonywania, zwykle za pomocą `QueryStatus` metody.<br /><br /> Dotyczy: `Button`,`Menu`|  
|TextChangesButton|Ważny do:`Button`|  
|TextIsAnchorCommand|W przypadku kontrolera menu Tekst menu jest pobierana z polecenie domyślne (zakotwiczenia). Polecenie zakotwiczenia jest ostatnie polecenie zaznaczone lub zablokowane. Jeśli ta flaga nie jest ustawiona, kontroler menu używa własnego `MenuText` pola. Jednak kliknięcie kontrolera menu nadal umożliwia ostatniego wybranego polecenia z tego kontrolera.<br /><br /> Firma Microsoft zaleca, aby połączyć tę flagę z `TextChanges` flagi.<br /><br /> Ta flaga dotyczy tylko menu typu MenuController lub MenuControllerLatched.<br /><br /> Ważny do:`Menu`|  
|TextMenuCtrlUseMenu|Użyj `MenuText` pole na kontrolerach menu. W polu domyślny jest `ButtonText`.<br /><br /> Ważny do:`Button`|  
|TextMenuUseButton|Użyj `ButtonText` pole menu. W polu domyślny jest `MenuText` jeśli je określono.<br /><br /> Ważny do:`Button`|  
|TextOnly|Pokaż tylko tekst na pasku narzędzi lub menu, ale bez ikony, nawet wtedy, gdy określono ikony.<br /><br /> Ważny do:`Button`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element przycisków](../extensibility/buttons-element.md)|Zawiera grupę [Button Element](../extensibility/button-element.md) elementów.|  
|[Element menu](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakiet VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)