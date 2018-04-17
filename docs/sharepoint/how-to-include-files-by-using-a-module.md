---
title: 'Porady: dołączanie plików za pomocą modułu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6af9ef6114a3ac187c50d17f16c39c89b08370dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-files-by-using-a-module"></a>Porady: dołączanie plików za pomocą modułu
  *Moduły* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduły) są kontenerami, które umożliwiają wdrażanie pliki takie jak ASPX strony wzorcowe, pliki tekstowe lub obrazów w programie SharePoint.  
  
 Można wdrożyć pliku do biblioteki dokumentów lub jako zwykłego pliku (na przykład default.aspx) poza bibliotekę dokumentów. Aby dodać plik do biblioteki dokumentów, określ `Type="GhostableInLibrary"` jako atrybut w **pliku** elementu. To ustawienie powoduje, że programu SharePoint, aby utworzyć element listy, aby przejść z pliku, gdy jest ona dodawana do biblioteki. Aby wdrożyć pliku poza bibliotekę dokumentów, albo określić `Type="Ghostable"` lub po prostu Pomiń **typu** atrybutu.  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>Dodanie modułu do rozwiązań SharePoint  
  
#### <a name="to-add-a-module"></a>Aby dodać moduł  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwarcia lub utworzenia projektu programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
3.  Na liście szablonów programu SharePoint, wybierz **modułu** szablonu, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Ten krok tworzy węzeł w projekcie o nazwie Module1.  
  
4.  W obszarze Module1 Usuń plik przykład.txt.  
  
     Przykład.txt znajduje się we wszystkich modułach nowe na przykład celów i nie jest wymagana. (Należy pamiętać, że usunięcie pliku spowoduje również usunięcie jego wpis z pliku Elements.xml modułu).  
  
5.  Pliki do wdrożenia struktura określonego folderu, w programie SharePoint, utworzyć te foldery, w obszarze Module1 w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wybierając węzeł Module1, a następnie na pasku, wybierając menu **projektu**, **nowy Folder**.  
  
6.  Wybierz folder, w której chcesz dodać plik, a następnie na pasku menu wybierz **projektu**, **Dodaj istniejący element**.  
  
7.  Wybierz jeden lub więcej plików, które chcesz wdrożyć w programie SharePoint, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Po dodaniu pliku do projektu objęcia są automatycznie dodawane do pliku Elements.xml modułu. Podczas wdrażania projektu pliki są kopiowane do programu SharePoint server, względem katalogu głównego projektu, które jest określone przez **pliku** elementu **adres Url** atrybutów, takich jak `Url="Module1/New Folder/SomeFile.doc`. Jeśli chcesz zmienić lokalizację wdrożenia dla pliku, albo przenieść do innego folderu w **Eksploratora rozwiązań** lub zmień jego **adres Url** ustawienie.  
  
8.  Wszystkie pliki, które mają być wyświetlane w bibliotece dokumentów, można dołączyć `Type="GhostableInLibrary"` atrybutu w celu ich wejściem w Elements.xml. Na przykład  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Wdrażanie projektu.  
  
     Skopiuj pliki do określonych lokalizacji w programie SharePoint.  
  
## <a name="see-also"></a>Zobacz też  
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  