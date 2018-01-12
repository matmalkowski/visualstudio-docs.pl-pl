---
title: "Porady: Dodawanie i usuwanie folderów mapowanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 29809344ee8a3f446589ba84f2fc47b1cf407582
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Porady: dodawanie i usuwanie folderów mapowanych
  Niektóre często używane foldery w programie SharePoint, takie jak obrazy i układy, głęboko osadzone w hierarchii plików. Możesz mapować te foldery do projektu SharePoint łatwiej je otworzyć. Zmapowane katalogi są foldery w projekcie programu SharePoint, które odpowiadają fizyczną lokalizację plików w instalacji programu SharePoint Server.  
  
 Podczas wdrażania aplikacji programu SharePoint, zawartość zamapowany folder i wszystkie jego podfoldery zostaną skopiowane przez pakietu rozwiązania (wsp) na serwerze z systemem programu SharePoint w określonej lokalizacji w drzewie folderów programu SharePoint. Ta lokalizacja jest określana przez **lokalizacja wdrożenia** właściwości ustawionej dla zamapowany folder. Wszystkie podfoldery w folderze zamapowanych są względem **lokalizacja wdrożenia** zamapowanych folderu. Należy pamiętać, że **lokalizacja wdrożenia** Określa właściwość, a nie nazwę zamapowany folder wdrożonym elementów.  
  
 Katalogi zmapowane można dodać do projektu przy użyciu polecenia na pasku menu lub menu skrótów dla projektu. Można użyć **dodać Folder programu SharePoint "Obrazy" mapowane** i **dodawania programu SharePoint "Układów" folder** polecenia, aby dodać te mapowane foldery, które są używane najczęściej. Możesz mapować jakiekolwiek inne dostępne foldery programu SharePoint do projektu przy użyciu **Dodaj SharePoint zamapowany Folder** polecenia menu skrótów, a następnie określając folderów w **Dodaj SharePoint zamapowany Folder** okno dialogowe.  
  
## <a name="adding-mapped-folders-to-a-project"></a>Dodawanie folderów mapowanych do projektu  
 Poniższa procedura zawiera opis sposobu dodawania dwa katalogi zmapowane do projektu programu visual web part. Aby rozpocząć, tworzenia projektu programu visual web part.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Aby dodać katalogi zmapowane do projektu  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń albo **Visual Basic** lub **Visual C#** węzła, rozwiń węzeł **Office i SharePoint** węzeł, a następnie Wybierz **rozwiązań SharePoint** węzła.  
  
3.  Na liście szablony projektów, wybierz **składnika Web Part programu SharePoint 2013 Visual** szablonu.  
  
4.  W **nazwa** wprowadź **TestProject1**, a następnie wybierz pozycję **OK** przycisku.  
  
5.  W **Kreator dostosowania programu SharePoint**, wybierz **Zakończ** przycisk, aby zachować ustawienia domyślne.  
  
6.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu**, **dodać Folder programu SharePoint "Obrazy" mapowane**.  
  
     Folder o nazwie **obrazów** pojawia się w projekcie i zawiera podfolder o nazwie TestProject1. Ten zamapowany folder będzie zawierać obrazy dla projektu programu visual web part.  
  
7.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu**, **Dodaj SharePoint zamapowany Folder** do wyświetlenia **Dodaj SharePoint zamapowany Folder** okno dialogowe.  
  
8.  W widoku drzewa folderów, które są dostępne dla mapowania, wybierz **zasobów** folder, a następnie wybierz pozycję **OK** przycisku.  
  
     Folder o nazwie **zasobów** pojawia się w projekcie. Ten folder może przechowywać elementów, takich jak pliki zasobów ciągu. Podfoldery mogą być przydatne do organizowania zawartość zamapowany folder, ale są tworzone automatycznie podczas dodawania zamapowany folder przy użyciu **Dodaj SharePoint zamapowany Folder** polecenia. Aby dodać podfolder, wybierz **zasobów** folder, a następnie na pasku menu wybierz **projektu**, **nowy Folder**.  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>Zmienianie lokalizacji wdrożenia zamapowany Folder  
 Domyślnie zmapowane katalogi są dodawane do określonych lokalizacji względem ścieżki instalacji programu SharePoint głównego, który wskazuje token {SharePointRoot}. Można jednak zmienić tę lokalizację, zmieniając **lokalizacja wdrożenia** właściwości zamapowany folder. Każdy zamapowany folder ma własną **lokalizacja wdrożenia** właściwości.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Aby zmienić lokalizację wdrożenia zamapowany folder  
  
1.  W projekcie, który został utworzony wcześniej wybierz zamapowany folder.  
  
2.  W **właściwości** okna, wybierz wielokropek (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")) znajdującego się na **wdrożenia Lokalizacja** właściwości.  
  
3.  W **Dodaj SharePoint zamapowany Folder** okno dialogowe, przejdź do folderu, do którego ma zostać zamapowany folder do punktu.  
  
4.  Wybierz węzeł, a następnie wybierz **OK** przycisku.  
  
## <a name="renaming-or-removing-mapped-folders"></a>Zmiana nazwy lub usuwanie folderów mapowanych  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Aby zmienić lub usunąć zamapowany folder  
  
1.  W projekcie, który został utworzony wcześniej wybierz zamapowany folder.  
  
2.  Aby zmienić nazwę folderu mapowane, otwórz menu skrótów, wybierz pozycję **zmienić**, wprowadź nową nazwę, a następnie wybierz klawisz Enter.  
  
     Alternatywnie, można wybrać zamapowany folder, który chcesz zmienić, otwórz **właściwości** okna, a następnie ustaw wartość **nazwa folderu** właściwości na nową nazwę.  
  
3.  Aby usunąć zamapowany folder z projektu, otwórz menu skrótów, wybierz pozycję **usunąć**, a następnie wybierz pozycję **OK** przycisk w oknie dialogowym, aby potwierdzić usunięcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  