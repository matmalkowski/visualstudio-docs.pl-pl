---
title: Dostosowywanie i rozszerzanie języka specyficznego dla domeny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7617deb73ecaec835b0100d243b75bc26fd54a17
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Dostosowywanie i rozszerzanie języka specyficznego dla domeny
Visual Studio modelowania i wizualizacja zestawu SDK (VMSDK) zapewnia różne poziomy, w których można zdefiniować narzędzi modelowania:  
  
1.  Zdefiniuj języka specyficznego dla domeny (DSL) przy użyciu diagramu definicji DSL. Może szybko utworzyć DSL podającą notacji, czytelnej postaci XML i podstawowe narzędzia, które są wymagane do generowania kodu i pozostałych artefaktów.  
  
     Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Dostosowywanie DSL za pomocą bardziej zaawansowanych funkcji definicji DSL. Na przykład możesz wprowadzić dodatkowe linki, które są wyświetlane podczas tworzenia elementu. Te techniki najczęściej są osiągane w definicji DSL, a niektóre wymagają zaledwie kilku wierszach kodu programu.  
  
3.  Rozszerzanie narzędzia do modelowania przy użyciu kodu programu. VMSDK jest zaprojektowany specjalnie w celu ułatwiają integrowanie rozszerzeń z kodem, które są generowane na podstawie definicji DSL.  Aby uzyskać więcej informacji, zobacz [pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Po zaktualizowaniu pliku definicji DSL, nie zapomnij kliknij **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań przed skompilować ponownie rozwiązanie.  
  
##  <a name="customShapes"></a> W tej sekcji  
  
|Aby uzyskać ten efekt|Odwołuje się do tego tematu|  
|----------------------------|-------------------------|  
|Zezwalaj użytkownikowi na ustawienie właściwości kolorów i Styl kształtu.|Kliknij prawym przyciskiem myszy klasę łącznik lub kształt, wskaż pozycję **dodać widoczne**i kliknij element.<br /><br /> Zobacz [Dostosowywanie prezentacji na diagramie](../modeling/customizing-presentation-on-the-diagram.md).|  
|Różnych klas elementu modelu wyglądać na diagramie, udostępnianie właściwości, takie jak początkowa wysokość i szerokość, kolorów, etykietek narzędzi.|Użyj dziedziczenia między kształtów lub łączników klasy. Mapowania między kształtami pochodnej i pochodne klasy dziedziczą szczegóły mapowania elementów nadrzędnych.<br /><br /> Lub mapowania klas inną domenę do tej samej klasy kształtu.|  
|Klasa elementu modelu jest wyświetlana w kontekstach różnych kształtów.|Mapowanie więcej niż jedną klasę kształtu do tej samej klasy domeny. Podczas kompilowania rozwiązania wykonaj raport o błędach i zapewnienia żądanego kodu do określania, jakie kształtu do użycia.|  
|Kolor kształtu lub inne funkcje, takie jak czcionki wskazuje bieżący stan.|Zobacz [aktualizowanie łączników i kształtów w celu odzwierciedlenia modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Utworzyć regułę, która aktualizuje ujawnionych właściwości. Zobacz [reguły Propaguj zmiany w modelu](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Możesz też użyć OnAssociatedPropertyChanged() aktualizacji innych niż udostępniane funkcje, takie jak strzałki łącze lub czcionki.|  
|Ikona na zmiany kształtu do wskazywania stanu.|W oknie Szczegóły DSL, należy ustawić widoczność dekoratora mapowania. Zlokalizuj kilka dekoratory obrazu na tej samej pozycji. Zobacz [aktualizowanie łączników i kształtów w celu odzwierciedlenia modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Lub zastąpienie `ImageField.GetDisplayImage()`. Zobacz przykład w <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Ustaw obraz tła na dowolnym kształcie|Zastąpienie InitializeInstanceResources(), aby dodać zakotwiczony element ImageField. Zobacz [Dostosowywanie prezentacji na diagramie](../modeling/customizing-presentation-on-the-diagram.md).|  
|Gniazdo kształty do dowolnej głębokości|Konfigurowanie cyklicznej osadzanie drzewa. Zdefiniuj BoundsRules zawiera kształtów. Zobacz [Dostosowywanie prezentacji na diagramie](../modeling/customizing-presentation-on-the-diagram.md).|  
|Dołącz łączników w punktach stałej na krawędzi elementu.|Zdefiniuj osadzone elementy terminali, reprezentowany przez małe porty na diagramie. Użyj BoundsRules naprawa porty w miejscu. Zobacz przykład schemat w [wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Pole tekstowe wyświetla wartość pochodzi od innych wartości.|Mapowanie dekoratora tekstu do właściwości domeny obliczona lub magazynu niestandardowego. Aby uzyskać więcej informacji, zobacz [obliczona i właściwości magazynu niestandardowe](../modeling/calculated-and-custom-storage-properties.md).|  
|Propaguj zmiany między elementami modelu, lub między kształtami|Zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).|  
|Propaguj zmiany do zasobów, takich jak inne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia spoza sklepu.|Zobacz [Propaguj zmiany poza modelu do obsługi zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Okno właściwości wyświetla właściwości elementu pokrewne.|Konfigurowanie właściwości przekazywania. Zobacz [dostosowywania okna właściwości](../modeling/customizing-the-properties-window.md).|  
|Kategorie właściwości|Okno właściwości jest podzielone na sekcje zawierają informacje o nazwie kategorii. Ustaw **kategorii** z właściwości domeny. Właściwości o tej samej nazwie kategorii będą wyświetlane w tej samej sekcji. Można również ustawić **kategorii** roli relacji.|  
|Kontrola dostępu użytkownika do właściwości domeny|Ustaw **jest można przeglądać** wartość false, aby uniemożliwić właściwości domeny w oknie właściwości w czasie wykonywania. Można nadal mapować do elementów decorator tekstu.<br /><br /> **Tylko do odczytu interfejsu użytkownika** uniemożliwia użytkownikom zmienianie właściwości domeny.<br /><br /> Nie dotyczy programu dostępu do właściwości domeny.|  
|Zmień nazwę, ikonę i widoczności węzłów w Eksploratorze modelu z DSL.|Zobacz [Dostosowywanie Eksploratora modelu](../modeling/customizing-the-model-explorer.md).|  
|Włącz kopiowanie, wycinanie i wklejanie|Ustaw **Włącz kopiowania/wklejania** właściwość **edytor** węzła w Eksploratorze DSL.|  
|Kopiuj odwołanie łącza i ich cele zawsze, gdy element zostanie skopiowany. Na przykład skopiuj komentarze dołączone do elementu.|Ustaw **propaguje kopiowania** właściwości roli źródłowej (reprezentowane przez wiersz po jednej stronie relacji domeny na diagramie definicji DSL).<br /><br /> Napisz kod umożliwiający zastąpienie ProcessOnCopy, aby uzyskać bardziej złożone efekty.<br /><br /> Zobacz [Dostosowywanie zachowania kopii](../modeling/customizing-copy-behavior.md).|  
|Usuń, zmienić elementu nadrzędnego lub ponowne łączenie powiązanych elementów, gdy element zostanie usunięty.|Ustaw **propaguje usunąć** wartość rolę w relacji. Bardziej złożone efekty zastępują `ShouldVisitRelationship` i `ShouldVisitRolePlayer` metod w `MyDslDeleteClosure` klas zdefiniowanych w **DomainModel.cs**<br /><br /> Zobacz [Dostosowywanie sposób usuwania](../modeling/customizing-deletion-behavior.md)|  
|Zachowaj kształt układu i wyglądu na kopiowanie i przeciągnij upuść.|Dodaj kształty i łączniki do skopiowanych `ElementGroupPrototype`. Najodpowiedniejszym metody do przesłonięcia `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Zobacz [Dostosowywanie zachowania kopii](../modeling/customizing-copy-behavior.md).|  
|Wklejanie kształtów w wybranej lokalizacji, np. w bieżącej pozycji kursora.|Zastąpienie `ClipboardCommandSet.ProcessOnCopy()` Aby użyć lokalizacji określonej wersji `ElementOperations.Merge().` zobacz [Dostosowywanie zachowania kopii](../modeling/customizing-copy-behavior.md).|  
|Tworzyć linki do dodatkowych przy wklejeniu|Override ClipboardCommandSet.ProcessOnPasteCommand()|  
|Przeciągania i upuszczania z diagramu, inne DSLs i Windows elementów|Zobacz [porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Zezwalaj na kształtu lub narzędzia przeciąganych na kształt podrzędny, taki jak port, tak jakby były przeciągnięto nadrzędnego.|Define — dyrektywa scalania Element na klasę obiektu docelowego do przekazywania upuszczony obiekt nadrzędny. Zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).|  
|Zezwalaj na kształt lub narzędzia może być przeciągnięto kształtu, a linki do dodatkowych lub obiekty utworzone. Na przykład, aby umożliwić komentarz, aby być upuszczone na element, do którego ma być połączony.|#Define — dyrektywa scalania Element dla klasy docelowej domeny i zdefiniowanie łączy do wygenerowania. W przypadku złożonych można dodać kod niestandardowy. Zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).|  
|Utwórz grupę elementów z jednego narzędzia. Na przykład składnik ustalonego zestawu portów.|Metoda inicjowania przybornika w ToolboxHelper.cs musi zostać zastąpiona. Utwórz Element grupy prototypu (EGP) zawierający elementy i ich relacji łącza. Zobacz [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Dołączyć kształtów głównej i port EGP albo zdefiniuj BoundsRules położenie kształtów portu EGP jest uruchomione. Zobacz [BoundsRules ograniczyć kształtu lokalizacja i rozmiar](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Narzędzie jednego połączenia można utworzyć kilka rodzajów relacji.|Dodaj łącze połączyć dyrektywy LCD do konstruktora połączenia, który jest wywoływany przez narzędzie. LCDs określenia typu relacji z typów dwa elementy. Aby to zależą od stanów elementów, można dodać kod niestandardowy. Zobacz [Dostosowywanie narzędzi i przybornika](../modeling/customizing-tools-and-the-toolbox.md).|  
|Trwałe narzędzia — użytkownik może kliknąć dwukrotnie dowolnego narzędzia, aby utworzyć wiele kształtów lub łączników pod rząd.|W Eksploratorze DSL wybierz `Editor` węzła. W oknie właściwości ustaw **używa trwałe elementy przybornika**.|  
|Definiowanie polecenia menu|Zobacz [porady: modyfikowanie polecenia standardowe Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Ogranicz modelu przy użyciu reguł sprawdzania poprawności|Zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md)|  
|Generuj kod, pliki konfiguracji lub dokumenty z DSL.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Dostosuj sposób modeli są zapisywane do pliku.|Zobacz [dostosowywania magazynu plików i serializacja XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Zapisz modeli baz danych lub innego nośnika.|Zastąpienie *YourLanguage*danych dokumentu<br /><br /> Zobacz [dostosowywania magazynu plików i serializacja XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integrować kilka DSLs, aby mogły działać w ramach jednej aplikacji.|Zobacz [integrowanie modeli przy użyciu programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Zezwalaj na Twoje DSL rozszerzyć przez osoby trzecie i kontrola rozszerzenia.|[Rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Udostępnianie klas między językami DSL za pomocą biblioteki DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definiowanie zasad blokowania na potrzeby tworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>Zobacz także

[Sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   
[Pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
[Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]