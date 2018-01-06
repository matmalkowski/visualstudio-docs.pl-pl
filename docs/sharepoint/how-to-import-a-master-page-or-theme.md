---
title: 'Porady: importowanie tematu lub strony wzorcowej | Dokumentacja firmy Microsoft'
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 447fa8749958a3fa2b65a6ef7eb878b906170e6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-import-a-master-page-or-theme"></a>Porady: importowanie tematu lub strony wzorcowej
  Można nadać stron w witrynie programu SharePoint spójny wygląd przez tworzenie i używanie stron wzorcowych i kompozycji. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]nie udostępnia szablonów dla tych elementów, ale można je utworzyć w programie SharePoint Designer, a następnie zaimportować je do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: stron i interfejs użytkownika](http://go.microsoft.com/fwlink/?LinkID=182095) w witrynie firmy Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Aby zaimportować strony wzorcowej lub motywu  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz lub Otwórz projekt programu SharePoint.  
  
     Aby uzyskać informacje o sposobie tworzenia projektu SharePoint, zobacz [projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
4.  Na liście szablonów programu SharePoint, wybierz **modułu** szablonu, a następnie określ nazwę dla modułu.  
  
     Moduł zawiera pliki (na przykład strony wzorcowej lub pliki motywu) do wdrożenia w określonej lokalizacji w programie SharePoint.  
  
5.  W module usunąć domyślny plik o nazwie przykład.txt.  
  
6.  Wybierz węzeł modułu.  
  
7.  Na pasku menu wybierz **projektu**, **Dodaj istniejący element**, a następnie wybierz plik tematu lub strony głównej.  
  
     Pliki strony wzorcowej mieć rozszerzenie .master i motyw pliki mają rozszerzenie .thmx.  
  
8.  Jeśli dodano strony wzorcowej, zmienić jego **Rozwiązywanie konfliktów wdrożenia** ustawienie **automatyczne** we właściwościach modułu.  
  
    > [!NOTE]  
    >  Mogą wystąpić błędy, jeśli nazwa strony głównej jest taka sama jak nazwa istniejącego strony wzorcowej, który jest oznaczony jako domyślna strona wzorcowa lub niestandardowej strony wzorcowej. Aby uzyskać informacje o sposobie rozwiązania tego problemu, zobacz [wskazówki: Importowanie niestandardowej strony wzorcowej oraz strony witryny z obrazem](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. W module Otwórz Elements.xml.  
  
     Należy zaktualizować plik Elements.xml odwołuje się do strony głównej ani motywu, który został dodany.  
  
10. Dla strony wzorcowej Zastąp istniejące znaczników modułu następujący kod znaczników.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Dla motywu należy zastąpić istniejące znaczników modułu następujący kod znaczników.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Należy zastąpić symbole zastępcze rzeczywistej nazwy modułu i strony wzorcowej lub motywu.  
  
     Atrybut `Type="GhostableInLibrary"` wskazuje, że element został dodany do bazy danych zawartości i `Url` atrybutu modułu określa, gdzie można przechowywać plik w bazie danych zawartości programu SharePoint.  
  
11. Aby zmienić zakres wdrożenia dla strony wzorcowej w **Eksploratora rozwiązań**, otwórz plik funkcji w Projektancie funkcji, a następnie wybierz nowy zakres wdrożenia z **zakres** listy.  
  
     Wartość **Web** oznacza, że strony wzorcowej ma zastosowanie tylko do witryny sieci Web, które jest obecnie określone w projekcie. Wartość **lokacji** oznacza, że strony wzorcowej odnosi się do bieżącej kolekcji lokacji, w tym wszystkie lokacje podrzędne i głównej sieci web. Nie można stosować inne wartości.  
  
    > [!NOTE]  
    >  Motywy zastosować tylko na poziomie zbioru witryn, dlatego zaleca się nie ustawienie zakresu motyw do żadnych innych niż **lokacji**. Mogą wystąpić błędy, jeśli motyw jest używana w lokacji podrzędnej.  
  
12. Na pasku menu wybierz **kompilacji**, **wdrożyć rozwiązanie**.  
  
13. Aby sprawdzić, czy pliki zostały poprawnie wdrożone, otwórz witrynę programu SharePoint, wybierz pozycję **Akcje witryny** menu, wybierz **ustawienia lokacji** polecenia, a następnie wybierz opcję **strony wzorcowej**  łącze lub **motywy** łącza.  
  
     Lista stron wzorcowych i motywów pojawia się i zawiera strony wzorcowej lub motywu, który można zaimportować.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony wzorcowej](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Tworzenie stron dla SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Stosowanie modułów podczas dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  