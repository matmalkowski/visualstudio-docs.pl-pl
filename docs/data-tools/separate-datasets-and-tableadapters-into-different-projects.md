---
title: Oddzielanie zestawów danych i TableAdapters do różnych projektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 304fa17ab036f868b8653efe64a59f68f0452723
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Oddzielne zestawy danych i TableAdapters do różnych projektów
Typizowane zbiory danych zostały rozszerzone, aby [TableAdapters](create-and-configure-tableadapters.md) i klasy zestawu danych mogą być generowane w oddzielnych projekty. Dzięki temu można szybko oddzielne warstwy aplikacji i generowanie aplikacji warstwowych.  
  
W poniższej procedurze opisano sposób korzystania z **Projektant obiektów Dataset** do generowania kodu zestawu danych do projektu, który różni się od projekt, który zawiera wygenerowany kod TableAdapter.  
  
## <a name="separate-datasets-and-tableadapters"></a>Oddzielne zestawy danych i TableAdapters  
Po oddzieleniu kodu zestawu danych z kodu TableAdapter, projekt, który zawiera kod zestawu danych musi znajdować się w bieżącym rozwiązaniu. Jeśli ten projekt nie znajduje się w bieżącym rozwiązaniu, nie będzie dostępny w **projektu DataSet** na liście **właściwości** okna.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Aby podzielić zestawu danych na inny projekt  
  
1.  Otwórz rozwiązanie, które zawiera zestaw danych (pliku xsd).  
  
    > [!NOTE]
    >  Jeśli rozwiązanie zawiera projekt, do którego chcesz oddzielić kodu zestawu danych, Utwórz projekt, lub Dodaj istniejący projekt do rozwiązania.  
  
2.  Kliknij dwukrotnie plik typizowanego obiektu dataset (plik XSD) w **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektant obiektów Dataset**.  
  
3.  Wybierz pusty obszar **Projektant obiektów Dataset**.  
  
4.  W **właściwości** okna, zlokalizuj **projektu DataSet** węzła.  
  
5.  W **projektu DataSet** listy, wybierz nazwę projektu, do którego chcesz wygenerować kod zestawu danych.  
  
     Po wybraniu projektu, do którego chcesz wygenerować kod zestawu danych, **pliku zestawu danych** właściwości jest wypełniane przy użyciu domyślnej nazwy pliku. W razie potrzeby można zmienić tej nazwy. Ponadto, jeśli chcesz wygenerować kod zestawu danych do określonego katalogu, można ustawić **folderu projektu** właściwość na nazwę folderu.  
  
    > [!NOTE]
    >  Po oddzieleniu zestawów danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące klasy częściowe dataset w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowy zestaw danych należy przenieść ręcznie do projektu dataset.  
  
6.  Zapisywanie zestawu danych.  
  
     Kod zestawu danych jest generowany w wybranym projekcie w **projektu DataSet** właściwości oraz **TableAdapter** zostaje wygenerowany kod w bieżącym projekcie.  
  
Domyślnie po oddzieleniu zestawu danych i kod TableAdapter, wynik jest plik odrębny klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie DatasetName.Designer.vb (lub DatasetName.Designer.cs) zawiera kod TableAdapter. Projekt, który jest oznaczany **projektu Dataset** właściwość istnieje plik o nazwie DatasetName.DataSet.Designer.vb (lub DatasetName.DataSet.Designer.cs) zawiera kod zestawu danych.  
  
> [!NOTE]
>  Aby wyświetlić plik wygenerowanej klasy, wybierz zestaw danych lub TableAdapter projektu. Następnie w **Eksploratora rozwiązań**, wybierz pozycję **Pokaż wszystkie pliki**.  
  
## <a name="see-also"></a>Zobacz także
[Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)   
[Wskazówki: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)   
[Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
[ADO.NET](/dotnet/framework/data/adonet/index)