---
title: MSI i wdrażanie VSIX DSL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: b66c2e2a61ebe046ab04006e1f7ce345151224c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Wdrażanie pakietów MSI i VSIX języka DSL
Języka specyficznego dla domeny można zainstalować na komputerze lokalnym lub na innych komputerach. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi być zainstalowany na komputerze docelowym.  
  
##  <a name="which"></a> Wybór między VSIX i wdrożenia MSI  
 Istnieją dwie metody wdrażania języka specyficznego dla domeny:  
  
|Metoda|Zalety|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia)|Bardzo łatwa do wdrożenia: kopiowania, a następnie wykonaj **.vsix** plik z projektu DslPackage.<br /><br /> Aby uzyskać więcej informacji, zobacz [instalowania i odinstalowywania DSL przy użyciu VSX](#Installing).|  
|MSI (plik Instalatora)|— Umożliwia użytkownikowi otwieranie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] klikając dwukrotnie plik DSL.<br />-Kojarzy ikony typu pliku DSL w komputerze docelowym.<br />-Kojarzy XSD (schemat XML) z typem pliku DSL. Dzięki temu można uniknąć ostrzeżeń podczas ładowania pliku do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Instalacja projektu należy dodać do rozwiązania, aby utworzyć instalatora MSI.<br /><br /> Aby uzyskać więcej informacji, zobacz [wdrażanie DSL przy użyciu pliku MSI](#msi).|  
  
##  <a name="Installing"></a> Instalowanie i odinstalowywanie DSL przy użyciu VSX  
 Po zainstalowaniu programu DSL przez tę metodę użytkownika DSL plik można otworzyć z poziomu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale nie można otworzyć pliku z Eksploratora Windows.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Aby zainstalować DSL za pomocą VSX  
  
1.  W komputerze, należy znaleźć **.vsix** pliku, który został utworzony w projekcie DSL pakietu.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DslPackage** projektu, a następnie kliknij przycisk **Otwórz Folder w Eksploratorze Windows**.  
  
    2.  Zlokalizuj plik **bin\\\*\\***YourProject***. DslPackage.vsix**  
  
2.  Kopiuj **.vsix** plik na komputer docelowy, na którym chcesz zainstalować DSL. Może to być własnym komputerze lub inny.  
  
    -   Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] obsługującej DSLs w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [obsługiwane wersje Visual Studio wizualizacji i modelowania SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] określony w **DslPackage\source.extensions.manifest**.  
  
3.  Na komputerze docelowym, kliknij dwukrotnie **.vsix** pliku.  
  
     **Instalator rozszerzenia programu Visual Studio** otwiera i instaluje rozszerzenie.  
  
4.  Uruchom lub uruchom ponownie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Aby przetestować DSL, użyj [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Aby utworzyć nowy plik o rozszerzeniu zdefiniowana dla sieci DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Aby odinstalować DSL, który został zainstalowany przy użyciu VSX  
  
1.  Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzenia**.  
  
2.  Rozwiń węzeł **zainstalowanych rozszerzeń**.  
  
3.  Wybierz rozszerzenia, w którym jest zdefiniowany DSL, a następnie kliknij przycisk **Odinstaluj**.  
  
 Rzadko uszkodzony rozszerzenia nie udało się załadować i tworzy raport w oknie błąd, ale nie są wyświetlane w Menedżerze rozszerzeń. W takim przypadku należy usunąć rozszerzenia przez usunięcie pliku:  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a> Wdrażanie DSL w pliku MSI  
 Definiując plik MSI (Instalator Windows) dla sieci DSL, mogą umożliwiać użytkownikom otwieranie plików DSL z Eksploratora Windows. Można również skojarzyć ikonę i krótki opis z rozszerzeniem nazwy. Ponadto MSI można zainstalować XSD, który może służyć do sprawdzania poprawności DSL plików. Inne składniki można dodać do pliku MSI, który zostanie zainstalowany w tym samym czasie.  
  
 Aby uzyskać więcej informacji na temat plików MSI i innych opcji wdrażania, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).  
  
 Aby utworzyć instalatora MSI, Dodaj projekt Instalatora do Twojej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania. Najprostszą tworzenia projektu Instalatora jest użycie szablonu CreateMsiSetupProject.tt, który można pobrać z [lokacji VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Aby wdrożyć DSL w pliku MSI  
  
1.  Ustaw `InstalledByMsi` w manifeście rozszerzenia. Zapobiega to VSX jest instalowana i odinstalowywana z wyjątkiem przez MSI. Jest to ważne, Jeśli dołączysz innych składników w MSI.  
  
    1.  Open DslPackage\source.extension.tt  
  
    2.  Wstaw następujący wiersz przed `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Utwórz lub Edytuj ikonę, która reprezentuje użytkownika DSL w Eksploratorze Windows. Na przykład edytować **DslPackage\Resources\File.ico**  
  
3.  Upewnij się, że następujące atrybuty DSL użytkownika są prawidłowe:  
  
    -   W Eksploratorze DSL kliknij węzeł główny, a następnie w oknie właściwości, przejrzyj:  
  
        -   Opis  
  
        -   Wersja  
  
    -   Kliknij przycisk **edytor** węzeł i kliknij w oknie właściwości **ikona**. Ustaw wartość, aby odwołać plik ikony w **DslPackage\Resources**, takich jak **File.ico**  
  
    -   Na **kompilacji** menu, otwórz **programu Configuration Manager**i wybierz konfigurację, którą chcesz utworzyć, takie jak **wersji** lub **debugowania** .  
  
4.  Przejdź do [strony głównej wizualizacji i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=186128)i z **pobiera** karcie, Pobierz **CreateMsiSetupProject.tt**.  
  
5.  Dodaj **CreateMsiSetupProject.tt** do projektu Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Spowoduje to utworzenie pliku o nazwie **CreateMsiSetupProject.vdproj**.  
  
6.  W Eksploratorze Windows, skopiuj Dsl\\Instalatora o nazwie *.vdproj do nowego folderu.  
  
     (Jeśli chcesz, można teraz wykluczyć CreateMsiSetupProject.tt z projektu Dsl.)  
  
7.  W **Eksploratora rozwiązań**, Dodaj **Instalator\\\*vdproj** jako istniejącego projektu.  
  
8.  Na **projektu** menu, kliknij przycisk **zależności projektu**.  
  
     W **zależności projektu** oknie dialogowym Wybierz projektu Instalatora.  
  
     Zaznacz pole obok **DslPackage**.  
  
9. Ponownie skompiluj rozwiązanie.  
  
10. W Eksploratorze Windows zlokalizuj plik MSI wbudowanych w projekcie Instalatora.  
  
     Skopiuj plik MSI na komputerze, na którym chcesz zainstalować z DSL. Kliknij dwukrotnie plik MSI. Instalator jest uruchamiany.  
  
11. W komputerze docelowym Utwórz nowy plik rozszerzeniem sieci DSL. Sprawdź, czy:  
  
    -   W widoku listy Eksploratora Windows plik pojawi się ikona i zdefiniowanym przez użytkownika.  
  
    -   Dwukrotne kliknięcie pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamia i otwiera plik DSL w edytorze DSL.  
  
 Jeśli wolisz, możesz utworzyć projektu Instalatora ręcznie, zamiast używać szablonu tekstowego. Aby uzyskać wskazówki, który zawiera tę procedurę zobacz rozdział 5 [wizualizacji i modelowania laboratorium SDK](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Aby odinstalować DSL, który został zainstalowany z Instalatora MSI  
  
1.  W systemie Windows, należy otworzyć **programy i funkcje** Panelu sterowania.  
  
2.  Odinstaluj DSL.  
  
3.  Uruchom ponownie program Visual Studio.