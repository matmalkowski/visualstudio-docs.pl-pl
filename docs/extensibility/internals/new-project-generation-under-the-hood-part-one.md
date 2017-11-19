---
title: "Generowanie nowego projektu: Kulisy, część jednego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efe08d9e23f1a77fd68df2bdba4389e7b7955b11
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generowanie nowego projektu: Kulisy, należy do jednego
Kiedykolwiek traktować o sposobie tworzenia własnego typu projektu? Zastanawiasz się, co faktycznie się dzieje podczas tworzenia nowego projektu? Teraz pobrać peek pod maską i zobacz, co naprawdę dzieje.  
  
 Istnieje kilka zadań, które współrzędne Visual Studio:  
  
-   Wyświetla drzewo wszystkie typy dostępnych projektów.  
  
-   Wyświetla listę szablonów aplikacji dla każdego typu projektu, a pozwala wybrać jeden.  
  
-   Zbiera informacje o projekcie dla aplikacji, takie jak nazwa projektu i ścieżkę.  
  
-   Przekazuje informację do fabrykę projektów.  
  
-   Generuje on elementy projektu i foldery w bieżącym rozwiązaniu.  
  
## <a name="the-new-project-dialog-box"></a>Okno dialogowe Nowy projekt  
 Wszystko to rozpoczyna się po wybraniu typu projektu dla nowego projektu. Zacznijmy od kliknięcie **nowy projekt** na **pliku** menu. **Nowy projekt** zostanie wyświetlone okno dialogowe, wyglądającej coś w następujący sposób:  
  
 ![Okno dialogowe Nowy projekt](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Spójrzmy bliżej. **Typy projektów** drzewa zawiera różne typy projektu można utworzyć. Po wybraniu typu projektu, takie jak **Visual C# Windows**, zostanie wyświetlona lista aplikacji szablony ułatwiające rozpoczęcie pracy. **Zainstalowane szablony Visual Studio** są instalowane przez program Visual Studio i są dostępne dla każdego użytkownika na komputerze. Nowe szablony utworzonych lub zebrać mogą być dodawane do **Moje szablony** i są dostępne tylko dla Ciebie.  
  
 Po wybraniu szablonu, takie jak **aplikacji systemu Windows**, opis typem aplikacji jest wyświetlany w oknie dialogowym; w takim przypadku **projekt do tworzenia aplikacji z interfejsem użytkownika systemu Windows**.  
  
 W dolnej części **nowy projekt** okno dialogowe, zobaczysz kilka formantów, które dodatkowych informacji. Formanty widoczne są zależne od typu projektu, ale zazwyczaj obejmują one projektu **nazwa** pole tekstowe **lokalizacji** pole tekstowe i pokrewnych **Przeglądaj** przycisk i **Nazwa rozwiązania** pole tekstowe i pokrewnych **Utwórz katalog rozwiązania** pole wyboru.  
  
## <a name="populating-the-new-project-dialog-box"></a>Okno dialogowe Nowy projekt wypełnianie  
 Gdzie jest **nowy projekt** okno dialogowe uzyskać informacji o jego? Istnieją dwa mechanizmy, w tym miejscu pracy, jeden z nich jest przestarzały. **Nowy projekt** okno dialogowe łączy i wyświetla informacje uzyskane z obu mechanizmów.  
  
 Starsze metody (przestarzałe) używa wpisy rejestru systemowego i .vsdir plików. Ten mechanizm jest uruchamiany po otwarciu programu Visual Studio. Nowsze — metoda korzysta z plików .vstemplate. Ten mechanizm uruchamia się po zainicjowaniu programu Visual Studio, na przykład uruchamiając  
  
```  
devenv /setup  
```  
  
 lub  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Typy projektów  
 Pozycja i nazwy **typy projektów** główny węzłów, takich jak **Visual C#** i **inne języki**, jest określany przez wpisy rejestru systemowego. Organizacja węzły podrzędne, takich jak **bazy danych** i **urządzeń inteligentnych**, odzwierciedla hierarchię folderów zawierających odpowiednie pliki .vstemplate. Przyjrzyjmy się węzły główne najpierw.  
  
#### <a name="project-type-root-nodes"></a>Węzły główne typ projektu  
 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest zainicjowany, przechodzi przez podkluczy klucza rejestru systemu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs do tworzenia i nazwy węzłów głównych **typyprojektów** drzewa. Te informacje są buforowane w celu późniejszego użycia. Przyjrzyj się TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 klucza. Każdy wpis jest identyfikatorem GUID pakiet VSPackage. Nazwa podklucza (/ 1) jest ignorowana, ale jego obecność wskazuje, że jest **typy projektów** węzła głównego. Węzeł główny z kolei może mieć kilka podkluczy kontrolujące wygląd w **typy projektów** drzewa. Oto niektóre z nich.  
  
##### <a name="default"></a>(Domyślnie)  
 To jest identyfikator zasobu zlokalizowanego ciągu nazwy węzła głównego. Zasób ciągu znajduje się w satelitarnej biblioteki DLL przez identyfikator GUID pakietu VSPackage.  
  
 W tym przykładzie jest identyfikatorem GUID pakiet VSPackage  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 i identyfikator zasobu (wartość domyślna) węzła głównego. (/ 1) jest #2345  
  
 Jeśli wyszukiwanie identyfikator GUID w pobliżu klucza pakietów i sprawdzić podklucz SatelliteDll, można znaleźć ścieżki zestawu, który zawiera zasób ciągu:  
  
 \<Ścieżka instalacji usługi Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Aby to sprawdzić, Otwórz okno Eksploratora plików, a następnie przeciągnij csprojui.dll do katalogu w Visual Studio. Tabela ciągów pokazuje, że zasób #2345 ma podpis **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Określa położenie węzła głównego w **typy projektów** drzewa.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Im mniejsza liczba priorytet, tym wyższy pozycji w drzewie.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Jeśli ten podklucz jest obecny, pozycja węzła głównego jest kontrolowana przez okno dialogowe ustawień dewelopera. Na przykład  
  
 REG_SZ DeveloperActivity VC #  
  
 Wskazuje, że Visual C# będzie węzła głównego Jeśli ustawiona jest Visual Studio [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] programowanie. W przeciwnym razie będzie elementem podrzędnym **inne języki**.  
  
##### <a name="folder"></a>Folder  
 Jeśli występuje ten podklucz węzła głównego stanie się elementem podrzędnym określonego folderu. Zostanie wyświetlona lista możliwych folderów w kluczu  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Na przykład wpis projektów bazy danych ma klucz folderu, który odpowiada wpisowi PseudoFolders inne typy projektów. Tak, to w **typy projektów** drzewa, **projektów bazy danych** jest elementem podrzędnym **inne typy projektów**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Węzły podrzędne typu projektu i plików .vstdir  
 Pozycja węzłów podrzędnych w **typy projektów** hierarchię folderów w folderach ProjectTemplates następuje drzewa. Dla szablonów maszyny (**zainstalowane szablony Visual Studio**), Typowa lokalizacja to \Program Files\Microsoft 14.0\Common7\IDE\ProjectTemplates\ programu Visual Studio i szablony użytkownika (**szablonów**), Typowa lokalizacja to \My Studio 14.0\Templates\ProjectTemplates\\. Hierarchie folderów z tych dwóch lokalizacjach zostały scalone do utworzenia **typy projektów** drzewa.  
  
 Dla programu Visual Studio z C# ustawień dewelopera **typy projektów** drzewa wygląda następująco:  
  
 ![Typy projektów](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Odpowiedniego folderu ProjectTemplates wygląda następująco:  
  
 ![Szablony projektu](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Gdy **nowy projekt** zostanie otwarte okno dialogowe, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przechodzi przez folderu ProjectTemplates i odtwarza jego struktury w **typy projektów** drzewa z pewne zmiany:  
  
-   Węzeł główny **typy projektów** drzewa jest określany przez szablon aplikacji.  
  
-   Nazwa węzła może być lokalizowany i może zawierać znaków specjalnych.  
  
-   Można zmienić kolejności sortowania.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Znajdowanie węzła głównego dla typu projektu  
 Gdy program Visual Studio jest przesyłany folderów ProjectTemplates, otwiera wszystkie pliki z rozszerzeniem .zip i wyodrębnia pliki .vstemplate. Plik .vstemplate jest używany plik XML opisujący szablonem aplikacji. Aby uzyskać więcej informacji, zobacz [nowej generacji projektu: pod maską, dwie części](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 \<ProjectType > tag Określa typ projektu dla aplikacji. Na przykład plik \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip zawiera plik EmptyProject.vstemplate, który zawiera ten tag:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > tag, a nie podfolderu w folderze ProjectTemplates określa węzła katalogu głównego aplikacji w **typy projektów** drzewa. W przykładzie aplikacji systemu Windows CE pojawiały się w obszarze **Visual C#** węzła głównego, a nawet wtedy, gdy zostały można przenieść folderu WindowsCE do folderu języka Visual Basic, aplikacje systemu Windows CE nadal będzie znajdować się pod  **Visual C#** węzła głównego.  
  
##### <a name="localizing-the-node-name"></a>Lokalizowanie nazwa węzła  
 Gdy program Visual Studio jest przesyłany folderów ProjectTemplates, sprawdza wszelkie znalezione pliki .vstdir. Plik .vstdir jest plik XML, który określa wygląd typ projektu w **nowy projekt** okno dialogowe. W pliku .vstdir \<LocalizedName > tag do nazwy **typy projektów** węzła.  
  
 Na przykład plik \CSharp\Database\TemplateIndex.vstdir zawiera ten tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Określa satelitarnej biblioteki DLL i zasobów identyfikator zlokalizowanego ciągu nazwy węzła głównego, w tym przypadku **bazy danych**. Zlokalizowana nazwa może zawierać znaków specjalnych, które nie są dostępne dla nazwy folderów, takie jak **.NET**.  
  
 Jeśli nie \<LocalizedName > tag, nosi nazwę typu projektu przez sam folder, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Znajdowanie porządek sortowania dla typu projektu  
 Aby określić kolejność sortowania typ projektu, użyj plików .vstdir \<SortOrder > tagu.  
  
 Na przykład plik \CSharp\Windows\Windows.vstdir zawiera ten tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Plik \CSharp\Database\TemplateIndex.vstdir ma tag z wyższej wartości:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Im niższa liczba w \<SortOrder > tag, tym wyższy pozycji w drzewie tak **systemu Windows** węzeł jest wyświetlany wyższa niż **bazy danych** w węźle **typy projektów**  drzewa.  
  
 Jeśli nie \<SortOrder > tag jest określona dla typu projektu wygląda w porządku alfabetycznym następujące typy żadnych projektu, które zawierają \<SortOrder > specyfikacji.  
  
 Należy pamiętać, że nie ma żadnych plików .vstdir w folderze Moje dokumenty (**Moje szablony**) folderów. Nazwy typów projektu aplikacji użytkownika nie są zlokalizowane i są wyświetlane w kolejności alfabetycznej.  
  
#### <a name="a-quick-review"></a>Szybki przegląd  
 Zmodyfikujmy **nowy projekt** okno dialogowe i utworzyć nowy szablon projektu użytkownika.  
  
1.  Dodaj podfolder Obiekt MyProjectNode do folderu 14.0\Common7\IDE\ProjectTemplates\CSharp \Program Files\Microsoft programu Visual Studio.  
  
2.  Utwórz plik MyProject.vstdir w folderze Obiekt MyProjectNode za pomocą dowolnego edytora tekstu.  
  
3.  Dodaj następujące wiersze do pliku .vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Zapisz i zamknij plik .vstdir.  
  
5.  Utwórz plik MyProject.vstemplate w folderze Obiekt MyProjectNode za pomocą dowolnego edytora tekstu.  
  
6.  Dodaj następujące wiersze w pliku .vstemplate:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Zapisz plik the.vstemplate i zamknij Edytor.  
  
8.  Wyślij plik .vstemplate do nowego skompresowanego folderu MyProjectNode\MyProject.zip.  
  
9. W oknie polecenia programu Visual Studio wpisz:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Otwórz program Visual Studio.  
  
1.  Otwórz **nowy projekt** okna dialogowego polu, a następnie rozwiń węzeł **Visual C#** węzła projektu.  
  
 ![Obiekt MyProjectNode](../../extensibility/internals/media/myprojectnode.png "Obiekt MyProjectNode")  
  
 **Obiekt MyProjectNode** jest wyświetlany jako węzeł podrzędny programu Visual C# tylko w węźle systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie nowego projektu: Kulisy, część druga](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)