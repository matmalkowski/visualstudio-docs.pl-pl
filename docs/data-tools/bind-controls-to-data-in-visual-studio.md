---
title: Powiązywanie formantów z danymi w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ce37768ce7a7685b89b82a04b944b7fa38af630c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Powiązywanie formantów z danymi w Visual Studio
Aby wyświetlić dane użytkownikom aplikacji, wiązanie danych do kontrolek. Tych kontrolek powiązanych z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na powierzchni projektu lub kontrolki na powierzchni w programie Visual Studio.  
  
 W tym temacie opisano źródeł danych, które służy do tworzenia formantów powiązanych z danymi. Omówiono także niektóre ogólne zadania w powiązaniu danych. Aby uzyskać szczegółowe informacje o sposobie tworzenia formantów powiązanych z danymi, zobacz [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) i [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
## <a name="data-sources"></a>Źródła danych  
 W kontekście wiązania danych źródła danych reprezentuje dane w pamięci, która może być powiązana z interfejsu użytkownika. W praktyce źródła danych może być klasą Entity Framework, zestawu danych, punkt końcowy usługi hermetyzowaną w obiekcie proxy .NET, LINQ do SQL klasy, lub dowolnych obiektów .NET lub kolekcji. Niektóre źródła danych umożliwiają tworzenie formantów powiązanych z danymi, przeciągając elementy z **źródeł danych** okna, gdy nie chcesz innych źródeł danych. W poniższej tabeli przedstawiono źródła danych, które są obsługiwane.  
  
|Źródło danych|Obsługa przeciągania i upuszczania w **Projektant formularzy systemu Windows**|Obsługa przeciągania i upuszczania w **projektanta WPF**|Obsługa przeciągania i upuszczania w **projektanta Silverlight**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|Zestaw danych|Tak|Tak|Nie|  
|Entity Data Model|Tak<sup>1</sup>|Tak|Tak|  
|Klasy LINQ do SQL|Nie<sup>2</sup>|Nie<sup>2</sup>|Nie<sup>2</sup>|  
|Usługi (łącznie z [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF usługi i usługi sieci web)|Tak|Tak|Tak|  
|Obiekt|Tak|Tak|Tak|  
|Program SharePoint|Tak|Tak|Tak|  
  
 1. Generowanie model przy użyciu **modelu Entity Data Model** kreatora, przeciągnij tych obiektów do projektanta.  
  
 2. Klasy LINQ do SQL nie są wyświetlane w **źródeł danych** okna. Można jednak dodać nowego źródła danych obiektu, który jest oparty na LINQ w klasach SQL, a następnie przeciągnij tych obiektów do projektanta, aby utworzyć formantów powiązanych z danymi. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie klasy LINQ do SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="data-sources-window"></a>Data Sources — Okno  
 Źródła danych są dostępne do projektu jako elementy w **źródeł danych** okna. To okno jest widoczne, lub jest dostępny z **widoku** menu powierzchni projektowej formularza jest aktywnym oknem w projekcie. Można przeciągnąć elementy z tego okna, aby utworzyć formantów, które są powiązane z danych podstawowych i źródeł danych można również skonfigurować, klikając prawym przyciskiem myszy.  
  
 ![Okno źródła danych](../data-tools/media/raddata-data-sources-window.png "raddata okna źródeł danych")  
  
 Dla każdego typu danych, która jest wyświetlana w **źródeł danych** okno formantu domyślny jest tworzony podczas przeciągnij element do projektanta. Aby przeciągnąć element z **źródeł danych** okna, można zmienić formant, który zostanie utworzony. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Zadania związane z powiązywanie kontrolek z danymi  
 W poniższej tabeli wymieniono niektóre z najbardziej typowych zadań, należy wykonać w celu powiązanie kontrolek z danymi.  
  
|Zadanie|Więcej informacji|  
|----------|----------------------|  
|Otwórz **źródeł danych** okna.|Otwórz powierzchni projektu w edytorze i wybierz polecenie **widoku** > **źródeł danych**.|  
|Dodawanie źródła danych do projektu.|[Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)|  
|Ustawianie formantu, który jest tworzony podczas przeciągnąć element z **źródeł danych** okna do projektanta.|[Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Zmodyfikuj listę i kontrolek, które są skojarzone z elementów w **źródeł danych** okna.|[Dodawanie kontrolek niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Tworzenie formantów powiązanych z danymi.|[Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Powiązanie formantów WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|  
|Powiązanie z obiektem lub kolekcji.|[Powiązanie obiektów w programie Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtrowanie danych, która jest wyświetlana w Interfejsie użytkownika.|[Filtrowanie i sortowanie danych w aplikacji Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Dostosowywanie podpisów dla formantów.|[Dostosowywanie sposobu tworzenia podpisów dla kontrolek powiązanych z danymi przez program Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio tools danych dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Wiązanie danych formularzy Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)