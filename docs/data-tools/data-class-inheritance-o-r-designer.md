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
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756740"
---
# <a name="data-class-inheritance-or-designer"></a>Dziedziczenie klas danych (Projektanta obiektów relacyjnych)

Podobnie jak inne obiekty klasy LINQ do SQL można użyć dziedziczenia i pochodzić z innych klas. W kodzie można określić relacji dziedziczenia między obiektami przez zadeklarowanie, że jedna klasa dziedziczy z innej. W bazie danych relacji dziedziczenia są tworzone na kilka sposobów. **Projektant obiektów relacyjnych** (**Projektanta obiektów relacyjnych**) obsługuje koncepcja dziedziczenia pojedynczej tabeli, jak często jest zaimplementowana w systemach relacyjnych.

W dziedziczeniu pojedynczej tabeli Brak tabeli pojedynczej bazy danych, która zawiera kolumny zarówno podstawowego, jak i pochodne klasy. Z danych relacyjnych kolumny rozróżniacza zawiera wartość, która określa, która klasa należy żadnych rekordów. Rozważmy na przykład `Persons` tabeli, która zawiera wszystkich stosowanych przez firmę. Niektórzy użytkownicy są pracownikami i niektórzy użytkownicy są menedżerów. `Persons` Tabela zawiera kolumny o nazwie `Type` mający wartość 1 dla menedżerów i wartość 2 dla pracowników. `Type` Kolumna jest kolumną rozróżniacza. W tym scenariuszu można utworzyć podklasy pracowników i wypełnienie klasy tylko te rekordy, które mają `Type` wartość 2.

Po skonfigurowaniu dziedziczenia klas jednostek przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], przeciągnij pojedynczej tabeli, która zawiera dane dziedziczenia do projektanta dwa razy: raz dla każdej klasy w hierarchii dziedziczenia. Po dodaniu tabel do projektanta, podłącz je z elementem dziedziczenia z **Projektant obiektów relacyjnych** przybornika, a następnie ustaw cztery dziedziczenia właściwości w **właściwości** okna.

## <a name="inheritance-properties"></a>Dziedziczenie właściwości

W poniższej tabeli wymieniono właściwości dziedziczenia i ich opisy:

|Właściwość|Opis|
|--------------|-----------------|
|**Właściwość rozróżniacza**|Właściwość (zamapowany na kolumny), która określa, która klasa należy bieżącego rekordu.|
|**Wartość dyskryminatora klasy podstawowej**|Wartość (w kolumnie wyznaczony jako **właściwość rozróżniacza**) określa, czy rekord jest klasy podstawowej.|
|**Wartość dyskryminatora klasy pochodnej**|Wartość (WE właściwości wyznaczony jako **właściwość rozróżniacza**) określa, czy rekord jest klasy pochodnej.|
|**Domyślnej dziedziczenia**|Klasa, która zostanie wypełnione, gdy wartość właściwości wyznaczony jako **właściwość rozróżniacza** nie pasuje do żadnej **wartość dyskryminatora klasy podstawowej** lub **klas pochodnych Wartość dyskryminatora**.|

Tworzenie modelu obiektów, która korzysta z dziedziczenia i odpowiada relacyjnej bazie danych może być nieco trudne. Ten temat zawiera informacje o podstawowych pojęć i poszczególnych właściwości, które są wymagane do konfigurowania dziedziczenia. W poniższych tematach przedstawiono jaśniejszy objaśnienie sposobu konfigurowania dziedziczenia z **Projektanta obiektów relacyjnych**.

|Temat|Opis|
|-----------|-----------------|
|[Porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Opisuje sposób konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu **Projektanta obiektów relacyjnych**.|
|[Wskazówki: Tworzenie LINQ w klasach SQL za pomocą pojedynczej tabeli dziedziczenia (Projektanta obiektów relacyjnych)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Instrukcje krok po kroku dotyczące konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu **Projektanta obiektów relacyjnych**.|

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie LINQ w klasach SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Wskazówki: Tworzenie LINQ w klasach SQL za pomocą pojedynczej tabeli dziedziczenia (Projektanta obiektów relacyjnych)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Wprowadzenie](/dotnet/framework/data/adonet/sql/linq/getting-started)