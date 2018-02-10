---
title: "Właściwości magazynu obliczeniowej i niestandardowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1b5d89a621c0f325fd20dbff47c30975f760a6f8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="calculated-and-custom-storage-properties"></a>Obliczone i niestandardowe właściwości przechowywania
Wszystkie właściwości domeny języka specyficznego dla domeny (DSL) mogą być wyświetlane dla użytkownika na diagramie i w Eksploratorze z języka i można uzyskać, sprawdzając kod programu. Jednak właściwości różnią się w taki sposób, że ich wartości są przechowywane.  
  
## <a name="kinds-of-domain-properties"></a>Rodzaje właściwości domeny  
 W definicji DSL, można ustawić **rodzaj** właściwości domeny, zgodnie z poniższą tabelą:  
  
|Rodzaj właściwości domeny|Opis|  
|--------------------------|-----------------|  
|**Standardowe** (domyślna)|Właściwość domeny, która jest zapisywany w *przechowywania* i Zserializowany do pliku.|  
|**Obliczone**|Właściwość domeny tylko do odczytu, który nie jest zapisany w magazynie, ale jest obliczana na podstawie innych wartości.<br /><br /> Na przykład `Person.Age` może być obliczana na podstawie `Person.BirthDate`.<br /><br /> Należy podać kod, który wykonuje obliczenia. Zazwyczaj należy obliczyć wartość od innych właściwości domeny. Jednak można również użyć zasobów zewnętrznych.|  
|**Niestandardowe magazynu**|Właściwość domeny, które nie są zapisywane bezpośrednio w magazynie, ale może być zarówno get i set.<br /><br /> Należy podać metody get i set wartość.<br /><br /> Na przykład `Person.FullAddress` może być przechowywany w `Person.StreetAddress`, `Person.City`, i `Person.PostalCode`.<br /><br /> Można również uzyskać dostępu do zasobów zewnętrznych, na przykład aby pobieranie i ustawianie wartości z bazy danych.<br /><br /> Kod nie może ustawić wartości w magazynie podczas `Store.InUndoRedoOrRollback` ma wartość true. Zobacz [transakcje i niestandardowej metody ustawiające](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Podanie kodu dla właściwości magazynu obliczona lub niestandardowych  
 Jeśli ustawisz rodzaj właściwości domeny obliczona lub magazyn niestandardowy, należy podać metody dostępu. Podczas kompilowania rozwiązania raportu o błędzie informuje o to, co jest wymagane.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Aby zdefiniować obliczona lub niestandardowe właściwości magazynu  
  
1.  W DslDefinition.dsl, wybierz właściwość domeny w schemacie lub w **DSL Explorer**.  
  
2.  W **właściwości** ustaw **rodzaj** do **obliczona** lub **magazynu niestandardowego**.  
  
     Upewnij się, że masz ustawioną również jego **typu** odpowiednią.  
  
3.  Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi **Eksploratora rozwiązań**.  
  
4.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Pojawi się następujący komunikat o błędzie: "*YourClass* nie zawiera definicji Get*YourProperty*."  
  
5.  Kliknij dwukrotnie komunikat o błędzie.  
  
     Otwiera Dsl\GeneratedCode\DomainClasses.CS lub DomainRelationships.cs. Powyżej wywołania metody wyróżnione komentarz monituje o podanie implementację GET*YourProperty*().  
  
    > [!NOTE]
    >  Ten plik został wygenerowany z DslDefinition.dsl. Jeśli możesz edytować ten plik, zmiany zostaną utracone przy następnym kliknięciu **Przekształć wszystkie szablony**. Zamiast tego dodać wymaganej metody w oddzielnym pliku.  
  
6.  Utwórz lub Otwórz plik klasy w oddzielnym folderze, na przykład CustomCode\\*YourDomainClass*. cs.  
  
     Upewnij się, że przestrzeń nazw jest taki sam jak wygenerowanego kodu.  
  
7.  Plik klasy zapisu częściowa Implementacja klasy domeny. W klasie, zapisać definicji brakujący `Get` metodę, która podobnego do następującego:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Jeśli ustawisz **rodzaj** do **magazynu niestandardowego**, również będzie musiał podać `Set` metody. Na przykład:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Kod nie może ustawić wartości w magazynie podczas `Store.InUndoRedoOrRollback` ma wartość true. Zobacz [transakcje i niestandardowej metody ustawiające](#setters).  
  
9. Tworzenie i uruchamianie rozwiązania.  
  
10. Testowanie właściwości. Upewnij się, że próby **Cofnij** i **wykonaj ponownie**.  
  
##  <a name="setters"></a>Niestandardowe ustawiających i transakcji  
 W metodzie zestaw właściwości niestandardowe magazynu nie trzeba otworzyć transakcji, ponieważ metoda nazywa się zwykle w aktywnej transakcji.  
  
 Metoda Set może jednak również nazywane czy użytkownik wywołuje cofania lub ponownego wykonywania, czy transakcja jest wycofywana. Gdy <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> ma wartość true, Set, metoda powinna zachowywać się w następujący sposób:  
  
-   Nie należy wprowadzać zmian w magazynie, takich jak przypisywanie wartości do innych właściwości domeny. Menedżera cofania spowoduje ustawienie wartości.  
  
-   Jednak należy go zaktualizować zasoby zewnętrzne, takie jak bazy danych lub zawartość pliku ani obiektów poza Sklepem. Spowoduje to upewnij się, że są one przechowywane w synchronism z wartościami w magazynie.  
  
 Na przykład:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Aby uzyskać więcej informacji na temat transakcji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Właściwości domeny](../modeling/properties-of-domain-properties.md)   
 [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)