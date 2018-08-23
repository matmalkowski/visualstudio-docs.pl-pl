---
title: Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d22bc992da094ea592f508f3d9e0662977e7e534
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689000"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](https://docs.microsoft.com/visualstudio/modeling/writing-code-to-customise-a-domain-specific-language).  
  
W tej sekcji dowiesz się, jak za pomocą niestandardowego kodu dostępu, modyfikowanie lub tworzenie modelu w języku specyficznym dla domeny.  
  
 Istnieje kilka kontekstów, w których można napisać kod, który współdziała z języka DSL:  
  
-   **Polecenia niestandardowe.** Można utworzyć polecenia, że użytkownicy mogą być wywoływane przez kliknięcie prawym przyciskiem myszy na diagramie i które można modyfikować modelu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Sprawdzanie poprawności.** Można napisać kod, który sprawdza, czy model jest w poprawnym stanie. Aby uzyskać więcej informacji, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Zastępowanie domyślnego zachowania.** Można modyfikować wiele aspektów kod, który jest generowany na podstawie DslDefinition.dsl. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformacja tekstu.** Możesz tworzyć szablony tekstowe, które zawierają kod, który uzyskuje dostęp do modelu i generuje plik tekstowy, na przykład w celu generowania kodu programu. Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Inne rozszerzenia programu Visual Studio.** Można napisać oddzielne rozszerzenia VSIX, które odczytują i modyfikowania modeli. Aby uzyskać więcej informacji, zobacz [porady: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Wystąpienia klas, które można zdefiniować w DslDefinition.dsl są przechowywane w strukturze danych o nazwie *Store In-Memory* (ISP) lub *Store*. Klas zdefiniowanych w DSL zawsze zająć Store jako argumentu do konstruktora. Jeśli na przykład modem DSL definiuje klasę o nazwie przykładowy:  
  
 `Example element = new Example (theStore);`  
  
 Przechowywanie obiektów w Store (a nie tylko jako zwykłe obiektów) zapewnia kilka korzyści.  
  
-   **Transakcje**. Można grupować seria powiązanych zmian do transakcji:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Jeśli wystąpi wyjątek podczas wprowadzania zmian, dzięki czemu końcowy Commit() nie jest wykonywane, Store zostaną zresetowane do jego poprzedniego stanu. Pomaga to upewnić się, że błędy nie spowodują pozostawienia modelu w stanie niespójnym. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Relacje binarne**. Jeśli zdefiniujesz relacje między dwoma klasami, na obu końcach mają właściwości, która przechodzi do drugiej stronie. Po obu stronach są zawsze zsynchronizowane. Na przykład jeśli zdefiniujesz relacje planowania przy użyciu role o nazwach elementów nadrzędnych i podrzędnych, można napisać:  
  
     `John.Children.Add(Mary)`  
  
     Oba z następujących wyrażeń są teraz wartość true:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Można również osiągnąć ten sam efekt, pisząc:  
  
     `Mary.Parents.Add(John)`  
  
     Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Reguły i zdarzenia**. Można zdefiniować reguły, które są uruchamiane zawsze, gdy określone zmiany zostały wprowadzone. Reguły są używane na przykład do kształtów na diagramie na bieżąco z elementami modelu, które stanowią one. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Serializacja**. Store udostępnia standardowy sposób wykonywania serializacji obiektów, zawartych w pliku. Można dostosować zasady do serializacji i deserializacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)



