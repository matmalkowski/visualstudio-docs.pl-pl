---
title: "Rozszerzanie funkcjonalności TableAdapter | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0fda0f47084370cd41440311f0cf31c43a69a408
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Rozszerzanie funkcjonalności TableAdapter
Aby rozszerzyć funkcjonalność TableAdapter, dodawanie kodu do pliku częściowej klasy TableAdapter.  
  
 Gdy zmian do elementu TableAdapter w ponownego wygenerowania kodu, który definiuje TableAdapter **Projektant obiektów Dataset**, lub gdy modyfikuje przez Kreatora konfiguracji TableAdapter. Aby zapobiec usunięciu podczas ponownego generowania TableAdapter kodu, Dodaj kod do pliku częściowej klasy TableAdapter.  
  
 Klasy częściowe umożliwiają kodu dla określonej klasy podzielony między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
## <a name="locate-tableadapters-in-code"></a>Zlokalizuj TableAdapters w kodzie  
 Gdy TableAdapters zostały zaprojektowane z **Projektant obiektów Dataset**, klasy TableAdapter, które są generowane, nie są zagnieżdżone klasy <xref:System.Data.DataSet>. TableAdapters znajdują się w przestrzeni nazw na podstawie nazwy TableAdapter skojarzonego elementu dataset. Na przykład jeśli aplikacja zawiera zestaw danych o nazwie `HRDataSet`, TableAdapters znajduje się w `HRDataSetTableAdapters` przestrzeni nazw. (Ten wzorzec jest zgodny konwencji nazewnictwa: *DatasetName* + `TableAdapters`).  
  
 W poniższym przykładzie założono TableAdapter o nazwie `CustomersTableAdapter`znajduje się w projekcie z `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Aby utworzyć klasę częściową dla TableAdapter  
  
1.  Dodaj nową klasę do projektu, przechodząc do **projektu** menu i wybierając **Dodaj klasę**.  
  
2.  Nazwa klasy `CustomersTableAdapterExtended`.  
  
3.  Wybierz **dodać**.  
  
4.  Zastąp kod poprawną przestrzeń nazw i nazwę klasy częściowej projektu w następujący sposób:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)