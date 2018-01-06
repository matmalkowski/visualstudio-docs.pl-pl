---
title: "Wdrażanie niestandardowego procesora dyrektywy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7c7881c20412ab5ffc3f1c4486958f4b5ca68a1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-custom-directive-processor"></a>Wdrażanie niestandardowego procesora dyrektywy
Aby użyć niestandardowego procesora dyrektywy w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na dowolnym komputerze, musi być zarejestrowany za pomocą jednej z metod opisanych w tym temacie.  
  
 Alternatywne metody to:  
  
-   [Rozszerzenie programu Visual Studio (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832). Zapewnia to sposób zainstalowania i odinstalowywania procesora dyrektywy zarówno na swoim komputerze, jak i na innych komputerach. Zazwyczaj można umieścić inne funkcje w tym samym VSIX.  
  
-   [Pakiet VSPackage](../extensibility/internals/vspackages.md). W przypadku definiowania VSPackage, zawierającego inne funkcje oprócz procesora dyrektywy, istnieje wygodna metoda rejestracji procesora dyrektywy.  
  
-   Ustaw klucz rejestru. W tej metodzie należy dodać wpis rejestru dla procesora dyrektywy.  
  
 Należy użyć jednej z tych metod, tylko wtedy, gdy chcesz transformacji szablonu tekstowego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Jeśli używasz niestandardowego hosta w aplikacji, niestandardowy host jest odpowiedzialny za znalezienie procesorów dyrektyw dla każdej dyrektywy.  
  
## <a name="deploying-a-directive-processor-in-a-vsix"></a>Wdrażanie procesora dyrektywy w VSIX  
 Można dodać niestandardowego procesora dyrektywy do [rozszerzenia serwera Visual Studio (VSIX)](http://msdn.microsoft.com/en-us/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 Upewnij się, że w pliku .vsix znajdują się dwa następujące elementy:  
  
-   Zestaw (.dll), który zawiera niestandardową klasę procesora dyrektywy.  
  
-   Plik .pkgdef, który rejestruje procesor dyrektywy. Główna nazwa pliku musi być zgodna z nazwą zestawu. Na przykład, pliki mogą być nazwane CDP.dll i CDP.pkgdef.  
  
 Aby sprawdzić lub zmienić zawartość pliku .vsix, zmień rozszerzenie nazwy pliku na .zip, a następnie otwórz go. Po zakończeniu edycji zawartości zmień nazwę pliku z powrotem na .vsix.  
  
 Istnieje kilka sposobów tworzenia plików .vsix. Poniższa procedura opisuje jedną z metod.  
  
#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Aby opracować niestandardowy procesor dyrektywy w projekcie VSIX  
  
1.  Tworzenie projektu VSIX w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   W **nowy projekt** okna dialogowego rozwiń **Visual Basic** lub **Visual C#**, następnie rozwiń węzeł **rozszerzalności**. Kliknij przycisk **projektu VSIX**.  
  
2.  W **source.extension.vsixmanifest**obsługiwanych wersji i Ustaw typ zawartości.  
  
    1.  W pliku VSIX manifestu edytorze na **zasoby** , wybierz pozycję **nowy** i ustaw właściwości nowy element:  
  
         **Typ zawartości** = **pakiet VSPackage**  
  
         **Źródło projektu** = \<*bieżącego projektu*>  
  
    2.  Kliknij przycisk **wybrane wersje** i Sprawdź typy instalacji, na którym ma zostać procesora dyrektywy może być używany.  
  
3.  Dodaj plik .pkgdef i ustaw jego właściwości, które mają zostać uwzględnione w VSIX.  
  
    1.  Utwórz plik tekstowy i nadaj mu nazwę \< *assemblyName*> .pkgdef.  
  
         \<*assemblyName*> zazwyczaj jest taka sama jak nazwa projektu.  
  
    2.  Wybierz go w oknie Eksploratora rozwiązań i ustaw jego właściwości w następujący sposób:  
  
         **Akcja kompilacji** = **zawartości**  
  
         **Kopiuj do katalogu wyjściowego** = **zawsze Kopiuj**  
  
         **Uwzględnione w pliku VSIX** = **True**  
  
    3.  Ustaw nazwę VSIX i upewnij się, że identyfikator jest unikatowy.  
  
4.  Dodaj następujący tekst do pliku .pkgdef.  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Zastąp własnymi nazwami następujące nazwy: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5.  Dodaj następujące odwołania do projektu:  
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost. \*.0**  
  
6.  Dodaj niestandardową klasę procesora dyrektywy do projektu.  
  
     Jest to klasa publiczna, który powinny implementować <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
#### <a name="to-install-the-custom-directive-processor"></a>Aby zainstalować procesor dyrektywy niestandardowej  
  
1.  W Eksploratorze Windows (Eksplorator plików w systemie Windows 8) otwórz katalog kompilacji (zazwyczaj bin\Debug lub bin\Release).  
  
2.  Jeśli chcesz zainstalować procesor dyrektywy na innym komputerze, skopiuj plik .vsix do innego komputera.  
  
3.  Kliknij dwukrotnie plik .vsix. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Pojawi się Instalator rozszerzenia.  
  
4.  Uruchom ponownie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Teraz można uruchomić szablony tekstowe, które zawierają dyrektywy odwołujące się do procesora dyrektywy niestandardowej. Każda dyrektywa jest tej postaci:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`  
  
#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Aby odinstalować lub tymczasowo wyłączyć procesor dyrektywy niestandardowej  
  
1.  W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **narzędzia** menu, kliknij przycisk **Menedżera rozszerzenia**.  
  
2.  Wybierz VSIX, który zawiera procesora dyrektywy, a następnie kliknij przycisk **Odinstaluj** lub **wyłączyć**.  
  
### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Rozwiązywanie problemów z procesorem dyrektywy w VSIX  
 Jeśli procesor dyrektywy nie działa, poniższe sugestie mogą pomóc:  
  
-   Nazwa procesora określona w niestandardowych dyrektywy powinna odpowiadać `CustomDirectiveProcessorName` określonej w pliku .pkgdef.  
  
-   Twoje `IsDirectiveSupported` metoda musi zwracać `true` po została przekazana nazwa użytkownika `CustomDirective`.  
  
-   Jeśli nie są widoczne w Menedżerze rozszerzeń rozszerzenie, ale system nie pozwoli go zainstalować, usunąć rozszerzenia z **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .  
  
-   Otwórz plik .vsix i sprawdź jego zawartość. Aby go otworzyć, zmień rozszerzenie nazwy pliku na .zip. Sprawdź, czy zawiera on pliki .dll, .pkgdef i extension.vsixmanifest. Plik extension.vsixmanifest powinien zawierać odpowiednią listę w węźle SupportedProducts i powinien też zawierać węzeł VsPackage w węźle Content:  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Wdrażanie procesora dyrektywy w VSPackage  
 Jeśli procesor dyrektywy jest częścią pakietu VSPackage, który zostanie zainstalowany w pamięci podręcznej GAC, system może automatycznie wygenerować plik .pkgdef.  
  
 Umieść następujący atrybut w klasie pakietu:  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Ten atrybut jest umieszczany w klasie pakietu, a nie w klasie procesora dyrektywy.  
  
 Plik .pkgdef zostanie wygenerowany podczas tworzenia projektu. Podczas instalowania pakietu VSPackage plik .pkgdef zarejestruje procesor dyrektywy.  
  
 Sprawdź, czy plik .pkgdef pojawia się w folderze kompilacji, zwykle bin\Debug lub bin\Release. Jeśli nie ma, otwórz plik .csproj w edytorze tekstów i usunąć następującego węzła: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.  
  
 Aby uzyskać więcej informacji, zobacz [VSPackages](../extensibility/internals/vspackages.md).  
  
## <a name="setting-a-registry-key"></a>Ustawianie klucza rejestru.  
 Ta metoda instalacji procesora dyrektywy niestandardowej jest najmniej polecana. Nie zapewnia wygodnego sposobu włączania i wyłączania procesora dyrektywy i nie zapewnia metody dystrybucji procesora dyrektywy do innych użytkowników.  
  
> [!CAUTION]
>  Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze.  
  
#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Aby zarejestrować procesor dyrektywy przez ustawienie klucza rejestru  
  
1.  Run `regedit`.  
  
2.  W edytorze regedit przejdź do  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
     Jeśli chcesz zainstalować procesora dyrektywy w wersji eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Wstaw "Exp" po "11.0".  
  
3.  Dodaj klucz rejestru, który ma taką samą nazwę jak klasa procesora dyrektywy.  
  
    -   W drzewie rejestru kliknij prawym przyciskiem myszy **DirectiveProcessors** węzła, wskaż **nowy**, a następnie kliknij przycisk **klucza**.  
  
4.  W nowym węźle dodaj wartości ciągu dla Class i CodeBase lub Assembly, zgodnie z poniższymi tabelami.  
  
    1.  Kliknij prawym przyciskiem myszy węzeł, który został utworzony, wskaż pozycję **nowy**, a następnie kliknij przycisk **wartość ciągu**.  
  
    2.  Wyedytuj nazwę wartości.  
  
    3.  Kliknij dwukrotnie nazwę i wyedytuj dane.  
  
 Jeśli procesor dyrektywy niestandardowej nie znajduje się w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:  
  
|Nazwa|Typ|Dane|  
|----------|----------|----------|  
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|  
|Class|REG_SZ|**\<Nazwa Namespace >. \<Nazwa klasy >**|  
|CodeBase|REG_SZ|**\<Ścieżka >\\< nazwę zestawu\>**|  
  
 W przypadku zestawu w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:  
  
|Nazwa|Typ|Dane|  
|----------|----------|----------|  
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|  
|Class|REG_SZ|\<**Twoje pełni kwalifikowaną nazwą klasy**>|  
|Zestaw|REG_SZ|\<**Nazwę zestawu w GAC**>|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego](../modeling/creating-custom-t4-text-template-directive-processors.md)