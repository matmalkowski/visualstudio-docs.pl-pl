---
title: Umożliwia tworzenie relacji między zestawów danych DataRelation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 94fb9217b779d00314b2a188ae2fe6f7d0ba4bb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="create-relationships-between-datasets"></a>Utwórz relacje między zbiory danych
Zestawy danych, które zawierają dane dotyczące tabel użyj <xref:System.Data.DataRelation> obiektów do reprezentowania relacji nadrzędny/podrzędny między tabelami i do zwrócenia powiązane rekordy od siebie nawzajem. Dodawanie tabel powiązanych do zestawów danych przy użyciu **Kreator konfiguracji źródła danych**, lub **Projektant obiektów Dataset**, tworzy i konfiguruje <xref:System.Data.DataRelation> obiekt.  
  
<xref:System.Data.DataRelation> Obiektu wykonuje dwie funkcje:  
  
-   Go można udostępnić rekordy związane z rekordu, który użytkownik pracuje z. Zapewnia podrzędne rekordy w rekord nadrzędny (<xref:System.Data.DataRow.GetChildRows%2A>) i rekordu nadrzędnego, jeśli pracujesz z podrzędnego rekordu (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
-   Można go wymuszać ograniczenia integralności referencyjnej, takich jak usuwanie rekordów podrzędnych podczas usuwania rekordu nadrzędnego.  
  
Ważne jest, aby zrozumieć różnicę między sprzężenia wartość true, a funkcja <xref:System.Data.DataRelation> obiektu. Wartość true, sprzężenia rekordy są pobierane z tabelą nadrzędną i podrzędną i poddane pojedynczy, płaski zestaw rekordów. Jeśli używasz <xref:System.Data.DataRelation> obiektu, a nie nowy zestaw rekordów. Zamiast tego DataRelation śledzi relacje między tabelami i przechowuje nadrzędne i podrzędne rekordy w synchronizacji.  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation — obiekty i ograniczenia  
A <xref:System.Data.DataRelation> obiekt służy do tworzenia i wymusić następujące ograniczenia:  
  
-   Ograniczenia unique, który gwarantuje, że kolumny w tabeli nie zawiera duplikatów.  
  
-   Ograniczenie klucza obcego, którego można użyć w celu zachowania integralności referencyjnej między tabelą nadrzędną a podrzędną w zestawie danych.  
  
Ograniczenia, które określisz w <xref:System.Data.DataRelation> obiektu są implementowane przez automatyczne utworzenie odpowiednich obiektów lub właściwości. Jeśli utworzysz ograniczenie klucza obcego za pomocą <xref:System.Data.DataRelation> obiektu, wystąpień <xref:System.Data.ForeignKeyConstraint> klasy zostaną dodane do <xref:System.Data.DataRelation> obiektu <xref:System.Data.DataRelation.ChildKeyConstraint%2A> właściwości.  
  
Ograniczenia unique jest zaimplementowana przez wystarczy wybrać ustawienie <xref:System.Data.DataColumn.Unique%2A> właściwość kolumny danych `true` lub dodając wystąpienia <xref:System.Data.UniqueConstraint> klasa do <xref:System.Data.DataRelation> obiektu <xref:System.Data.DataRelation.ParentKeyConstraint%2A> właściwości. Aby uzyskać informacje na wstrzymanie ograniczenia w zestawie danych, zobacz [wyłączanie ograniczeń w czasie wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Więzy integralności  
W ramach ograniczenie klucza obcego można określić zasady integralności referencyjnej, które są stosowane w trzech miejscach:  
  
-   Podczas aktualizacji rekordu nadrzędnego  
  
-   Gdy zostaje usunięty rekord nadrzędny  
  
-   Po zmianie jest zaakceptowane lub odrzucone  
  
Zasady, które mogą ułatwić są określone w <xref:System.Data.Rule> wyliczenie i są wymienione w poniższej tabeli.  
  
|Klucz obcy ograniczenia reguły|Akcja|  
|----------------------------------|------------|  
|<xref:System.Data.Rule.Cascade>|(Update lub delete) do nadrzędnego rekordu również zmian w powiązanych rekordów w tabeli podrzędnej.|  
|<xref:System.Data.Rule.SetNull>|Podrzędne rekordy nie zostaną usunięte, ale ma ustawioną wartość klucza obcego w podrzędne rekordy <xref:System.DBNull>. To ustawienie, podrzędne rekordy może pozostać "oddzielone" — to znaczy ich nie mają relacji nadrzędny rekordów. **Uwaga:** przy użyciu tej reguły może spowodować nieprawidłowe dane w tabeli podrzędnej.|  
|<xref:System.Data.Rule.SetDefault>|Klucz obcy w rekordach podrzędnych ma ustawioną wartość domyślną (zgodnie z ustaleniami kolumny <xref:System.Data.DataColumn.DefaultValue%2A> właściwości).|  
|<xref:System.Data.Rule.None>|Nie zmian do rekordów podrzędnych. To ustawienie, podrzędne rekordy mogą zawierać odwołania do rekordów nieprawidłowy element nadrzędny.|  
  
Aby uzyskać więcej informacji o aktualizacjach w tabelach zestawu danych, zobacz [zapisać danych w bazie danych](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Tylko ograniczenie relacji  
Po utworzeniu <xref:System.Data.DataRelation> obiektu, mieć możliwość określenia, czy relacja można użyć tylko w celu wymuszenia ograniczenia — to znaczy go zostanie nie również służyć do powiązane rekordy dostępu. Ta opcja umożliwia wygenerować obiektu dataset jest nieco bardziej wydajne i zawiera metody mniej niż jeden z możliwością powiązane rekordy. Jednak nie można uzyskać dostępu do powiązanych rekordów. Na przykład relacji tylko do ograniczenia uniemożliwia usuwanie rekordu nadrzędnego, który nadal ma podrzędne rekordy i podrzędne rekordy nie może uzyskać dostępu do obiektu nadrzędnego.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Ręczne tworzenie relacji danych w Projektancie obiektów Dataset  
Podczas tworzenia tabel danych za pomocą narzędzi do projektowania danych w programie Visual Studio, relacje są tworzone automatycznie, jeśli można zbierać informacje ze źródła danych. Jeśli ręcznie dodać tabele danych z **DataSet** karty **przybornika**, może być konieczne ręczne tworzenie relacji. Aby uzyskać informacje na temat tworzenia <xref:System.Data.DataRelation> obiektów programowo, zobacz [Dodawanie DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).  
  
Relacje między tabelami danych są wyświetlane jako wiersze w **Projektant obiektów Dataset**, z klucza i wartości infinity symbolu przedstawiające aspekt relacji jeden do wielu. Domyślnie nazwa relacji nie są wyświetlane na powierzchni projektu.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Można utworzyć relacji między tabelami dwóch danych  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Przeciągnij **relacji** obiekt z **DataSet** przybornika do tabeli danych podrzędnej w relacji.  
  
     **Relacji** zostanie otwarte okno dialogowe wypełnianie **tabeli podrzędnej** pola z tabeli, który został przeciągnięty **relacji** obiekt na.  
  
3.  Wybierz tabelę nadrzędną z **tabeli nadrzędnej** pole. Tabela nadrzędna zawiera rekordy na stronie "jeden" w relacji jeden do wielu.  
  
4.  Sprawdź, czy tabela podrzędna poprawne są wyświetlane w **tabeli podrzędnej** pole. Tabeli podrzędnej zawiera rekordy na stronie "wielu" relacji jeden do wielu.  
  
5.  Wpisz nazwę relacji w **nazwa** pola lub pozostaw nazwę domyślną, w oparciu o wybrane tabele. Jest to nazwa rzeczywistych <xref:System.Data.DataRelation> obiektu w kodzie.  
  
6.  Wybierz kolumny, które sprzężenia w **kolumn klucza** i **kolumny klucza obcego** listy.  
  
7.  Wybierz, czy można utworzyć relacji, ograniczenie lub obu.   
  
8.  Wybierz lub wyczyść **relacji zagnieżdżonych** pole. Wybranie tej opcji ustawia <xref:System.Data.DataRelation.Nested%2A> właściwości `true`, i powoduje wierszy relacji do być zagnieżdżone wewnątrz kolumny nadrzędnej, gdy te wiersze są zapisywane jako dane XML lub synchronizowane z elementem podrzędnym <xref:System.Xml.XmlDataDocument>. Aby uzyskać więcej informacji, zobacz [zagnieżdżania DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).  
  
9. Ustaw zasady, które mają zostać wymuszone, gdy wprowadzasz zmiany do rekordów w tych tabelach. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Rule>.  
  
10. Kliknij przycisk **OK** do utworzenia relacji. Zostanie wyświetlony wiersz relacji w Projektancie między dwiema tabelami.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Aby wyświetlić nazwę relacji w Projektancie obiektów Dataset  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Z **danych** menu, wybierz opcję **Pokaż etykiety relacji** polecenie, aby wyświetlić nazwę relacji. Usuń zaznaczenie tego polecenia, aby ukryć nazwę relacji.

## <a name="see-also"></a>Zobacz także
[Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)