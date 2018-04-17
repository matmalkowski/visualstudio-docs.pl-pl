---
title: Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f10e0c2d3dc7a561b4fff7ad74081e9a26570b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel
  Jeśli użytkownik dopiero rozpoczynasz pracę tworzenie dostosowań na poziomie dokumentu dla programu Microsoft Office Excel za pomocą programu Visual Studio, Oto co należy wiedzieć.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>Opis sposobu poziomie dokumentu dla programu Excel pracy  
 Dostosowanie poziomie dokumentu dla programu Excel opiera się wokół pojedynczego skoroszytu. Aby rozpocząć korzystanie z dostosowań, użytkownik końcowy zostanie otwarty skoroszyt lub tworzy skoroszyt na podstawie szablonu programu Excel. Zdarzenia w skoroszycie, na przykład wpisanie w komórkach lub kliknięcie przycisków i elementów menu, można wywołać metody obsługi zdarzeń w zestawie. Po zamknięciu skoroszytu funkcje oferowane przez dostosowanie nie będą dostępne w programie Excel, tylko w dokumencie, który je zawiera.  
  
 Aby uzyskać więcej informacji, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-excel"></a>Tworzenie projektów na poziomie dokumentu dla programu Excel  
 Aby utworzyć dostosowania poziomie dokumentu dla programu Excel, należy użyć szablonu projektu skoroszyt programu Excel lub szablon programu Excel w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do wymaganych zestawów i pliki projektu.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia projektu poziomie dokumentu dla programu Excel, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>Programowanie skoroszytów programu Excel przy użyciu elementów hosta i formantów hosta  
 *Host elementów* i *hostowania formantów* są klasy zawierających modelu programowania dostosowań na poziome dokumentu utworzone za pomocą programu Visual Studio.  
  
 Obiekty hosta podaj punkt wejścia dla kodu i mogą również działać jako kontenery dla formantów hosta i formantów formularzy systemu Windows. W projektach na poziomie dokumentu dla programu Excel, te elementy hosta są reprezentowane przez `ThisWorkbook`, `Sheet1`, `Sheet2`, i `Sheet3` klasy.  
  
 Formanty hosta są oparte na natywnego obiektami programu Excel, takie jak listy obiektów i zakresów. Formanty hosta zapewniać funkcje podobne do natywnej obiektami programu Excel, ale ma także nowych zdarzeń, wsparcia projektanta i możliwość powiązania danych. Są wyświetlane jako najwyższej jakości obiektów w kodzie projektu i IntelliSense, co ułatwia odwoływać się do określonych obiektów bezpośrednio w kodzie, bez konieczności Przejdź modelu obiektów programu Excel.  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Programowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)  
  
-   [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>Dostosowywanie interfejsu użytkownika programu Excel  
 Większość rozwiązań Microsoft Office zmodyfikować interfejsu użytkownika (UI) aplikacji pakietu Office do niektórych umożliwiają użytkownikom na interakcję z rozwiązaniem. Istnieje wiele sposobów, w których można zmodyfikować interfejsu użytkownika programu Excel za pomocą dostosowania poziomie dokumentu. Na przykład można dodać kontrolki do Wstążki lub można wyświetlić w okienku Akcje. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
 Można również otworzyć skoroszytu, który jest skojarzony z projektu bezpośrednio w programie Visual Studio. Gdy skoroszyt jest otwarty w programie Visual Studio, można zmodyfikować skoroszytu przy użyciu interfejsu użytkownika programu Excel. Skoroszyt można także używać jako powierzchni projektowej, dzięki czemu można przeciągnięcie formantów do arkusza. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w Visual Studio środowiska](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="using-data-binding"></a>Używanie powiązania danych  
 Formanty hosta są również na liście formantów, które można przeciągnąć z **źródeł danych** okna. Dodawanie formantów hosta w ten sposób automatycznie wiąże je do źródła danych, które można skonfigurować za pomocą okna. Bez pisania żadnego kodu, można wyświetlić dane z bazy danych, usługi sieci web i business obiektów. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak utworzyć dostosowania poziomie dokumentu dla programu Excel, zobacz [wskazówki: tworzenie swój pierwszy dokument dostosowania na poziomie dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). W tym przewodniku przedstawiono narzędzi programowania pakietu Office w Visual Studio i model programowania do dostosowań na poziome dokumentu programu Excel.  
  
 Aby uzyskać listę tematów, które umożliwia przeprowadzenie niektórych typowych zadań w projekty programu Excel, zobacz [typowe zadania w programowaniu Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Rozwiązania programu Excel](../vsto/excel-solutions.md)   
 [Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  