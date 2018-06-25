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
ms.openlocfilehash: a7a61ff71b5ed8caa8ad50dff71957bee20b955a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757995"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Porady: Dodawanie i usuwanie zależności funkcji
  Funkcja programu SharePoint może zależeć od innych funkcji dla funkcji lub danych. W takich przypadkach funkcje te można oznaczyć jako zależności dla funkcji programu. W ten sposób programu SharePoint server gwarantuje, że funkcje zależne zostaną aktywowane aktywowania funkcji programu.  
  
## <a name="add-dependencies"></a>Dodaj zależności  
 Możesz dodać inne funkcje w rozwiązaniu jako zależności. W ten sposób można upewnij się, że wymagane funkcje są zainstalowane i aktywowane przed zainstalowaniem programu funkcji.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Aby dodać zależność od funkcji w rozwiązaniu
  
1.  Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** węzeł, a następnie wybierz pozycję **Dodaj** przycisku.  
  
2.  W **Dodaj zależności aktywacji funkcji** okno dialogowe Wybierz **Dodaj zależność od funkcji w rozwiązaniu** przycisk opcji, wybierz tytuł funkcja, która ma zostać dodany jako zależność, a następnie Wybierz **Dodaj** przycisku.  
  
     Można dodać więcej niż jedną funkcję, wybierając większą liczbę tytułów podczas wybierania **Ctrl** klucza.  
  
## <a name="addi-custom-dependencies"></a>Niestandardowe zależności Addi  
 Funkcje, które są już zainstalowane na serwerze programu SharePoint można dodać jako zależność. W ten sposób sprawdza proces aktywacji programu SharePoint, upewnij się, że wszystkie funkcje zależne zostaną aktywowane przed zainstalowaniem programu funkcji.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Aby dodać zależność przez identyfikator funkcji
  
1.  Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** węzeł, a następnie wybierz pozycję **Dodaj** przycisku.  
  
2.  W **Dodaj zależności aktywacji funkcji** okno dialogowe Wybierz **dodać niestandardowe zależności** przycisk opcji.  
  
3.  W **identyfikator funkcji** tekst Wprowadź identyfikator GUID dla funkcji, które chcesz oznaczyć jako zależność aktywacji, a następnie wybierz **Dodaj** przycisku.  
  
## <a name="edit-custom-dependencies"></a>Edytuj niestandardowe zależności  
 Można edytować niestandardowe zależności, które zostały wcześniej dodane. Jednak funkcje zależne, które są w rozwiązaniu można tylko usunięte, nie można ich edytować.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Aby zmienić zależności funkcji w rozwiązaniu
  
1.  Otwórz projektanta funkcji, a następnie rozwiń **zależności aktywacji funkcji** węzła.  
  
2.  Wybierz nazwę funkcji, który chcesz edytować, a następnie wybierz pozycję **Edytuj** przycisku.  
  
3.  W **edytować zależności aktywacji funkcji niestandardowych** okno dialogowe Zmień tytuł, identyfikator funkcji lub opis, a następnie wybierz **przesyłania** przycisku.  
  
## <a name="remove-dependencies"></a>Usuwanie zależności  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Aby usunąć zależności funkcji w rozwiązaniu
  
1.  W Projektancie funkcji Rozwiń **zależności aktywacji funkcji** węzła, wybierz nazwę funkcji, który chcesz usunąć, a następnie wybierz pozycję **Usuń** przycisku.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Porady: dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Porady: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
