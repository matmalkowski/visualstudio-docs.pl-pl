---
title: "Porady: przewijanie rekordów bazy danych w arkuszu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 78ccd24a262863a4d6f844d624ef9996d09d568f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Porady: przewijanie rekordów bazy danych w arkuszu
  Poniższa procedura przedstawia sposób wyświetlania jednego pola z tabeli bazy danych w arkuszu programu Microsoft Office Excel z formantami, które umożliwiają użytkownikom końcowym przewijania wszystkich rekordów za pomocą projektanta.  
  
 Projektant służy wyłącznie w projektach na poziomie dokumentu. Można również dodawać formanty i powiązać je programowo z danymi w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [wskazówki: proste powiązanie danych w VSTO dodatku projektu](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Do przewijania rekordów bazy danych w arkuszu  
  
1.  Otwórz projekt aplikacji Excel w Visual Studio.  
  
2.  Otwórz **źródeł danych** okna i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3.  Rozwiń tabeli, która zawiera dane, które chcesz wyświetlić, a następnie wybierz określone kolumny.  
  
4.  Otwórz listę kontrolek i wybierz **NamedRange**.  
  
5.  Przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania na komórkę, w którym ma być wyświetlana data.  
  
6.  Z **formularzy systemu Windows** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.BindingNavigator> kontroli do arkusza i konfigurowanie kontroli, którego chcesz użyć. Aby uzyskać więcej informacji, zobacz [informacje o formancie BindingNavigator &#40; Formularze systemu Windows &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  