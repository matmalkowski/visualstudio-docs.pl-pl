---
title: "Strona odwołań, Projektant (Visual Basic) projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a6fb8d57be1101f8faa5826b2459a9a1658009d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="references-page-project-designer-visual-basic"></a>Strona odwołań, Projektant projektu (Visual Basic)
Użyj **odwołania** strony **projektanta projektu** do zarządzania odwołań, odwołania sieci Web i importowane przestrzenie nazw w projekcie. Projekty mogą zawierać odwołania do składników COM usług XML sieci Web, biblioteki klas .NET Framework lub zestawów albo innych bibliotek klas. Aby uzyskać więcej informacji na temat używania odwołania zobacz [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md).  

 Aby uzyskać dostęp do **odwołania** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz pozycję **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **odwołania** kartę.  

## <a name="uielement-list"></a>Lista elementów UI  
 Poniższe opcje pozwalają na zaznacz lub usuń odwołania i importowane przestrzenie nazw w projekcie.  

 **Nieużywanych odwołań**  
 Kliknij ten przycisk, aby uzyskać dostęp do **nieużywanych odwołań** okno dialogowe.  

 **Nieużywanych odwołań** okno dialogowe umożliwia usunięcie odwołań, które są zawarte w projekcie, ale nie faktycznie używana przez kod. Zawiera on Siatka wyświetla **Nazwa odwołania**, **ścieżki**i inne informacje o odwołania do nieużywanych przestrzeni nazw w projekcie. W siatce, wybierz odwołania do przestrzeni nazw, które chcesz usunąć z projektu, a następnie kliknij przycisk **Usuń**.  

 **Ścieżek odwołania**  
 Kliknij ten przycisk, aby uzyskać dostęp do **ścieżek odwołania** okno dialogowe.  

> [!NOTE]
>  Gdy system projektu znajduje się odwołanie do zestawu, system usuwa odwołanie przez wyszukiwanie w następujących lokalizacjach w następującej kolejności:  
>   
>  1.  Folder projektu. Pliki folderu projektu są wyświetlane w **Eksploratora rozwiązań** podczas **Pokaż wszystkie pliki** nie ma zastosowania.  
> 2.  Foldery, które są określone w **ścieżek odwołania** okno dialogowe.  
> 3.  Foldery zawierające pliki w **Dodaj odwołanie** okno dialogowe.  
> 4.  Folderze obj. projektu. (Podczas dodawania do projektu odwołanie COM jeden lub więcej zestawów można dodać do folderu obj projektu.)  

 **Odwołania**  
 Ta lista zawiera wszystkie odwołania do projektu, używane lub nieużywane.  

 **Dodaj**  
 Kliknij ten przycisk, aby dodać odwołanie lub odwołania sieci Web do **odwołania** listy.  

 Wybierz **odwołania** można dodać odwołania do projektu przy użyciu okna dialogowego Dodaj odwołanie.  

 Wybierz **odwołania sieci Web** można dodać odwołania sieci Web do projektu przy użyciu okna dialogowego Dodaj odwołanie sieci Web.  

 **Usuń**  
 Wybierz co najmniej jednego odwołania w **odwołania** listy, a następnie kliknij ten przycisk, aby go usunąć.  

 **Aktualizacja odwołania sieci Web**  
 Wybierz odwołanie sieci Web w **odwołania** listy i kliknij ten przycisk, aby go zaktualizować.  

 **Importowane przestrzenie nazw**  
 Można wpisać własną przestrzeni nazw w tym polu i kliknij przycisk **dodać importu użytkownika** można dodać go do listy przestrzeni nazw.  

 Można utworzyć aliasów dla importowanych przestrzeni nazw. Aby to zrobić, należy wprowadzić w formacie alias i przestrzeń nazw *alias*=*przestrzeni nazw*. Jest to przydatne, jeśli używasz długich nazw, na przykład: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  

 **Dodaj użytkownika importu**  
 Kliknij ten przycisk, aby dodać przestrzeni nazw określonej w **importowane przestrzenie nazw** pole do listy importowanych przestrzeni nazw. Ten przycisk jest aktywny tylko wtedy, gdy w określonej przestrzeni nazw nie jest już na liście.  

 **Liście przestrzeni nazw**  
 Ta lista zawiera wszystkich dostępnych przestrzeni nazw. Zaznaczono pola wyboru obszary nazw dołączane do projektu.  

 **Importowanie użytkowników aktualizacji**  
 Wybierz obszar nazw określonego przez użytkownika na liście przestrzeni nazw, wpisz nazwę, którą chcesz zamienić go w **importowane przestrzenie nazw** , a następnie kliknij ten przycisk, aby zmienić nowej przestrzeni nazw. Przycisk jest aktywny tylko wtedy, gdy wybranego obszaru nazw, który zostanie dodany do listy przy użyciu **dodać importu użytkownika** przycisku. Można dodać:  

-   Klasy lub przestrzeni nazw, takich jak <xref:System.Math?displayProperty=fullName>.  

-   Alias imports, takich jak `VB=Microsoft.VisualBasic`.  

-   Przestrzenie nazw XML, takich jak `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  

## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)   
 [Porady: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [Imports, instrukcja (przestrzeń nazw XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
