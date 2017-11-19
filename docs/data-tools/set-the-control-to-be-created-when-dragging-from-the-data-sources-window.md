---
title: "Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 12b8c166873802e3c0e6a8d4e73ff1b686229222
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych
Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na projektanta WPF lub Projektant formularzy systemu Windows. Każdy element **źródeł danych** okno ma domyślny formant, który jest tworzony podczas przeciągania do projektanta. Można jednak utworzyć inny formant.  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Ustawianie formantów, które ma zostać utworzony dla tabel danych lub obiektów  
Przed przeciągnij elementy, które reprezentują tabel danych lub obiektów z **źródeł danych** okna, można wybrać do wyświetlania wszystkich danych w jeden formant lub do wyświetlania każdej kolumny lub właściwości w oddzielnych formantu.  
  
W tym kontekście termin *obiektu* odwołuje się do obiektu biznesowego niestandardowych, jednostki (w modelu Entity Data Model) lub obiektu zwróconego przez usługę.  
  
### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Aby ustawić formantów, które ma zostać utworzony dla tabel danych lub obiektów  
  
1.  Upewnij się, że projektant WPF lub Projektant formularzy systemu Windows jest otwarty.  
  
2.  W **źródeł danych** okna, zaznacz element, który reprezentuje tabelę danych lub obiekt, którego chcesz ustawić.  
  
3.  Kliknij menu rozwijane elementu, a następnie kliknij jedną z następujących elementów w menu:  
  
    -   Aby wyświetlić każdego pola danych w formancie oddzielne, kliknij **szczegóły**. Przeciągnięcie elementu danych do projektanta, ta akcja spowoduje utworzenie inny formant powiązany z danymi dla każdej kolumny lub właściwości nadrzędnej danych tabeli lub obiektu oraz etykiety dla każdego formantu.  
  
    -   Aby wyświetlić wszystkie dane w jeden formant, wybierz inny formant na liście, takie jak **DataGrid** lub **listy** w aplikacji WPF lub **DataGridView** w formularzach systemu Windows aplikacja.  
  
    Lista dostępnych formantów zależy, na których projektant otwartych, która wersja architektury .NET Framework elementy docelowe projektu i czy dodano niestandardowe formanty danych obsługi powiązanie z **przybornika**. Jeśli formant, który chcesz utworzyć nie jest na liście dostępnych formantów, można dodać kontrolki do listy. Aby uzyskać więcej informacji, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
    Aby dowiedzieć się, jak utworzyć niestandardowego formantu formularzy systemu Windows, który można dodać do listy formantów dla tabel danych lub obiektów w **źródeł danych** okna, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego złożone danych Powiązanie](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Ustawianie formantów, które ma zostać utworzony dla właściwości lub kolumny danych  
Przeciągania elementu, który reprezentuje kolumnę lub właściwości obiektu z **źródeł danych** okna projektanta, można ustawić formantu do utworzenia.  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Aby ustawić formantów, które ma zostać utworzony dla kolumny lub właściwości  
  
1.  Upewnij się, że projektant WPF lub Projektant formularzy systemu Windows jest otwarty.  
  
2.  W **źródeł danych** okna, rozwiń odpowiednią tabelę lub obiekt, aby wyświetlić właściwości lub kolumny.  
  
3.  Wybierz każdej kolumny lub właściwości, dla którego chcesz ustawić formantu do utworzenia.  
  
4.  Kliknij menu rozwijane w kolumnie lub właściwości, a następnie wybierz formant, który chcesz utworzyć, gdy element zostanie przeciągnięty do projektanta.  
  
     Listę dostępnych formantów zależy, na których projektant otwartych, która wersja architektury .NET Framework elementy docelowe projektu i które niestandardowe formanty obsługujące, możesz powiązania danych zostały dodane do **przybornika**. Jeśli formant, który chcesz utworzyć znajduje się na liście dostępnych formantów, można dodać kontrolki do listy. Aby uzyskać więcej informacji, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Aby dowiedzieć się, jak utworzyć niestandardowego formantu, który można dodać do listy formantów dla kolumn danych lub właściwości w **źródeł danych** okna, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Jeśli nie chcesz utworzyć formant do kolumny lub właściwości, wybierz **Brak** w menu rozwijanym. Jest to przydatne, jeśli chcesz przeciągnąć do projektanta tabeli nadrzędnej lub obiekt, ale nie chcesz dołączyć do określonej kolumny lub właściwości.  
  
## <a name="see-also"></a>Zobacz także
[Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)