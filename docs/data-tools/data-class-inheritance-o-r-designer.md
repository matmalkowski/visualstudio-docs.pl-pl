---
title: Dziedziczenie klas danych (Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1ed71ad820e6e55d05bc7cc6c7bf62b45f58f55
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="data-class-inheritance-or-designer"></a>Dziedziczenie klas danych (Projektanta obiektów relacyjnych)

Inne obiekty, takich jak [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy można użyć dziedziczenia i pochodzić z innych klas. W kodzie można określić relacji dziedziczenia między obiektami przez zadeklarowanie, że jedna klasa dziedziczy z innej. W bazie danych relacji dziedziczenia są tworzone na kilka sposobów. [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) Obsługuje koncepcja dziedziczenia pojedynczej tabeli, jak często jest zaimplementowana w systemach relacyjnych.

W dziedziczeniu pojedynczej tabeli Brak tabeli pojedynczej bazy danych, która zawiera kolumny zarówno podstawowego, jak i pochodne klasy. Z danych relacyjnych kolumny rozróżniacza zawiera wartość, która określa, która klasa należy żadnych rekordów. Rozważmy na przykład tabeli osoby, która zawiera wszystkich stosowanych przez firmę. Niektórzy użytkownicy są pracownikami i niektórzy użytkownicy są menedżerów. Tabela osób zawiera kolumny o nazwie typu, który ma wartość 1 dla menedżerów i wartość 2 dla pracowników. Kolumna typu jest kolumny rozróżniacza. W tym scenariuszu można utworzyć podklasy pracowników i wypełnić klasy z tylko te rekordy, które mają wartość typu 2.

Po skonfigurowaniu dziedziczenia klas jednostek przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], przeciągnij pojedynczej tabeli, która zawiera dane dziedziczenia do projektanta dwa razy: raz dla każdej klasy w hierarchii dziedziczenia. Po dodaniu tabel do projektanta, podłącz je z elementem dziedziczenia z **Projektant obiektów relacyjnych** przybornika, a następnie ustaw cztery dziedziczenia właściwości w **właściwości** okna.

## <a name="inheritance-properties"></a>Dziedziczenie właściwości

W poniższej tabeli wymieniono właściwości dziedziczenia i ich opisy:

|Właściwość|Opis|
|--------------|-----------------|
|Właściwość rozróżniacza|Właściwość (zamapowany na kolumny), która określa, która klasa należy bieżącego rekordu.|
|Wartość dyskryminatora klasy podstawowej|Wartość (w kolumnie wyznaczony jako właściwość rozróżniacza), która określa, czy rekord jest klasy podstawowej.|
|Wartość dyskryminatora klasy pochodnej|Wartość (WE właściwości wyznaczony jako właściwość rozróżniacza), która określa, czy rekord jest klasy pochodnej.|
|Domyślnej dziedziczenia|Klasy, które powinny zostać wypełnione, gdy wartość właściwości wyznaczony jako **właściwość rozróżniacza** nie pasuje do żadnej **wartość dyskryminatora klasy podstawowej** lub **klas pochodnych Wartość dyskryminatora**.|

Tworzenie modelu obiektów, która korzysta z dziedziczenia i odpowiada relacyjnej bazie danych może być nieco trudne. Ten temat zawiera informacje o podstawowych pojęć i poszczególnych właściwości, które są wymagane do konfigurowania dziedziczenia. W poniższych tematach przedstawiono jaśniejszy objaśnienie sposobu konfigurowania dziedziczenia z [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

|Temat|Opis|
|-----------|-----------------|
|[Porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Opisuje sposób konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|
|[Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (Projektanta obiektów relacyjnych)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Zawiera instrukcje krok po kroku dotyczące konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie klasy LINQ do SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (Projektanta obiektów relacyjnych)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Wprowadzenie](/dotnet/framework/data/adonet/sql/linq/getting-started)