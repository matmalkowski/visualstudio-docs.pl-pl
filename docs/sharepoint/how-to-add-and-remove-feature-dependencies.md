---
title: 'Porady: Dodawanie i usuwanie zależności funkcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eeda1b63132de49785b2f2ba5743dbd683504a71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Porady: dodawanie i usuwanie zależności funkcji
  Funkcja programu SharePoint może zależeć od innych funkcji dla funkcji lub danych. W takich przypadkach funkcje te można oznaczyć jako zależności dla funkcji programu. W ten sposób programu SharePoint server gwarantuje, że funkcje zależne zostaną aktywowane aktywowania funkcji programu.  
  
## <a name="adding-dependencies"></a>Dodawanie zależności  
 Możesz dodać inne funkcje w rozwiązaniu jako zależności. W ten sposób można upewnij się, że wymagane funkcje są zainstalowane i aktywowane przed zainstalowaniem programu funkcji.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Aby dodać zależność od funkcji w rozwiązaniu  
  
1.  Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** węzeł, a następnie wybierz pozycję **Dodaj** przycisku.  
  
2.  W **Dodaj zależności aktywacji funkcji** okno dialogowe Wybierz **Dodaj zależność od funkcji w rozwiązaniu** przycisk opcji, wybierz tytuł funkcja, która ma zostać dodany jako zależność, a następnie Wybierz **Dodaj** przycisku.  
  
     Możesz dodać więcej niż jedną funkcję, wybierając większą liczbę tytułów podczas wybierania klawisz Ctrl.  
  
## <a name="adding-custom-dependencies"></a>Dodawanie niestandardowych zależności  
 Funkcje, które są już zainstalowane na serwerze programu SharePoint można dodać jako zależność. W ten sposób sprawdza proces aktywacji programu SharePoint, upewnij się, że wszystkie funkcje zależne zostaną aktywowane przed zainstalowaniem programu funkcji.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Aby dodać zależność przez identyfikator funkcji  
  
1.  Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** węzeł, a następnie wybierz pozycję **Dodaj** przycisku.  
  
2.  W **Dodaj zależności aktywacji funkcji** okno dialogowe Wybierz **dodać niestandardowe zależności** przycisk opcji.  
  
3.  W **identyfikator funkcji** tekst Wprowadź identyfikator GUID dla funkcji, które chcesz oznaczyć jako zależność aktywacji, a następnie wybierz **Dodaj** przycisku.  
  
## <a name="editing-custom-dependencies"></a>Edytowanie niestandardowego zależności  
 Można edytować niestandardowe zależności, które zostały wcześniej dodane. Jednak funkcje zależne, które są w rozwiązaniu można tylko usunięte, nie można ich edytować.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Aby zmienić zależności funkcji w rozwiązaniu  
  
1.  Otwórz projektanta funkcji, a następnie rozwiń **zależności aktywacji funkcji** węzła.  
  
2.  Wybierz nazwę funkcji, który chcesz edytować, a następnie wybierz pozycję **Edytuj** przycisku.  
  
3.  W **edytować zależności aktywacji funkcji niestandardowych** okno dialogowe Zmień tytuł, identyfikator funkcji lub opis, a następnie wybierz **przesyłania** przycisku.  
  
## <a name="removing-dependencies"></a>Usuwanie zależności  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Aby usunąć zależności funkcji w rozwiązaniu  
  
1.  W Projektancie funkcji Rozwiń **zależności aktywacji funkcji** węzła, wybierz nazwę funkcji, który chcesz usunąć, a następnie wybierz pozycję **Usuń** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  