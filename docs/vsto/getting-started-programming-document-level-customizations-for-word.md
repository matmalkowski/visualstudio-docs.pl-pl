---
title: Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5bed5c08e15861840a34960d186b408fb86085d
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448857"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
  Jeśli użytkownik dopiero rozpoczynasz pracę tworzenie dostosowań na poziomie dokumentu dla programu Microsoft Office Word za pomocą programu Visual Studio, Oto co należy wiedzieć.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Zrozumienie sposobu poziomie dokumentu dla programu Word pracy  
 Każde dostosowanie programu Word, którą utworzysz opiera się wokół pojedynczego dokumentu. Aby rozpocząć korzystanie z dostosowań, użytkownik końcowy otwiera dokument lub tworzy dokumentu z szablonu programu Word. Zdarzenia w dokumencie, na przykład Przesuń kursor w określonych obszarach lub kliknięcie przycisków i elementów menu, można wywołać metody obsługi zdarzeń w zestawie. Gdy dokument zostanie zamknięty, funkcje oferowane przez dostosowanie nie będą dostępne w programie Word.  
  
 Aby uzyskać więcej informacji, zobacz [architektura dostosowań na poziome dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Tworzenie projektów na poziomie dokumentu dla programu Word  
 Aby utworzyć dostosowania poziomie dokumentu dla programu Word, należy użyć szablonu projektu dokument programu Word lub szablon programu Word w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do wymaganych zestawów i pliki projektu.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia projektu poziomie dokumentu dla programu Word, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office project](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Formanty hosta programu dokumentów programu Word przy użyciu elementów hosta  
 *Host elementów* i *hostowania formantów* klas, które zapewniają modelu programowania dostosowań na poziomie dokumentu.  
  
 Obiekty hosta podaj punkt wejścia dla kodu i mogą również działać jako kontenery dla formantów hosta i formantów formularzy systemu Windows. W projektach na poziomie dokumentu dla programu Word, element hosta jest reprezentowana przez `ThisDocument` klasy.  
  
 Formanty hosta są oparte na natywny obiektów programu Word, takich jak formantów zawartości, zakładek i XML węzłów. Formanty hosta zapewniać funkcje podobne do natywnej obiektów programu Word, ale ma także nowych zdarzeń, wsparcia projektanta i możliwości wiązania danych. Są wyświetlane jako najwyższej jakości obiektów w kodzie projektu i IntelliSense, co ułatwia odwoływać się do określonych obiektów bezpośrednio w kodzie, bez konieczności Przejdź modelu obiektów programu Word.  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)  
  
-   [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Dostosowywanie interfejsu użytkownika programu Word  
 Większość rozwiązań Microsoft Office zmodyfikować interfejsu użytkownika (UI) aplikacji pakietu Office do niektórych umożliwiają użytkownikom na interakcję z rozwiązaniem. Istnieje wiele sposobów, w których można zmodyfikować interfejsu użytkownika programu Word za pomocą dostosowania poziomie dokumentu. Na przykład można dodać kontrolki do Wstążki i można wyświetlić w okienku Akcje. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
 Można również otworzyć dokument, który jest skojarzony z projektu bezpośrednio w programie Visual Studio. Gdy dokument jest otwarty w programie Visual Studio, można zmodyfikować dokumentu za pomocą interfejsu użytkownika programu Word. Można także używać go jako powierzchni projektu, co pozwala na przeciągnij formanty. Aby uzyskać więcej informacji, zobacz [projektów pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Powiązanie kontrolek z danymi  
 Formanty zawartości i <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli znajdują się na liście formantów, które można przeciągnąć z **źródeł danych** okna. Dodawanie zawartości kontrolki i sposób automatycznie zakładki w tym wiąże je do źródła danych, które można skonfigurować przy użyciu okna. Bez pisania żadnego kodu, można wyświetlić dane z bazy danych, usług i obiektów biznesowych. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak utworzyć dostosowania poziomie dokumentu dla programu Word, zobacz [wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). W tym przewodniku przedstawiono narzędzi programowania pakietu Office w Visual Studio i model programowania do dostosowań na poziome dokumentu programu Word.  
  
 Aby uzyskać listę tematów, które umożliwia przeprowadzenie niektórych typowych zadań w projekty programu Word, zobacz [typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  