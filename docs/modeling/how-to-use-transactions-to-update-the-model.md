---
title: "Porady: Użyj transakcji, aby zaktualizować Model | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ecd9645bfb202d83bf672d03d3c6903a889677f9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Porady: użycie transakcji do aktualizacji modelu
Transakcje upewnij się, że zmiany wprowadzone w magazynie są traktowane jako grupa. Zmiany, które są zgrupowane można zatwierdzona lub wycofana jako pojedyncza jednostka.  
  
 Po każdej zmianie kodu źródłowego modyfikuje, dodaje lub usuwa dowolny element w magazynie w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania SDK, należy wykonać czynności wewnątrz transakcji. Musi być wystąpieniem active <xref:Microsoft.VisualStudio.Modeling.Transaction> skojarzone ze sklepem, w przypadku zmiany. Dotyczy to wszystkich elementów modelu, relacje kształtów, diagramy i ich właściwości.  
  
 Mechanizm transakcji pomaga uniknąć niespójny stan. Jeśli wystąpi błąd podczas transakcji, wszystkie zmiany zostaną wycofane. Gdy użytkownik wykonuje polecenie Cofnij, każdą transakcję ostatnie są traktowane jako pojedynczy krok. Użytkownik nie można cofnąć części zmiany, chyba że jawnie umieść je w oddzielne transakcje.  
  
## <a name="opening-a-transaction"></a>Otwieranie transakcji  
 Najwygodniejsza metoda zarządzania transakcji jest i `using` instrukcji ujęta w `try...catch` instrukcji:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Jeśli wyjątek, który uniemożliwia ostatecznych `Commit()` występuje podczas zmiany, magazynie zostaną zresetowane do jego poprzedniego stanu. Dzięki temu można upewnij się, że błędy nie zostawiają modelu w niespójnym stanie.  
  
 Możesz wprowadzić dowolną liczbę zmian w jednej transakcji. Można otwierać nowych transakcji w aktywnej transakcji. Transakcje zagnieżdżone należy przekazać ani wycofać przed zakończeniem zawierającego transakcji. Aby uzyskać więcej informacji, zobacz przykład <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> właściwości.  
  
 Aby zmiany były trwałe, należy `Commit` transakcji przed jego usunięcia. Jeśli wystąpi wyjątek, który nie zawiera wewnątrz transakcji, magazynie zostaną zresetowane do stanu przed wprowadzeniem zmian.  
  
## <a name="rolling-back-a-transaction"></a>Wycofywanie transakcji  
 Aby upewnić się, że magazyn pozostaje w lub powraca do stanu przed transakcji, użyj jednej z tych taktyk:  
  
1.  Zgłoś wyjątek, który nie zawiera się w zakresie transakcji.  
  
2.  Jawnie wycofać transakcji:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Transakcje nie wpływają na obiekty z systemem innym niż magazynu  
 Transakcje określają tylko stanu magazynu. Nie można ich cofnąć częściowe zmiany, które zostały wprowadzone do elementów zewnętrznych, takich jak pliki, bazy danych lub obiektów, które zostały zadeklarowane ze zwykłej typów poza definicją DSL.  
  
 Jeśli wyjątek mogą pozostać taka zmiana niespójna ze sklepem, powinien uwzględniać możliwości wystąpienia programu obsługi wyjątków. Jednym ze sposobów upewnij się, że zasobów zewnętrznych pozostają zsynchronizowane z obiektami magazynu jest połączenie każdego obiektu zewnętrznego do elementu w magazynie przy użyciu programów obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Reguły Fire na końcu transakcji  
 Na koniec transakcji zanim zostanie usunięty, transakcji, reguły dołączone do elementów w magazynie są uruchamiane. Każda reguła stanowi metodę, która jest stosowana do elementu modelu, który został zmieniony. Na przykład "Napraw" reguł, które zaktualizowany stan kształtu, gdy zmieniono jego element modelu, a które tworzenie kształtu po utworzeniu elementu modelu. Nie ma żadnych kolejność uruchamiania określony. Zmiany wprowadzone przez regułę mogą wyzwalać inną regułę.  
  
 Można zdefiniować własnych reguł. Aby uzyskać więcej informacji o regułach, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
 Zasady nie uruchamiają się po cofania, powtórz lub polecenia rollback.  
  
## <a name="transaction-context"></a>Kontekst transakcji  
 Każdą transakcję ma słownika, w którym można przechowywać wszystkie informacje, które mają:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Jest to szczególnie przydatne w przypadku przesyłania informacji między reguły.  
  
## <a name="transaction-state"></a>Stan transakcji  
 W niektórych przypadkach potrzebne w celu uniknięcia propagowanie zmian, jeśli zmiana jest spowodowany przez Cofanie lub ponawianie transakcji. Może to się zdarzyć na przykład podczas pisania obsługi wartość właściwości, który umożliwia zaktualizowanie inną wartość w magazynie. Ponieważ operację cofnięcia zmiany resetuje wszystkie wartości w magazynie do poprzedniego stanu, nie jest niezbędne do obliczenia zaktualizowane wartości. Użyj tego kodu:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Reguły mogą zostać wywołane, podczas magazynu są wstępnie ładowane z pliku. Aby uniknąć odpowiadać na te zmiany, należy użyć:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```