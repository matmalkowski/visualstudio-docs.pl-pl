---
title: "Właściwości domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 58402e1030516e6f587ec428bd98179ff82ec43a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-properties"></a>Właściwości właściwości domeny
A *właściwości domeny* jest funkcją element modelu, który może zawierać wartości. Na przykład `Person` klasa domeny może mieć właściwości `Name` i `BirthDate`. W definicji DSL właściwości domeny są wyświetlane w polu Domena klasy na diagramie, a w obszarze klasy domeny w Eksploratorze DSL. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Wyraz "property" ma dwa zastosowania. A *właściwości domeny* jest funkcją, która definiuje się na klasie domeny. Z kolei ma wiele elementów DSL *właściwości*, które są wymienione w **właściwości** okna w definicji DSL. Na przykład dla każdej właściwości domeny ma zbiór właściwości, które są opisane w tym temacie.  
  
 W czasie wykonywania, gdy użytkownik tworzy wystąpienia klasy domeny, wartości właściwości domeny są widoczne w oknie właściwości i mogą być wyświetlane kształtów.  
  
 Większość właściwości domeny są zaimplementowane jako zwykłej CLR właściwości. Z programowania punktu widzenia właściwości domeny są bardziej rozbudowane funkcje niż właściwości zwykłego programu:  
  
-   Można zdefiniować reguły i monitorować stan właściwości zdarzenia. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
-   Transakcje pomagać w zapobieganiu niespójny stan. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Po wybraniu właściwości domeny na diagramie lub w Eksploratorze DSL, można zostać wyświetlone następujące informacje w oknie właściwości. Aby uzyskać więcej informacji na temat używania tych elementów, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Właściwość|Opis|Wartość domyślna|  
|--------------|-----------------|-------------------|  
|**Opis**|Opis, który służy do dokumentów w interfejsie użytkownika (UI) wygenerowanego projektanta.|\<Brak >|  
|**Nazwa wyświetlana**|Nazwa, która będzie wyświetlana w Projektancie wygenerowany dla tej właściwości domeny. Może zawierać spacji i znaków interpunkcyjnych, na przykład "utworu".|\<Brak >|  
|**Element nazwy dostawcy**|Ma to zastosowanie tylko wtedy, gdy ustawiono `Is Element Name` do `true`. Można napisać kod, który zawiera nazwę nowego elementu klasą domeny Zastępowanie domyślnego zachowania.<br /><br /> W pliku kodu w projekcie DSL, Utwórz klasę, która jest pochodną <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Następnie w Eksploratorze DSL, kliknij prawym przyciskiem myszy pierwiastek DSL i kliknij przycisk Dodaj typu zewnętrznego. Wprowadź nazwę klasy.<br /><br /> Ponownie wybierz pozycję Właściwości tej domeny i wybierz z listy rozwijanej nazwę klasy.|\<Brak >|  
|**Modyfikator dostępu metody pobierającej**|Poziom dostępu klasy domeny (`public` lub `internal`). To określa zakres, w jaki program kodu można dostępu do właściwości.|`public`|  
|**Słowo kluczowe pomocy**|Optional-słowo kluczowe służący do indeksu Pomocy F1 dla tej właściwości domeny.|\<Brak >|  
|**Umożliwia przeglądania**|Jeśli `True`, wartość właściwości jest wyświetlane użytkownikowi w oknie właściwości, gdy modele tego DSL są otwarte.<br /><br /> Jeśli `False`, wartość właściwości jest ukryty w interfejsie użytkownika.<br /><br /> Jeśli chcesz właściwość domeny widoczny, ale tylko do odczytu, ustaw **jest interfejs użytkownika tylko do odczytu**.|`True`|  
|**Nazwa elementu jest**|Jeśli `True`, ta właściwość domeny będzie wyświetlana jako nazwa elementu modelu w Eksploratorze DSL.<br /><br /> Nowe elementy modelu otrzyma wartość domyślną unikatowy dla tej właściwości. Jeśli chcesz kontrolować, jak te wartości są generowane, ustaw **dostawcy nazwy elementu**.|`False`|  
|**Interfejs użytkownika tylko do odczytu**|Jeśli `True`, nie można zmienić wartości właściwości domeny przy użyciu interfejsu użytkownika. Nadal można ustawić przez programy i będą widoczne w oknie właściwości.<br /><br /> Jeśli chcesz ukryć właściwości domeny użytkownika, należy ustawić **jest można przeglądać**. Jeśli chcesz kontrolować dostęp przez programy, ustaw **modyfikator dostępu metody ustawiającej**.|`False`|  
|**Rodzaj**|Rodzaj właściwości domeny (`Normal`, `Calculated`, lub `CustomStorage`). Aby uzyskać więcej informacji, zobacz [obliczona i właściwości magazynu niestandardowe](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Nazwa**|Nazwa tej właściwości domeny. Go musi być prawidłowym identyfikatorem, na przykład **SongTitle**.|\<Brak >|  
|**Uwagi**|Nieformalne uwagi, które są skojarzone z tą właściwością domeny.|\<Brak >|  
|**Modyfikator dostępu metody ustawiającej**|Modyfikator dostępu dla metody ustawiającej. To określa zakres, w jaki program kodu można ustawić właściwości.|`public`|  
|**Typ**|Typ właściwości. Aby dodać do listy dostępnych typów, kliknij prawym przyciskiem myszy pierwiastek DSL w Eksploratorze DSL, a następnie kliknij przycisk **Dodaj typu zewnętrznego**.|`String`|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)