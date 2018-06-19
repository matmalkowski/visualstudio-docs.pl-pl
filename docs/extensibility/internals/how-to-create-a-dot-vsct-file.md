---
title: 'Porady: tworzenie. Pliku Vsct | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6456b0b866f08956862fa197719354bedf0ecf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132923"
---
# <a name="how-to-create-a-vsct-file"></a>Porady: tworzenie. Plik Vsct  
  
Istnieje kilka sposobów, aby utworzyć plik konfiguracji (vsct) oparte na języku XML programu Visual Studio polecenia tabeli.  
  
-   Możesz utworzyć nowy pakiet VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietu szablonu.  
  
-   Można użyć kompilatora konfiguracji tabeli polecenia opartych na języku XML, Vsct.exe, aby wygenerować plik z istniejącego pliku .ctc.  
  
-   Vsct.exe służy do generowania pliku vsct z istniejącego pliku .cto.  
  
-   Można ręcznie utworzyć nowego pliku vsct.  
  
 W tym temacie wyjaśniono, jak ręcznie utworzyć nowego pliku vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Aby ręcznie utworzyć nowego pliku vsct  
  
1.  Uruchom [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **pliku**.  
  
3.  W **szablony** okienku, kliknij przycisk **pliku XML** , a następnie kliknij przycisk **Otwórz**.  
  
4.  Na **widoku** menu, kliknij przycisk **okna właściwości** Aby wyświetlić właściwości pliku XML.  
  
5.  W **właściwości** okna, kliknij przycisk Przeglądaj (...) we właściwości schematów.  
  
6.  Na liście schematów XSD wybierz schemat vsct.xsd. Jeśli nie jest na liście, kliknij przycisk **Dodaj** , a następnie znajdź plik na dysku lokalnym. Kliknij przycisk **OK** po zakończeniu.  
  
7.  W pliku XML, wpisz `<CommandTable` , a następnie naciśnij klawisz TAB. Tag zamykający wpisując `>`.  
  
     Spowoduje to utworzenie pliku vsct podstawowe.  
  
8.  Wypełnij elementy pliku XML, który chcesz dodać, zgodnie z [schematu VSCT](../../extensibility/vsct-xml-schema-reference.md). Aby uzyskać więcej informacji, zobacz [tworzenie. Pliki Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Porady: tworzenie. Plik Vsct z istniejącego. Plik CTC  
  
Można utworzyć pliku vsct opartych na języku XML z istniejącego pliku źródłowego .ctc tabeli polecenia. Dzięki temu można korzystać z nowej opartych na języku XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] format kompilatora tabeli (VSCT) polecenia.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Aby utworzyć plik vsct z pliku .ctc  
  
1.  Uzyskaj kopię języka Perl.  
  
2.  Uzyskaj kopię programu skryptów języka Perl ConvertCTCToVSCT.pl, zazwyczaj znajduje się w  *\<ścieżki instalacji programu Visual Studio SDK >* \VisualStudioIntegration\Tools\bin folderu.  
  
3.  Uzyskaj kopię .ctc plik źródłowy, który ma zostać przekonwertowany.  
  
4.  Umieścić pliki w tym samym katalogu.  
  
5.  W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia oknie monitu, przejdź do katalogu.  
  
6.  Typ  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     gdzie PkgCmd.ctc jest nazwa pliku .ctc i PkgCmd.vsct jest nazwą pliku vsct, który chcesz utworzyć.  
  
     Spowoduje to utworzenie nowego vsct polecenia tabeli źródłowej pliku XML. Plik można kompilować przy użyciu Vsct.exe, kompilator VSCT, jak w przypadku każdego innego pliku vsct.  
  
    > [!NOTE]
    >  Aby poprawić czytelność pliku vsct, należy ponowne formatowanie komentarze XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Porady: tworzenie. Plik Vsct z istniejącego. Pliku Cto  
  
Można utworzyć pliku vsct opartych na języku XML z istniejącego pliku binarnego .cto. W ten sposób pozwala korzystać z nowego formatu kompilatora tabeli polecenia. Ten proces działa nawet wtedy, gdy plik .cto został skompilowany z pliku .ctc. Możesz edytować i skompilować pliku vsct w innym pliku .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Aby utworzyć plik vsct z pliku .cto  
  
1.  Uzyskaj kopię pliku .cto i plik .ctsym.  
  
2.  Umieścić pliki w tym samym katalogu co vsct.exe kompilatora.  
  
3.  W programie Visual Studio wierszu polecenia przejdź do katalogu, który zawiera pliki .cto i .ctsym.  
  
4.  Typ **vsct.exe** *ctofilename *** .cto** * vsctfilename***vsct -S***symfilename ***.ctsym**.  
  
     `ctofilename` to nazwa pliku .cto `vsctfilename` to nazwa pliku vsct, który chcesz utworzyć, a `symfilename` to nazwa pliku .ctsym.  
  
     Ten proces tworzy nowy vsct polecenia tabeli kompilatora plik XML. Możesz edytować i skompiluj plik z vsct.exe, kompilator vsct, jak w przypadku każdego innego pliku vsct.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Dodawanie pliku vsct w projekcie nie powoduje go skompilować. Musi ona zawierać w procesie kompilacji.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Aby dodać plik vsct do kompilacji projektu  
  
1.  Otwórz plik projektu w edytorze. Jeśli projekt został załadowany, należy go najpierw zwolnienia.  
  
2.  Dodaj [ItemGroup — element](../../msbuild/itemgroup-element-msbuild.md) zawierający VSCTCompile element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName element powinien zawsze mieć ustawioną `Menus.ctmenu`.  
  
3.  Jeśli projekt zawiera plik .resx, Dodaj element EmbeddedResource, który zawiera MergeWithCTO element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Ten kod znaczników powinien znajdować się wewnątrz elementu ItemGroup, który zawiera zasoby osadzone.  
  
4.  Otwórz plik pakietu, zwykle o nazwie *ProjectName*Package.cs lub *ProjectName*Package.vb w edytorze.  
  
5.  Dodaj atrybut ProvideMenuResource do klasy pakietu, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Pierwsza wartość parametru musi odpowiadać wartości atrybutu ResourceName zdefiniowanych w pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie. Pliki Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)