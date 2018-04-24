---
title: Wpisane a nietypizowane zbiory danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5819a208a54a5a4235330216e46b5e17f1260fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="typed-vs-untyped-datasets"></a>Wpisane a nietypizowane zbiory danych
Typizowany zestaw dataset jest zestawu danych, który najpierw pochodzi od podstawy <xref:System.Data.DataSet> klasy, a następnie używa informacji z **Projektant obiektów Dataset**, który jest przechowywany w pliku XSD, aby wygenerować nowy, silnie typizowanej klasy dataset. Informacje ze schematu (tabel, kolumn i tak dalej) są generowane i skompilowany w tej nowej klasy dataset jako zestaw obiektów pierwszej klasy i właściwości. Ponieważ typizowanego obiektu dataset pochodząca od klasy podstawowej <xref:System.Data.DataSet> klasy typizowanej klasy przyjęto założenie, wszystkie funkcje <xref:System.Data.DataSet> klasy i mogą być używane z metod, które przyjmują wystąpienia <xref:System.Data.DataSet> klasy jako parametr.

 Nietypizowanego zestawu danych z kolei ma brak odpowiednich wbudowanego schematu. Jak typizowanego obiektu dataset nietypizowanego zestawu danych zawiera tabele, kolumny i tak dalej, ale te są widoczne tylko w kolekcjach. (Jednak utworzony ręcznie tabele i inne elementy w nietypizowanego zestawu danych, można wyeksportować struktury zestawu danych jako schematu za pomocą zestawu danych <xref:System.Data.DataSet.WriteXmlSchema%2A> metody.)

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Kontrastem dostępu do danych w zestawach danych typu i bez typu
 Klasy typizowanego zestawu danych ma modelu obiektów, które mają jej właściwości na rzeczywiste nazwy tabel i kolumn. Na przykład jeśli pracujesz z typizowanego zestaw danych, można się odwołać kolumny przy użyciu kodu, takie jak następujące:

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 Z kolei podczas pracy z zestawem danych bez typu, jest równoważne kodu:

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Dostęp typu nie jest tylko czytelności, ale również pełni obsługiwane przez funkcję IntelliSense w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **edytora kodu**. Oprócz łatwiej współpracować, składnia typizowanego obiektu dataset zawiera typ sprawdzenie w czasie kompilacji, co pozwala znacznie zmniejszyć prawdopodobieństwo wystąpienia błędów w przypisywanie wartości do elementów członkowskich zestawu danych. Jeśli zmienisz nazwę kolumny w Twojej <xref:System.Data.DataSet> klasy, a następnie skompilować aplikację, komunikat o błędzie kompilacji. Klikając dwukrotnie błąd kompilacji w **listy zadań**, można przejść bezpośrednio do wiersze kodu, które odwołują się do starej nazwy kolumny. Dostęp do tabel i kolumn w typizowanego zestawu danych również jest nieco większa w czasie wykonywania, ponieważ dostęp jest określany w czasie kompilacji, nie za pomocą kolekcji w czasie wykonywania.

 Mimo że typizowane zbiory danych ma wiele zalet, nietypizowanego zestawu danych jest przydatne w różnych sytuacjach. Najbardziej oczywisty scenariusz jest gdy brak schematu nie jest dostępny dla zestawu danych. Taka sytuacja może wystąpić, na przykład jeśli aplikacja prowadzi interakcję z składnik, który zwraca dataset, ale nie znasz z wyprzedzeniem jego struktura jest. Podobnie są razy podczas pracy z danymi, które nie ma on struktury statycznych, przewidywalnych. W takim przypadku jest niemożliwe do użycia typizowanego zestaw danych, ponieważ będzie musiał ponownie wygenerować klasy typizowanego zestawu danych z każdej zmiany w strukturze danych.

 Ogólnie rzecz biorąc są wielokrotnie podczas można dynamicznie utworzyć zestawu danych bez schematu dostępne. W takim przypadku zestawu danych jest po prostu wygodny struktury zachować informacje, jak długo dane można przedstawić w sposób relacyjnej. W tym samym czasie można korzystać z możliwości zestawu danych, takie jak możliwość serializować informacji do przekazania do inny proces lub zapisać pliku XML.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi zestawów danych](../data-tools/dataset-tools-in-visual-studio.md)