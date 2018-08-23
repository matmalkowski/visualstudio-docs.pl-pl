---
title: 'Porady: wyświetlanie powiązanych danych w Windows Forms aplikacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fc62789860cc10f5c410849936715a8ef82eae3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684093"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Porady: wyświetlanie powiązanych danych w aplikacji Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyświetlić dane dotyczące przez przeciąganie elementów, które współużytkują ten sam węzeł główna tabela z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formularza. Na przykład, jeśli użytkownik ma danych źródłowych, która ma `Customers` tabeli i powiązane `Orders` tabeli, powinny zostać wyświetlone obie tabele jako węzłów najwyższego poziomu (w widoku drzewa) **źródeł danych** okna. Rozwiń `Customers` węzeł, aby zobaczyć kolumn i zauważysz, że ostatnia kolumna na liście jest rozwijany węzeł reprezentujący `Orders` tabeli. Ten węzeł reprezentuje powiązane zamówienia dla klienta. Oznacza to, jeśli chcesz utworzyć formularz, który pozwala wybrać klienta, a następnie Wyświetl listę zamówień tego klienta przeciągniesz elementy, które mają być wyświetlane z tym jednej hierarchii.  
  
 ![Okno źródeł danych, przedstawiający relacji](../data-tools/media/datasources2.gif "DataSources2")  
Tworzenie formantów powiązanych z danymi, które wyświetlania powiązanych rekordów  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") wersja wideo tego tematu, zobacz [jak powiązane tabele aktualizacji I:](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>Aby utworzyć formanty, które wyświetlania powiązanych rekordów  
  
1.  Otwórz formularz w [Windows Forms Designer](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Otwórz **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [porady: otwieranie okna źródeł danych](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Rozwiń węzeł reprezentujący tabeli nadrzędnej w relacji. (Tabela nadrzędna jest tabeli na stronie "jeden" w relacji jeden do wielu).  
  
4.  Przeciągnij wszystkie elementy, które mają być wyświetlane z tabeli nadrzędnej w relacji z **źródeł danych** okna do formularza.  
  
5.  Tabele powiązane podrzędne są wyświetlane jako węzły można rozwijać w dolnej części listy kolumn tabeli nadrzędnej. Przeciągnij elementy, które mają być wyświetlane z odpowiedni węzeł do formularza.  
  
    > [!NOTE]
    >  Przeciąganie elementów z węzłów najwyższego poziomu tworzy oddzielny niezwiązanych ze sobą [BindingSource, składnik](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) ułatwiających nie, nawigowania między rekordami powiązane. Aby powiązać dane dotyczące należy wybrać tabele z tym samym węźle hierarchicznej.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Instrukcje: nawigowanie po danych za pomocą kontrolki BindingNavigator formularzy Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)