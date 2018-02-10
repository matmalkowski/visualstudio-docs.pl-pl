---
title: "Dostosowywanie Element tworzenia i przepływu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ac29f7b745c9698f6051bce6a7b54a1476bf8a7c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-element-creation-and-movement"></a>Dostosowywanie tworzenia i przesuwania elementów
Można zezwolić na element, aby być przeciągnięto innego, z przybornika lub wklejenie lub operacji przenoszenia. Może mieć przeniesione elementy połączone z elementów docelowych przy użyciu relacji, które określisz.  
  
 Element scalania — dyrektywa (EMD) określa, co się dzieje, gdy jest jeden element modelu *scalone* w innym elementem modelu. Kojarzenie jest wykonywane, gdy:  
  
-   Użytkownik przeciąga z przybornika do diagramu lub kształtu.  
  
-   Użytkownik tworzy element przy użyciu menu Dodaj w Eksploratorze lub przedział kształtu.  
  
-   Użytkownik elementu są przenoszone z jednego tor na inny.  
  
-   Użytkownik wkleja elementu.  
  
-   Kod program wywołuje element dyrektywa scalania.  
  
 Chociaż operacje tworzenia mogą wydawać się różnić od operacje kopiowania, faktycznie działają w taki sam sposób. Gdy element zostanie dodany, na przykład z przybornika, prototyp go są replikowane. Prototyp jest scalany modelu w taki sam sposób jak elementy, które zostały skopiowane z innej części modelu.  
  
 Odpowiedzialność EMD jest określenie, jak obiekt lub grupę obiektów powinny zostać scalone do określonej lokalizacji w modelu. W szczególności decyduje, jakie relacje należy można utworzyć wystąpienia połączyć scalonych grupy do modelu. Można również dostosować go do ustawiania właściwości i utworzyć dodatkowe obiekty.  
  
 ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd_merge.png "DSL-EMD_Merge")  
Rola dyrektywy scalania Element  
  
 EMD jest generowany automatycznie podczas definiowania relacja osadzania. To ustawienie domyślne EMD tworzy wystąpienie relacji po dodaniu nowych wystąpień podrzędnych do elementu nadrzędnego. Na przykład te EMDs domyślne można zmodyfikować przez dodanie niestandardowego kodu.  
  
 Można również dodać własne EMDs w definicji DSL, aby umożliwić użytkownikom przeciągnij lub Wklej różnych kombinacji klas scalone i odbierania.  
  
## <a name="defining-an-element-merge-directive"></a>Definiowanie scalania Element — dyrektywa  
 Dyrektywy scalania element można dodać do klasy, relacje domeny kształtów, łączniki i diagramy. Można dodawać lub je znaleźć w Eksploratorze DSL w klasie odbierania domeny. Odbieranie klasa jest klasą domeny elementu, który jest już w modelu i na której element nowe lub skopiowane zostaną scalone.  
  
 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd_details.png "DSL-EMD_Details")  
  
 **Indeksowania klasy** jest klasą domeny elementów, które można by scalić do elementów członkowskich klasy odbiorczej. Wystąpienia podklasami klasy indeksowania również zostaną scalone przez ten EMD, chyba że zostanie ustawiony **dotyczy podklasy** na wartość False.  
  
 Istnieją dwa rodzaje dyrektywy scalania:  
  
-   A **procesu scalania** dyrektywa określa relacji, według których powinna być łączona nowego elementu w drzewie.  
  
-   A **do przodu scalania** dyrektywy przekierowuje nowego elementu do innego elementu odbierania, zwykle elementu nadrzędnego.  
  
 Można dodać kod niestandardowy do scalenia dyrektywy:  
  
-   Ustaw **zaakceptować używa niestandardowych** można dodać własny kod, aby określić, czy powinny zostać scalone konkretnego wystąpienia elementu indeksowania w elemencie docelowym. Gdy użytkownik przeciąga z przybornika, "nieprawidłowe" Wskaźnik przedstawia, jeśli kod uniemożliwia scalanie.  
  
     Na przykład można zezwolić scalanie tylko wtedy, gdy element odbierania w określonym stanie.  
  
-   Ustaw **używa niestandardowych scalania** można dodać Podaj własny kod, aby zdefiniować zmiany wprowadzone w modelu podczas scalania.  
  
     Na przykład można ustawić właściwości w elemencie scalony przy użyciu danych z nowej lokalizacji w modelu.  
  
> [!NOTE]
>  Podczas pisania kodu niestandardowego scalania, dotyczy tylko scalenia, które są wykonywane przy użyciu tego EMD. Jeśli istnieją inne EMDs, które łączą się tego samego typu obiektu lub w przypadku innych kodu niestandardowego, który tworzy tych obiektów bez użycia EMD, następnie one nie dotyczy kodu niestandardowego scalania.  
>   
>  Jeśli chcesz upewnić się, że nowy element lub nowej relacji zawsze jest przetwarzany przez niestandardowy kod, rozważ zdefiniowanie `AddRule` na Relacja osadzania i `DeleteRule` klasy domeny elementu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Przykład: Definiowanie EMD bez kod niestandardowy  
 Poniższy przykład umożliwia użytkownikom tworzenie elementu i łącznika w tym samym czasie, przeciągając je z przybornika do istniejącego kształtu. W przykładzie dodano EMD do definicji DSL. Przed modyfikacji użytkownicy będą mogli przeciągać narzędzia na diagramie, ale nie do kształtów.  
  
 Użytkownicy mogą również wkleić elementy do innych elementów.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Aby zezwolić użytkownikom na tworzenie elementu i łącznika w tym samym czasie  
  
1.  Tworzenie nowego DSL przy użyciu **minimalnego języka** szablon rozwiązania.  
  
     Po uruchomieniu tego DSL umożliwia utworzenie łączników między kształtami i kształtów. Nie można przeciągnąć nowy **ExampleElement** kształt z przybornika do istniejącego kształtu.  
  
2.  Aby umożliwić użytkownikom scal elementy na `ExampleElement` kształtów, Utwórz nowy EMD w `ExampleElement` klasy domeny:  
  
    1.  W **DSL Explorer**, rozwiń węzeł **klasy domeny**. Kliknij prawym przyciskiem myszy `ExampleElement` , a następnie kliknij przycisk **Dodaj nowy Element scalania dyrektywy**.  
  
    2.  Upewnij się, że **szczegóły DSL** okno jest otwarte, dzięki czemu można wyświetlić szczegóły nowego EMD. (Menu: **widoku**, **innych okien**, **szczegóły DSL**.)  
  
3.  Ustaw **indeksowania klasy** okno Szczegóły DSL do zdefiniowania, jakie klasy elementów można scalić na `ExampleElement` obiektów.  
  
     Na przykład wybierz `ExampleElements`, dzięki czemu użytkownik można przeciągnięcie nowe elementy do istniejących elementów.  
  
     Zwróć uwagę, że klasa indeksowanie staje się nazwa EMD w Eksploratorze DSL.  
  
4.  W obszarze **procesu scalania, tworząc łącza**, Dodaj dwie ścieżki:  
  
    1.  Jedną ścieżkę łączy nowego elementu nadrzędnego modelu. Wyrażenie ścieżki, które należy wprowadzić nawiguje od istniejącego elementu się relacja osadzania modelu nadrzędnego. Na koniec określa rolę w nowe łącze, do której zostanie przypisany nowy element. Ścieżka wygląda następująco:  
  
         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
    2.  Innej ścieżki łączy nowego elementu do istniejącego elementu. Wyrażenie ścieżki Określa relacja odwołania i roli, do której zostanie przypisany nowy element. Ta ścieżka jest następująca:  
  
         `ExampleElementReferencesTargets.Sources`  
  
     Narzędzie ścieżek nawigacji służy do tworzenia poszczególnych ścieżek:  
  
    1.  W obszarze **procesu scalania przez tworzenie łączy w ścieżkach**, kliknij przycisk  **\<Dodaj ścieżkę >**.  
  
    2.  Kliknij strzałkę listy rozwijanej z prawej strony elementu listy. Zostanie wyświetlony widok drzewa.  
  
    3.  Rozwiń węzły drzewa do ścieżki, która ma zostać określony.  
  
5.  Przetestuj DSL:  
  
    1.  Naciśnij klawisz F5, aby ponownie skompilować i uruchomić rozwiązanie.  
  
         Ponowne kompilowanie będzie trwać dłużej niż zwykle, ponieważ wygenerowany kod zostanie zaktualizowany z szablonów tekstowych, które są zgodne z nową definicję DSL.  
  
    2.  Gdy eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] została uruchomiona, otwórz plik modelu DSL użytkownika. Utwórz niektóre przykładowe elementy.  
  
    3.  Przeciągnij z **przykład elementu** narzędzia do istniejącego kształtu.  
  
         Pojawi się nowy kształt i jest połączony istniejący kształt z łącznika.  
  
    4.  Skopiuj istniejącego kształtu. Wybierz inny kształt i Wklej.  
  
         Zostanie utworzona kopia pierwszego kształtu.  Jego nazwa została zmieniona i jest włączony na drugi kształt z łącznika.  
  
 Zwróć uwagę następujące kwestie z tej procedury:  
  
-   Tworząc dyrektywy scalić elementu, można zezwolić na dowolnej klasy elementu, aby akceptować inne. EMD jest tworzony w klasie odbierania domeny, a klasa zaakceptowane domeny określono w **indeksu klasy** pola.  
  
-   Definiując ścieżki, można określić łącza, które powinny być używane do połączenia z nowego elementu istniejącego modelu.  
  
     Linki, które określisz powinna zawierać jedna relacja osadzania.  
  
-   EMD dotyczy zarówno tworzenie z przybornika, a także operacji wklejania.  
  
     Podczas pisania kodu niestandardowego, który tworzy nowe elementy, można jawnie wywołać EMD przy użyciu `ElementOperations.Merge` metody. Dzięki temu kod łączy nowych elementów do modelu w taki sam sposób jak inne operacje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopii](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Przykład: Dodawanie niestandardowych zaakceptować kodu do EMD  
 Dodając kod niestandardowy do EMD, można zdefiniować bardziej złożonych zachowanie scalania. Ten prosty przykład uniemożliwia dodanie więcej niż określoną liczbę elementów do diagramu. Przykład modyfikuje domyślne EMD, który towarzyszy relacja osadzania.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Aby napisać kod niestandardowy zaakceptować ograniczenia co użytkownik może dodawać  
  
1.  Tworzenie DSL przy użyciu **minimalnego języka** szablon rozwiązania. Otwórz diagram definicji DSL.  
  
2.  W Eksploratorze DSL rozwiń **klasy domeny**, `ExampleModel`, **dyrektywy scalania Element**. Wybierz dyrektywę scalania element o nazwie `ExampleElement`.  
  
     Formanty EMD to jak użytkownik może utworzyć nowego `ExampleElement` obiektów w modelu, na przykład przeciągając je z przybornika.  
  
3.  W **szczegóły DSL** wybierz **zaakceptować używa niestandardowych**.  
  
4.  Ponownie skompiluj rozwiązanie. Spowoduje to trwać dłużej niż zwykle, ponieważ wygenerowany kod będą aktualizowane na podstawie modelu.  
  
     Błąd kompilacji zostanie zgłoszony, podobnie jak: "Company.ElementMergeSample.ExampleElement nie zawiera definicji dla CanMergeExampleElement..."  
  
     Musisz zaimplementować metodę `CanMergeExampleElement`.  
  
5.  Utwórz nowy plik kodu w **Dsl** projektu. Zastąp zawartość następującym kodem i zmień przestrzeni nazw projektu.  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     Ten prosty przykład ogranicza liczbę elementów, które można scalić w modelu nadrzędnego. Warunki bardziej interesujące metody sprawdzić właściwości i linki odbierania obiektu. On również monitorować właściwości scalania elementów, które będą przenoszone w <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Aby uzyskać więcej informacji na temat `ElementGroupPrototypes`, zobacz [Dostosowywanie zachowania kopii](../modeling/customizing-copy-behavior.md). Aby uzyskać więcej informacji dotyczących sposobu pisania kodu, który odczytuje modelu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  Przetestuj DSL:  
  
    1.  Naciśnij klawisz F5, aby ponownie skompiluj rozwiązanie. Gdy eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zostanie otwarty, otwórz wystąpienie programu DSL.  
  
    2.  Utwórz nowe elementy na kilka sposobów:  
  
        1.  Przeciągnij z **przykład elementu** narzędzia na diagramie.  
  
        2.  W **Eksplorator modelu przykład**, kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij przycisk **Dodaj nowy Element przykład**.  
  
        3.  Skopiuj i Wklej elementu na diagramie.  
  
    3.  Sprawdź, czy nie można użyć dowolnej z następujących sposobów, aby dodać więcej niż cztery elementy do modelu. Jest to spowodowane wszyscy korzystają dyrektywę scalania Element.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Przykład: Dodawanie niestandardowych scalania kodu do EMD  
 Kod niestandardowy scalania można zdefiniować, co się dzieje, gdy użytkownik przeciąga narzędzia lub wkleja na element. Istnieją dwa sposoby definiowania niestandardowych scalania:  
  
1.  Ustaw **używa niestandardowych scalania** i podaj kod wymagany. Kod zastępuje scalania wygenerowanego kodu. Użyj tej opcji, jeśli chcesz całkowicie ponownie zdefiniować czego scalania.  
  
2.  Zastąpienie `MergeRelate` metody i opcjonalnie `MergeDisconnect` metody. Aby to zrobić, należy ustawić **generuje podwójne pochodnych** właściwości klasy domeny. Kod może wywoływać scalania wygenerowany kod w klasie podstawowej. Użyj tej opcji, jeśli chcesz wykonać dodatkowe czynności, po wykonaniu operacji scalania.  
  
 Scalenia, które są wykonywane przy użyciu tego EMD wpływ tylko na tych metod. Jeśli chcesz mieć wpływ na wszystkie sposoby, w których można utworzyć elementu scalonych alternatywą jest określenie `AddRule` na Relacja osadzania i `DeleteRule` w klasie scalonych domeny. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Aby zastąpić MergeRelate  
  
1.  W definicji DSL upewnij się, zdefiniowano EMD, do której chcesz dodać kod. Jeśli chcesz, możesz dodać ścieżki i definiować niestandardowe zaakceptować kodu, zgodnie z opisem w poprzedniej sekcji.  
  
2.  Na diagramie DslDefinition wybrać klasę odbierania scalania. Zazwyczaj jest klasa w końcu źródłowym relacja osadzania.  
  
     Na przykład w DSL, generowane z rozwiązania minimalnego języka, wybierz pozycję `ExampleModel`.  
  
3.  W **właściwości** ustaw **generuje podwójne pochodnych** do **true**.  
  
4.  Ponownie skompiluj rozwiązanie.  
  
5.  Sprawdź zawartość **Dsl\Generated Files\DomainClasses.cs**. Wyszukaj metody o nazwie `MergeRelate` i sprawdź, czy ich zawartość. Ten sposób można napisać własny wersji.  
  
6.  W nowym pliku kodu zapisu klasę częściową dla klasy odbierania i zastąpić `MergeRelate` metody. Pamiętaj, aby wywołać metodę podstawową. Na przykład:  
  
    ```csharp  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>Pisanie kodu niestandardowego scalania  
  
1.  W **Dsl\Generated Code\DomainClasses.cs**, sprawdź metody o nazwie `MergeRelate`. Te metody tworzyć łącza między nowego elementu i istniejącego modelu.  
  
     Ponadto inspekcja metody o nazwie `MergeDisconnect`. Te metody odłączyć element na podstawie modelu, gdy ma zostać usunięty.  
  
2.  W **DSL Explorer**wybierz lub Utwórz dyrektywy scalania elementów, które chcesz dostosować. W **szczegóły DSL** ustaw **używa niestandardowych scalania**.  
  
     Po ustawieniu tej opcji **procesu scalania** i **do przodu scalania** opcje są ignorowane. Zamiast niego jest używana kodu.  
  
3.  Ponownie skompiluj rozwiązanie. Będzie trwało dłużej niż zwykle, ponieważ pliki wygenerowanego kodu będą aktualizowane na podstawie modelu.  
  
     Pojawią się komunikaty o błędach. Kliknij dwukrotnie komunikatu o błędzie, zapoznaj się z instrukcjami w wygenerowanym kodzie. Te instrukcje monit o podanie dwie metody `MergeRelate` *YourDomainClass* i `MergeDisconnect` *YourDomainClass*  
  
4.  Zapisywanie metod w definicji klasy częściowej w osobnym pliku kodu. Przykłady, które należy sprawdzić wcześniej powinien sugerują, co jest potrzebne.  
  
 Kod niestandardowy scalania nie wpływa na kod, który tworzy obiekty i relacje bezpośrednio i nie ma wpływ na inne EMDs. Aby upewnić się, że dodatkowe zmiany są wykonywane niezależnie od tego, w jaki sposób jest tworzony element, należy wziąć pod uwagę zapisu `AddRule` i `DeleteRule` zamiast tego. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Przekierowywanie operacji scalania  
 Dyrektywa do przodu scalania przekierowuje obiekt docelowy operacji scalania. Zazwyczaj nowy obiekt docelowy jest nadrzędny osadzania początkowego obiektu docelowego.  
  
 Na przykład w DSL, który został utworzony przy użyciu szablonu diagram składnika, porty są osadzone w składnikach. Porty są wyświetlane jako małe kształty na krawędzi kształtu składnik. Użytkownik tworzy portów, przeciągając narzędzie portu na kształt składnik. Czasami użytkownik przeciąga przez pomyłkę narzędzia portu do istniejącego portu, zamiast składnik, a kończy się niepowodzeniem. Jest to prosty błąd, gdy istnieje kilka istniejących portów. Aby pomóc użytkownikowi w celu uniknięcia tego niedogodności, można zezwolić na porty, które mają być przeciągnięto istniejącego portu, ale ma akcji przekierowanie do elementu nadrzędnego. Operacja działa tak, jakby składnik był elementem docelowym.  
  
 Dyrektywa scalania do przodu można tworzyć w rozwiązaniu składnik modelu. Jeśli możesz skompilować i uruchomić oryginalnym rozwiązaniu, powinny pojawić się przeciągnąć dowolną liczbę użytkowników **Port wejściowy** lub **Port wyjściowy** elementy z **przybornika** do **Składnika** elementu. Nie można jednak przeciągania port do istniejącego portu. Niedostępne wskaźnika alerty ich to przeniesienie jest wyłączona. Jednak utworzyć dyrektywy do przodu scalania, aby port to przypadkowo usunięte na istniejącym **Port wejściowy** był kierowany do **składnika** elementu.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Aby utworzyć dyrektywy do przodu scalania  
  
1.  Utwórz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązania przy użyciu szablonu składnik modelu.  
  
2.  Wyświetl **DSL Explorer** otwierając DslDefinition.dsl.  
  
3.  W **DSL Explorer**, rozwiń węzeł **klasy domeny**.  
  
4.  **ComponentPort** klasy abstrakcyjnej domeny jest klasą bazową obu **InPort** i **OutPort**. Kliknij prawym przyciskiem myszy **ComponentPort** , a następnie kliknij przycisk **Dodaj nowy Element scalania dyrektywy**.  
  
     Nowy **dyrektywę scalania Element** węzeł jest wyświetlany w obszarze **dyrektywy scalania Element** węzła.  
  
5.  Wybierz **dyrektywę scalania Element** węzła i Otwórz **szczegóły DSL** okna.  
  
6.  Na liście klasy indeksowanie wybierz **ComponentPort**.  
  
7.  Wybierz **przekazywania scalania do innej domeny klasy**.  
  
8.  Na liście wyboru ścieżki rozwiń **ComponentPort**, rozwiń węzeł **ComponentHasPorts**, a następnie wybierz **składnika**.  
  
     Nowa ścieżka powinien wyglądać tego:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Zapisz rozwiązanie i Przekształć szablonów, klikając przycisk po prawej stronie **Eksploratora rozwiązań** paska narzędzi.  
  
10. Tworzenie i uruchamianie rozwiązania. Nowe wystąpienie klasy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pojawi się.  
  
11. W **Eksploratora rozwiązań**, otwórz Sample.mydsl. Diagram i **przybornika ComponentLanguage** są wyświetlane.  
  
12. Przeciągnij **Port wejściowy** z **przybornika** do innego **Port wejściowy.** Następnie przeciągnij **OutputPort** do **InputPort** , a następnie do innego **OutputPort**.  
  
     Użytkownik nie powinien być widoczny wskaźnik niedostępny i powinno być możliwe usunięcie nowe **Port wejściowy** istniejącą. Wybierz nową **Port wejściowy** i przeciągnij go do innego punktu **składnika**.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Dostosowywanie przybornika i narzędzia](../modeling/customizing-tools-and-the-toolbox.md)   
 [Przykładowe diagramy obwodu DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)