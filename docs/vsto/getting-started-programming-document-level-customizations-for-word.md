---
title: Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 850579b91b9905b3de6298f0e44b84201ac31692
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-programming-document-level-customizations-for-word"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
  Jeśli użytkownik dopiero rozpoczynasz pracę tworzenie dostosowań na poziomie dokumentu dla programu Microsoft Office Word za pomocą programu Visual Studio, Oto co należy wiedzieć.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-word-work"></a>Opis sposobu poziomie dokumentu dla programu Word pracy  
 Każde dostosowanie programu Word, którą utworzysz opiera się wokół pojedynczego dokumentu. Aby rozpocząć korzystanie z dostosowań, użytkownik końcowy otwiera dokument lub tworzy dokumentu z szablonu programu Word. Zdarzenia w dokumencie, na przykład Przesuń kursor w określonych obszarach lub kliknięcie przycisków i elementów menu, można wywołać metody obsługi zdarzeń w zestawie. Gdy dokument zostanie zamknięty, funkcje oferowane przez dostosowanie nie będą dostępne w programie Word.  
  
 Aby uzyskać więcej informacji, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-word"></a>Tworzenie projektów na poziomie dokumentu dla programu Word  
 Aby utworzyć dostosowania poziomie dokumentu dla programu Word, należy użyć szablonu projektu dokument programu Word lub szablon programu Word w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do wymaganych zestawów i pliki projektu.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia projektu poziomie dokumentu dla programu Word, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-word-documents-by-using-host-items-host-controls"></a>Programowanie dokumentów programu Word za pomocą formantów hosta elementy hosta  
 *Host elementów* i *hostowania formantów* klas, które zapewniają modelu programowania dostosowań na poziomie dokumentu.  
  
 Obiekty hosta podaj punkt wejścia dla kodu i mogą również działać jako kontenery dla formantów hosta i formantów formularzy systemu Windows. W projektach na poziomie dokumentu dla programu Word, element hosta jest reprezentowana przez `ThisDocument` klasy.  
  
 Formanty hosta są oparte na natywny obiektów programu Word, takich jak formantów zawartości, zakładek i XML węzłów. Formanty hosta zapewniać funkcje podobne do natywnej obiektów programu Word, ale ma także nowych zdarzeń, wsparcia projektanta i możliwości wiązania danych. Są wyświetlane jako najwyższej jakości obiektów w kodzie projektu i IntelliSense, co ułatwia odwoływać się do określonych obiektów bezpośrednio w kodzie, bez konieczności Przejdź modelu obiektów programu Word.  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Programowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)  
  
-   [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-word"></a>Dostosowywanie interfejsu użytkownika programu Word  
 Większość rozwiązań Microsoft Office zmodyfikować interfejsu użytkownika (UI) aplikacji pakietu Office do niektórych umożliwiają użytkownikom na interakcję z rozwiązaniem. Istnieje wiele sposobów, w których można zmodyfikować interfejsu użytkownika programu Word za pomocą dostosowania poziomie dokumentu. Na przykład można dodać kontrolki do Wstążki i można wyświetlić w okienku Akcje. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
 Można również otworzyć dokument, który jest skojarzony z projektu bezpośrednio w programie Visual Studio. Gdy dokument jest otwarty w programie Visual Studio, można zmodyfikować dokumentu za pomocą interfejsu użytkownika programu Word. Można także używać go jako powierzchni projektu, co pozwala na przeciągnij formanty. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w Visual Studio środowiska](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="binding-controls-to-data"></a>Powiązywanie kontrolek z danymi  
 Formanty zawartości i <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli znajdują się na liście formantów, które można przeciągnąć z **źródeł danych** okna. Dodawanie zawartości kontrolki i sposób automatycznie zakładki w tym wiąże je do źródła danych, które można skonfigurować przy użyciu okna. Bez pisania żadnego kodu, można wyświetlić dane z bazy danych, usług i obiektów biznesowych. Aby uzyskać więcej informacji, zobacz [wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak utworzyć dostosowania poziomie dokumentu dla programu Word, zobacz [wskazówki: tworzenie swój pierwszy poziomie dokumentu dostosowania dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). W tym przewodniku przedstawiono narzędzi programowania pakietu Office w Visual Studio i model programowania do dostosowań na poziome dokumentu programu Word.  
  
 Aby uzyskać listę tematów, które umożliwia przeprowadzenie niektórych typowych zadań w projekty programu Word, zobacz [typowe zadania w programowaniu Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  