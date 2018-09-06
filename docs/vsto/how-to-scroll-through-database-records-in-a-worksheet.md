---
title: 'Porady: przewijanie rekordów bazy danych w arkuszu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e9ffaffdefda98e3e074467fcd4df8cacce91b4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677280"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Porady: przewijanie rekordów bazy danych w arkuszu
  Poniższa procedura pokazuje, jak używać projektanta do wyświetlania jedno pole z tabeli bazy danych w arkuszu programu Microsoft Office Excel, za pomocą formantów, które umożliwiają użytkownikowi końcowemu przewiń wszystkie rekordy.  
  
 Tylko w projektach na poziomie dokumentu można używać projektanta. Można również dodawać formanty i powiązać je z danymi programowo w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [wskazówki: proste powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Do przewijania rekordów bazy danych w arkuszu  
  
1.  Otwórz projekt aplikacji programu Excel w programie Visual Studio.  
  
2.  Otwórz **źródeł danych** okna i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3.  Rozwiń tabelę, która zawiera dane, które mają być wyświetlane, a następnie wybierz określone kolumny.  
  
4.  Otwórz listę kontrolek, a następnie wybierz pozycję **NamedRange**.  
  
5.  Przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli na komórkę, w którym ma się pojawić się dane.  
  
6.  Z **Windows Forms** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.BindingNavigator> sterowania do arkusza i konfigurowanie kontrolek, w której chcesz użyć. Aby uzyskać więcej informacji, zobacz [— informacje o formancie BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  