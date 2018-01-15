---
title: "Właściwości role domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6a2ae5a5e017980a6f7a5310ea3c76e49253249d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-domain-roles"></a>Właściwości ról w domenie
Właściwości w poniższej tabeli są skojarzone z rolą domeny. Aby uzyskać informacje o rolach domeny, zobacz [opis modeli, klasy i relacje](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Typ kolekcji|Jeśli ta rola ma liczebności 0.. * lub 1.. \*, ta właściwość dostosowuje typu ogólnego, który jest używany do przechowywania kolekcji łączy.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>jest używany|  
|Atrybuty niestandardowe|Atrybuty, które są określone w tym miejscu zostanie dodany jako atrybuty do klasy wygenerowanego kodu.|< Brak\>|  
|Właściwość jest można przeglądać|Jeśli `True`, a Jeśli liczebność relacji jest od 0 do 1 lub 1.. 1, można przeglądać właściwości roli użytkownika w **właściwości** okna. Właściwość Wyświetla nazwę elementu na drugim końcu łącza relacji.|`True`|  
|Jest Generator właściwości|Jeśli `True`, właściwości roli jest generowany dla tej roli, co umożliwia przenoszenie relacji w kodzie programu. Jeśli ustawisz to false, można przechodzenia relacji w sposób mniej wydajne, za pomocą metod statycznych relacji domeny.|`True`|  
|Modyfikator dostępu metody pobierającej właściwość|Modyfikator dostępu do metody pobierającej właściwości wygenerowanego (`public`, `internal`, `private`, `protected`, lub `protected internal`).|`public`|  
|Modyfikator dostępu metody ustawiającej właściwość|Modyfikator dostępu dla metody ustawiającej właściwości wygenerowanego (`public`, `internal`, `private`, `protected`, lub `protected internal`).|`public`|  
|Liczebność|Liczba elementów modelu, które można odtwarzać przeciwną roli (`0..1`, `1..1`, `0..*`, lub `1..*`). Jeśli liczebność jest `0..*` lub `1..*`, następnie wygenerowanej właściwości reprezentuje kolekcję; w przeciwnym razie wygenerowanej właściwości reprezentuje element pojedynczego modelu.|Zależy od typu relacji i czy jest to źródłowa lub docelowa rola w relacji.|  
|Nazwa|Nazwa roli domeny. Ta właściwość nie może zawierać spacji.|Nazwa klasy domeny obiektu pełniącego rolę dla tej roli.|  
|Propaguje kopiowania|`DoNotPropagateCopy`-Skopiowane obiektu pełniącego rolę nie odniesie nie kopię tego łącza.<br /><br /> `PropagateCopyToLinkOnly`Punkty skopiowane łącze do istniejącej przeciwne obiektu pełniącego rolę.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-Link skopiowanych wskazuje kopię odtwarzacza odwrotnej roli.|`PropagateCopyToLinkAndOppositeRolePlayer`dla ról źródła osadzeń.<br /><br /> `DoNotPropagateCopy`dla innych ról.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md)|  
|Propaguje Delete|`True`Aby usunąć element, do którego ta rola jest odtwarzany po usunięciu skojarzone łącze.|`True`dla celu osadzania roli.<br /><br /> `False`dla innych ról.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dostosowywanie sposób usuwania](../modeling/customizing-deletion-behavior.md).|  
|Nazwa właściwości|Nazwa właściwości wygenerowany kod obiektu pełniącego rolę. Ta nazwa nie może zawierać spacji.|Nazwa roli przeciwnej, jeśli ta rola ma zero do jeden lub jeden do jednego liczebność; w przeciwnym razie pluralized nazwa przeciwną roli.|  
|Obiekt pełniący rolę|Klasa domeny element, który można odtwarzać tej roli w relacji. Ta właściwość jest tylko do odczytu.|Klasa domeny pełniący rolę dla tej roli.|  
|Uwagi|Nieformalne uwagi skojarzonych z rolą domeny.|< Brak\>|  
|Kategoria|Kategorii, pod którym wygenerowanej właściwości pojawia się w **właściwości** okna w Projektancie wygenerowany. Jeśli ta właściwość jest pusta, a następnie wygenerowanej właściwości jest wyświetlany w obszarze **różne** kategorii|< Brak\>|  
|Opis|Opis, który jest używany do kod dokumentów i jest używany w Interfejsie użytkownika wygenerowanego projektanta.<br /><br /> Opis jest wyświetlany w etykietce narzędzia Intellisense dla wygenerowanej właściwości dla klasy obiektu pełniącego rolę.|`Description for`*Pełna nazwa roli*|  
|Nazwa wyświetlana|Nazwa, która jest wyświetlana w Projektancie wygenerowany dla roli domeny.|Skorygowaną wartość właściwości Name.|  
|Słowo kluczowe pomocy|Optional-słowo kluczowe służący do indeksu Pomocy F1 dla roli domeny.|\<Brak >|  
|Wyświetlana nazwa właściwości|Nazwa, która jest wyświetlana w Projektancie wygenerowany dla właściwości wygenerowanego roli.|Skorygowaną wartość właściwości nazwy właściwości.|  
  
> [!NOTE]
>  Wartość domyślna nazwa wyświetlana opiera się na wartości właściwości skojarzonej, ponieważ w wyniku dopełnienia spacjami przed każdego znaku wielkimi literami, który jest poprzedzony znakiem małe i który nie następuje innego wielką literą.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości relacji domeny](../modeling/properties-of-domain-relationships.md)