---
title: Dostosowywanie języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f7fd63546f7d85ddbcc7661ac600a56bd340e6ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31965229"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Napisz kod umożliwiający dostosowanie języka specyficznego dla domeny

W tej sekcji przedstawiono sposób użycia niestandardowego kodu dostępu, zmodyfikować lub utworzyć model języka specyficznego dla domeny.

Istnieje kilka kontekstów, w których można napisać kod, który działa z DSL:

-   **Polecenia niestandardowe.** Można utworzyć polecenie użytkowników można wywołać, klikając prawym przyciskiem myszy na diagramie, czy które można modyfikować modelu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

-   **Sprawdzanie poprawności.** Można napisać kod, który sprawdza, czy model jest w odpowiednim stanie. Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).

-   **Zastępowanie domyślnego zachowania.** Można modyfikować wiele aspektów kod, który jest generowany na podstawie DslDefinition.dsl. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).

-   **Transformacji tekstu.** Można napisać szablony tekstu, które zawierają kod, który uzyskuje dostęp do modelu i generuje plik tekstowy, na przykład w celu generowania kodu programu. Aby uzyskać więcej informacji, zobacz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

-   **Inne rozszerzenia programu Visual Studio.** Można napisać oddzielne rozszerzenia VSIX, które odczytywać i modyfikować modeli. Aby uzyskać więcej informacji, zobacz [porady: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Wystąpienia klas zdefiniowanych w DslDefinition.dsl są przechowywane w strukturze danych o nazwie *magazynu w pamięci* (ISP) lub *magazynu*. Klas zdefiniowanych w DSL zawsze przyjmować sklepu jako argument do konstruktora. Na przykład, jeśli Twoje DSL definiuje klasę o nazwie przykładzie:

`Example element = new Example (theStore);`

utrzymywanie obiektów w magazynie (a nie tylko jako zwykłe obiektów) zapewnia kilka korzyści.

-   **Transakcje**. Można grupować szereg powiązanych zmian do transakcji:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Jeśli wystąpi wyjątek podczas zmiany, dzięki czemu Commit() końcowego nie jest wykonywane, magazynie zostaną zresetowane do jego poprzedniego stanu. Dzięki temu można się upewnić, że błędy nie zostawiają modelu w niespójnym stanie. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Relacje binarne**. Po zdefiniowaniu relację między dwiema klasami wystąpień obu końców ma właściwość, która przechodzi do drugiej. Dwa końce zawsze są synchronizowane. Na przykład w przypadku definiowania relacji planowania z rolami o nazwie elementów nadrzędnych i podrzędnych, można zapisać:

     `John.Children.Add(Mary)`

     Następujących wyrażeń spełnione są obydwa teraz:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Można również osiągnąć ten sam efekt, wpisując:

     `Mary.Parents.Add(John)`

     Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

-   **Reguły i zdarzenia**. Można zdefiniować reguły uruchamianych przy każdym określone zmiany zostały wprowadzone. Zasady są używane, na przykład do kształtów na diagramie zapewnienie aktualności z elementami modelu, które stanowią one. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

-   **Serializacja**. Magazyn udostępnia standardowy sposób serializacji obiektów, które zawiera do pliku. Można dostosować zasady serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz [dostosowywania magazynu plików i serializacja XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)