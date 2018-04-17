---
title: Kontrolowanie widoczności ikony lub Dekoratora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7682bbb448caa6dbd1938dfc6dcdb6d89c083680
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub elementu Decorator
A *dekoratora* jest ikona albo wiersza tekstu wyświetlanego na kształt języka specyficznego dla domeny (DSL). Możesz ustawić dekoratora występują a znikają w zależności od stanu właściwości w modelu. Na przykład na kształt reprezentujący osoby, może mieć inne ikony, które znajdują się w zależności od danej osoby, płci, liczbę elementów podrzędnych i tak dalej.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub dekoratora  
 W poniższej procedurze przyjęto, że został już zdefiniowany kształt i jego mapowania do klasy domeny. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Aby ustawić widoczność dekoratora ikony lub tekstu  
  
1.  Na diagramie definicji DSL Dodaj do klasy kształtu ikony lub elementów decorator tekstu, które mają być wyświetlane.  
  
    1.  Kliknij prawym przyciskiem myszy klasę kształtu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk wymagany typ dekoratora.  
  
    2.  Ustaw dekoratora **pozycji** właściwości. Więcej niż jeden dekorator może mieć to samo położenie. Na przykład można mieć ikony męskiego oraz gniazdo udostępnianie tej samej pozycji.  
  
    3.  Ustaw **domyślna ikona** właściwości dekoratora ikony.  
  
2.  Wybierz diagram element mapy, szara linia między kształtu Klasa i klasy domeny na diagramie definicji DSL.  
  
3.  W okienku szczegółów DSL w **mapy Dekoratora** , a następnie wybierz dekoratora. Na przykład MaleDecorator.  
  
4.  Sprawdź **filtru widoczność** pole.  
  
5.  Jeśli właściwość domeny, którą należy ustawić widoczność znajduje się w klasie natychmiastowego domeny, należy pozostawić **ścieżka do właściwości filtru** puste.  
  
     W przeciwnym razie kliknij menu rozwijane i przejście do relacji lub klasy, w którym znajduje się właściwość.  
  
    -   Aby uniknąć raportu o błędach, należy nie przeglądania relacji oznaczonej jako "*" w narzędziu nawigacji.  
  
6.  Ustaw **właściwości filtru** do właściwości domeny. Na przykład płeć.  
  
7.  W **wpisy widoczność** liście, Dodaj wartości tej właściwości domeny, dla którego dekorator powinny być widoczne. Na przykład męskiego.  
  
8.  Powtórz kroki dla każdego ikony.  
  
9. **Przekształć wszystkie szablony**, tworzenia i uruchamiania i Otwórz diagram testu.  
  
10. Po zmianie wartości właściwości kontrolowanie elementów decorator powinien pojawiają się i znikają.  
  
 Często mają widoczność kontrolowany przez formułę bardziej złożone niż prosty zestaw wartości. Na przykład na ma ikony są zależne od liczby łączy określonego typu, lub aby wprowadzić go zależy, czy liczba jest w określonym zakresie. W takim przypadku należy użyć następującej procedury.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Aby ustawić widoczność dekoratora, na podstawie wzoru  
  
1.  Dodaj właściwość domeny obliczeniowych do klasy domeny. W **właściwości** okna, ustaw następujące wartości:  
  
     **IsBrowsable =**`False`**— spowoduje to ukrycie właściwości użytkownika**   
  
     **Rodzaj =**`Calculated`**-oznacza to, że zapewni kod, który oblicza swoją wartość**   
  
     **Nazwa** na przykład **DecoratorControl**  
  
     **Typ** = `Boolean`  
  
     Aby uzyskać więcej informacji, zobacz [obliczona i właściwości magazynu niestandardowe](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Należy ustawić widoczność dekoratora właściwości w nowym.  
  
    1.  Wybierz diagram element mapy, szara linia z klasy domeny dla kształtu. W **szczegóły DSL** okna, otwórz **DecoratorMap** kartę.  
  
    2.  Sprawdź **filtru widoczność** pole.  
  
    3.  W **właściwości filtru**, wybierz właściwość formantu **DecoratorControl**.  
  
    4.  W obszarze **wpisy widoczność**, wprowadź `True`.  
  
3.  Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.  
  
4.  Kliknij przycisk **Kompiluj rozwiązanie** na **kompilacji** menu.  
  
5.  Kliknij dwukrotnie pozycję raportu o błędach, które pojawiły: "*YourClass* nie zawiera definicji dla GetDecoratorControlValue...".  
  
     Otwiera edytora tekstu na Dsl\GeneratedCode\DomainClasses.cs. Powyżej wyróżnione błędu jest komentarz, który wyświetlenie monitu o dodanie metody.  
  
6.  Należy pamiętać, przestrzeń nazw, klasy i metody, które nie są spełnione.  For example, Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  W osobnym pliku kodu należy zapisać definicji częściowej klasy, która zawiera brakującej metody. Na przykład:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Aby uzyskać więcej informacji na temat dostosowywania model kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Ponownie skompilować i uruchomić rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie łączników i kształtów](../modeling/defining-shapes-and-connectors.md)   
 [Ustawienie obraz tła na diagramie](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)