---
title: "Powiązywanie formantów z obrazami z bazy danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 77d2780200fd8be7a42d396cdade39b271b04bae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Powiązywanie formantów z obrazami z bazy danych
Można użyć **źródeł danych** okna do powiązania obraz w bazie danych z formantem w aplikacji. Na przykład można powiązać obraz <xref:System.Windows.Controls.Image> kontroli w aplikacji WPF lub do <xref:System.Windows.Forms.PictureBox> formantu w aplikacji formularzy systemu Windows.  
  
Obrazy w bazie danych są zwykle przechowywane jako tablice typu byte. Elementy w **źródeł danych** okna, które są przechowywane jako tablice typu byte mieć kontrolę wpisz wartość **Brak** domyślnie, ponieważ tablice typu byte mogą zawierać nic proste tablicę bajtów do pliku wykonywalnego dużych aplikacji. Można utworzyć formantu powiązanego z danymi elementu tablicy bajtów w **źródeł danych** okna, który reprezentuje obraz, należy wybrać formant do utworzenia.  
  
W poniższej procedurze przyjęto, że **źródeł danych** okno jest już wypełniony elementu, który jest powiązany z obrazu. 
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Aby powiązać obrazu w bazie danych do formantu  
  
1.  Upewnij się, że chcesz dodać kontrolki do powierzchni projektu jest otwarty w Projektancie WPF lub Projektant formularzy systemu Windows.  
  
2.  W **źródeł danych** okna, rozwiń odpowiednią tabelę lub obiekt, aby wyświetlić właściwości lub kolumny.  
  
3.  Wybierz kolumny lub właściwości zawierającego dane obrazu, a z listy kontrolka listy rozwijanej wybierz jedną z poniższych formantów:  
  
    -   Projektant WPF jest otwarty, wybierz opcję **obrazu**.  
  
    -   Jeśli projektant formularzy systemu Windows jest otwarty, wybierz **PictureBox**.  
  
    -   Alternatywnie można wybrać inny formant, który obsługuje powiązanie danych i które można wyświetlić obrazy. Jeśli formant, który ma być używany, nie jest na liście dostępnych formantów, należy dodać go do listy, a następnie zaznacz go. Aby uzyskać więcej informacji, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Zobacz także
[Powiązanie formantów WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)