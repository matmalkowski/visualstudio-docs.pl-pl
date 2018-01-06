---
title: Tworzenie aplikacji ClickOnce z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 39a64737c3e34b7e0c4d89824b22f169d60d4fd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Tworzenie aplikacji ClickOnce z wiersza poleceń
W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], nawet jeśli są one tworzone w zintegrowane środowisko programistyczne (IDE) można tworzyć projektów z wiersza polecenia. W rzeczywistości, można ponownie utworzyć projekt utworzone za pomocą [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] na innym komputerze, który zawiera tylko [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zainstalowane. Dzięki temu można odtworzyć za pomocą zautomatyzowanego procesu kompilacji, na przykład w centralnej kompilacji laboratorium lub przy użyciu zaawansowanych skryptów techniki poza zakres tworzenia projektu.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Korzystanie z MSBuild do odtworzenia wdrożenia aplikacji ClickOnce  
 Po wywołaniu /target:publish programu msbuild w wierszu polecenia, informuje system MSBuild, aby skompilować projekt i utworzyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] w folderze publikowania aplikacji. Jest to równoważne wybraniu **publikowania** w IDE.  
  
 To polecenie wykonuje msbuild.exe, który znajduje się w ścieżce w wierszu polecenia środowiska Visual Studio.  
  
 "Miejsce docelowe" jest wskaźnikiem do MSBuild na temat sposobu przetwarzania polecenia. Kluczowe elementy docelowe są docelowych "kompilacji" i "Publikuj". Element docelowy kompilacji jest równoważne wybraniu kompilacji polecenia (lub naciskając klawisz F5) w środowisku IDE. Jeśli chcesz utworzyć projekt, można osiągnąć który wpisując `msbuild`. To polecenie działa, ponieważ element docelowy kompilacji jest elementem docelowym domyślnego dla wszystkich projektów generowane przez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Oznacza to, że jawnie zbędna, nie można określić cel kompilacji. W związku z tym, wpisując `msbuild` jest tej samej operacji wpisaniu `msbuild /target:build`.  
  
 `/target:publish` Polecenie informuje program MSBuild do wywołania, lokalizacja docelowa publikowania. Lokalizacja docelowa publikowania zależy od docelowego kompilacji. Oznacza to, że operacja publikowania ma podzbiorem operacji tworzenia. Na przykład jeśli wprowadzono zmiany do jednego z plików źródłowych Visual Basic lub C#, odpowiedni zestaw może automatycznie odbudować przez operację publikowania.  
  
 Aby uzyskać informacje dotyczące generowania pełnego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu narzędzia wiersza polecenia Mage.exe do utworzenia sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Tworzenie i tworzenie aplikacji ClickOnce podstawowe za pomocą MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Aby utworzyć i opublikować projekt ClickOnce  
  
1.  Kliknij przycisk **nowy projekt** z **pliku** menu. **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **aplikacji systemu Windows** i nadaj mu nazwę `CmdLineDemo`.  
  
3.  Z **kompilacji** menu, kliknij przycisk **publikowania** polecenia.  
  
     Ten krok zapewnia, że projekt jest skonfigurowany prawidłowo wygenerowało [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji.  
  
     Zostanie wyświetlony Kreator publikowania.  
  
4.  W Kreatorze publikowania kliknij **Zakończ**.  
  
     Program Visual Studio generuje i wyświetla domyślnej strony sieci Web o nazwie Publish.htm.  
  
5.  Zapisz projektu i zanotuj lokalizację folderu, w której jest przechowywany.  
  
 Powyższe kroki tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu, który został opublikowany po raz pierwszy. Teraz można odtworzyć kompilacji poza IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Aby odtworzyć kompilacji z wiersza polecenia  
  
1.  Zakończ [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Z systemu Windows **Start** menu, kliknij przycisk **wszystkie programy**, następnie **programu Microsoft Visual Studio**, następnie **programu Visual Studio Tools**, a następnie **Wiersz polecenia programu visual Studio**. Powinno to otwórz wiersz polecenia w folderze głównym bieżącego użytkownika.  
  
3.  W **wiersz polecenia programu Visual Studio**, zmień bieżący katalog w lokalizacji projektu, należy po prostu zbudować powyżej. Na przykład wpisz `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Aby usunąć istniejące pliki wygenerowane w "Aby utworzyć i opublikować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projektu," typ `rmdir /s publish`.  
  
     Ten krok jest opcjonalny, ale gwarantuje, że nowe pliki zostały wszystkie utworzone przez kompilacji wiersza polecenia.  
  
5.  Typ `msbuild /target:publish`.  
  
 Powyższe kroki powodują pełnej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji w podfolderze o nazwie P projektu**blikuj**. Jest CmdLineDemo.application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania. Folder CmdLineDemo_1.0.0.0 zawiera pliki CmdLineDemo.exe i CmdLineDemo.exe.manifest, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Setup.exe jest inicjujący, która domyślnie jest skonfigurowana do zainstalowania [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. DotNetFX folder zawiera pakietów redystrybucyjnych dla [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Jest to całego zestawu plików, należy wdrożyć aplikację sieci Web lub za pośrednictwem UNC lub dysk CD/DVD.  
  
## <a name="publishing-properties"></a>Właściwości publikacji  
 Podczas publikowania aplikacji w powyższych procedurach, następujące właściwości są wstawiane przez Kreatora publikacji w pliku projektu. Te właściwości mają bezpośredni wpływ jak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji jest generowany.  
  
 W CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Można zastąpić dowolne z tych właściwości w wierszu polecenia bez jego zmiany w samym pliku projektu. Na przykład utworzy następujące [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji bez inicjujący:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Właściwości publikacji są kontrolowane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z **publikowania**, **zabezpieczeń**, i **podpisywanie** stron właściwości **Projektant projektu** . Poniżej znajduje się opis właściwości publikacji, wraz ze wskazaniem każdej konfiguracji na różnych stronach właściwości projektanta aplikacji:  
  
-   `AssemblyOriginatorKeyFile`Określa plik klucza używany do podpisywania z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów aplikacji. Ten sam klucz może również przypisać do zestawów z silnej nazwy. Ta właściwość jest ustawiona na **podpisywanie** strony **projektanta projektu**.  
  
 Następujące właściwości są ustawione na **zabezpieczeń** strony:  
  
-   **Włączanie ustawień zabezpieczeń technologii ClickOnce** Określa, czy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty są generowane. Podczas tworzenia projektu, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Generowanie manifestu jest domyślnie wyłączone. Kreator automatycznie spowoduje wyłączenie tej flagi w przypadku publikowania po raz pierwszy.  
  
-   **TargetZone** określa poziom zaufania, aby być wydane do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Możliwe wartości to "Internet", "LocalIntranet" i "Custom". Internet i LocalIntranet spowoduje domyślne uprawnienia ustawioną być wydane do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Wartość domyślna to LocalIntranet, a zasadniczo oznacza pełne zaufanie. Niestandardowe Określa, że uprawnienia zostały jawnie określone w pliku app.manifest podstawowej mają być wydane do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji. Pliku app.manifest jest częściowe pliku manifestu, który zawiera tylko definicje informacji zaufania. Jest to ukryty plik automatycznie dodane do projektu podczas konfigurowania uprawnień **zabezpieczeń** strony.  
  
 Następujące właściwości są ustawione na **publikowania** strony:  
  
-   `PublishUrl`jest to lokalizacja, w której aplikacja zostanie opublikowana tutaj w IDE. Zostaną wstawione do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji, jeśli żadna `InstallUrl` lub `UpdateUrl` określona właściwość.  
  
-   `ApplicationVersion`Określa wersję [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Jest to numer wersji czterech cyfr. Jeśli ostatnia cyfra "*", a następnie `ApplicationRevision` zostanie zastąpiony wartością wstawione do manifestu w czasie kompilacji.  
  
-   `ApplicationRevision`Określa poprawkę. Jest to liczba całkowita, która zwiększany po każdej zmianie publikowanych w IDE. Zwróć uwagę, że nie jest on automatycznie zwiększany dla kompilacji, wykonane w wierszu polecenia.  
  
-   `Install`Określa, czy aplikacja jest zainstalowana aplikacja lub aplikację do uruchamiania z sieci Web.  
  
-   `InstallUrl`(tego nie pokazano) to lokalizacja, w której użytkownicy będą instalować aplikację z. Jeśli jest określony, ta wartość jest wbudowany w program inicjujący setup.exe Jeśli `IsWebBootstrapper` właściwość jest włączona. Również znajduje się w przypadku manifestu aplikacji `UpdateUrl` nie jest określona.  
  
-   `SupportUrl`(tego nie pokazano) jest lokalizacja konsolidowana **Dodaj lub usuń programy** okno dialogowe dla zainstalowanej aplikacji.  
  
 Następujące właściwości są ustawiane w **aktualizacji aplikacji** okno dialogowe, dostępne z **publikowania** strony.  
  
-   `UpdateEnabled`Wskazuje, czy aplikacja ma sprawdzać dostępność aktualizacji.  
  
-   `UpdateMode`Określa aktualizacje pierwszego planu lub aktualizowane w tle.  
  
-   `UpdateInterval`Określa, jak często aplikacja ma sprawdzać dostępność aktualizacji.  
  
-   `UpdateIntervalUnits`Określa, czy `UpdateInterval` wartość znajduje się w jednostkach godziny, dni lub tygodnie.  
  
-   `UpdateUrl`(tego nie pokazano) to lokalizacja, z której aplikacja będzie otrzymywać aktualizacje. Jeśli jest określony, ta wartość zostanie wstawiony do manifestu aplikacji.  
  
-   Następujące właściwości są ustawiane w **opcji publikowania** okno dialogowe, dostępne z **publikowania** strony.  
  
-   `PublisherName`Określa nazwę wydawcy, wyświetlane w wierszu wyświetlany podczas instalowania i uruchamiania aplikacji. W przypadku zainstalowanej aplikacji, jest również używana, należy określić nazwę folderu na **Start** menu.  
  
-   `ProductName`Określa nazwę produktu wyświetlany w wierszu wyświetlany podczas instalowania i uruchamiania aplikacji. W przypadku zainstalowanej aplikacji, jest również używana, określ nazwę skrótu na **Start** menu.  
  
-   Następujące właściwości są ustawiane w **wymagania wstępne** okno dialogowe, dostępne z **publikowania** strony.  
  
-   `BootstrapperEnabled`Określa, czy do generowania programu inicjującego setup.exe.  
  
-   `IsWebBootstrapper`Określa, czy program inicjujący setup.exe działa w trybie opartej na dysku lub w sieci Web.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl PublishURL i UpdateURL  
 W poniższej tabeli przedstawiono cztery opcje wdrażania ClickOnce adresu URL.  
  
|Opcja adresu URL|Opis|  
|----------------|-----------------|  
|`PublishURL`|Wymagane, jeśli w przypadku publikowania aplikacji ClickOnce do witryny sieci Web.|  
|`InstallURL`|Opcjonalny. Ustaw tę opcję adresu URL, jeśli witryna instalacji różni się od `PublishURL`. Na przykład można ustawić `PublishURL` ścieżka FTP i zestawu `InstallURL` do adresu URL sieci Web.|  
|`SupportURL`|Opcjonalny. Ustaw tę opcję adresu URL, jeśli witrynę pomocy technicznej jest inna niż `PublishURL`. Na przykład można ustawić `SupportURL` do witryny sieci Web pomocy technicznej firmy.|  
|`UpdateURL`|Opcjonalny. Ustaw tę opcję adresu URL, jeśli lokalizacja aktualizacji jest inna niż `InstallURL`. Na przykład można ustawić `PublishURL` ścieżka FTP i zestawu `UpdateURL` do adresu URL sieci Web.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)