---
title: Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea1c04066099b385b03c1b81bc4d85c7fb13e329
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120319"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint
  W tym temacie opisano różne problemy, które mogą wystąpić podczas pakowania i wdrażania rozwiązań programu SharePoint.

## <a name="enable-enhanced-debugging"></a>Włącz rozszerzony debugowania
 Aby zdiagnozować między Visual Studio, SharePoint i innych warstw, klucz rejestru EnableDiagnostics służy do wyświetlania ślad stosu. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint debugowania](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Dodaj dane wyjściowe projektu do pakietu rozwiązań
 Do pakietu przy użyciu projektanta pakietów można dodać danych wyjściowych projektu. Jednak podczas dodawania danych wyjściowych projektu, upewnij się, że platforma projektu jest zgodna z platformy rozwiązania programu SharePoint. Firma Microsoft zaleca użycie **Any CPU** platformy docelowej dla zestawów, które mają zostać wdrożone na serwerze programu SharePoint. Aby uzyskać więcej informacji, zobacz [strona kompilowania, Projektant projektu &#40;Visual Basic&#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) i [okno dialogowe Zaawansowane ustawienia kompilatora &#40;Visual Basic&#41;](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).

## <a name="validation-warnings-and-errors"></a>Sprawdzanie poprawności ostrzeżeń i błędów
 Narzędzi programowanie SharePoint w Visual Studio wykonaj kroki weryfikacji, aby sprawdzić, czy pakiet rozwiązania jest poprawnie sformułowany. Można również utworzyć niestandardowego sprawdzania poprawności kroki dla funkcji i pakietów. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie funkcji niestandardowej oraz pakietu reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Rozwiązywanie konfliktów wdrożenia
 Podczas wdrażania rozwiązania SharePoint kolizji może się okazać, gdy element na serwerze ma tej samej nazwie, adres URL lub identyfikator jako element do pakietu rozwiązań. Możesz zmienić **Rozwiązywanie konfliktów wdrożenia** właściwości, aby rozwiązać, raportu lub zignorować kolizji dla modułów, części sieci Web, wystąpienia listy i typy zawartości.

 Poniższa tabela przedstawia ustawienia **Rozwiązywanie konfliktów wdrożenia** właściwości.

|Wartość|Opis|
|-----------|-----------------|
|Automatyczne|Wykrywa kolizje i pozwala rozwiązać konflikty w automatycznie.|
|Monituj|Wykrywa kolizje i raporty dewelopera, przed rozwiązywania konfliktów.|
|Brak|Nie wykrywa kolizji.|

## <a name="differences-between-f5-deployment"></a>Różnice między wdrożenia F5
 Jeśli używasz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do wdrażania projektu programu SharePoint do lokalnego serwera programu SharePoint, testowanie i debugowanie, istnieją pewne dodatkowe kroki są wykonywane przez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1.  Resetuj Internet Information Service (IIS) podczas wykonywania kroku wdrożenia.

2.  Automatycznie skojarzyć przepływ pracy.

3.  Ustawianie kolejności aktywacji funkcji zgodnie z hierarchii w Projektancie pakietu.

 Możesz dodać kroki wdrażania niestandardowego do dalszych zmian **F5** zachowanie. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Opóźnienie wyświetlania strony programu SharePoint podczas wdrażania wizualny składnik web part
 Strony programu SharePoint trwa długo po wdrożeniu wizualny składnik Web part, aby otworzyć folder Bin na [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], lub [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Jeśli zmienisz wszystkie pliki w najwyższego poziomu [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] rekompiluje całej aplikacji sieci Web katalogu, takiego jak katalog Bin. Może to spowodować opóźnienie wynoszące do 25 sekund dla strony programu SharePoint do renderowania.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Aby obejść ten problem, wykonaj następujące czynności:

1.  Zainstaluj aktualizację KB967535 zgodnie z opisem w artykule firmy Microsoft Support [NAPRAW: ustalenie dwa problemy w programie ASP.NET w usługach IIS 7.0 dla systemu Windows Vista i Windows Server 2008 dostępna jest poprawka](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Dodaj następujący wiersz do pliku Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Wdrażanie projektu SharePoint kończy się niepowodzeniem z powodu błędu "Nie można wyodrębnić pliku cab w rozwiązaniu"
 Jeśli nazwa dowolnego elementu projektu SharePoint zawiera nawiasy, jego rozwiązanie nie powiedzie się na wdrożenia z powodu błędu.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd podczas kroku wdrożenia Dodaj rozwiązanie: nie można wyodrębnić pliku cab w rozwiązaniu.

### <a name="resolution"></a>Rozwiązanie
 Aby obejść ten problem, należy usunąć wszelkie nawiasy w nazwach SharePoint — elementy projektu.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Błąd pojawia się w przypadku wdrażania wizualny składnik web part do lokacji w innej aplikacji sieci web
 Podczas pierwszego wdrażania składnika Web part programu visual do lokacji w aplikacji sieci Web innego niż ten, na którym jest obecnie wdrożona (, zmieniając właściwość SiteUrl visual części sieci Web), wystąpi błąd.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd podczas kroku wdrożenia Dodaj rozwiązanie: funkcja o identyfikatorze [#] został już zainstalowany w tej farmie. Użyj atrybutu force, aby jawnie ponownie zainstalować tę funkcję.

### <a name="resolution"></a>Rozwiązanie
 Ten błąd występuje, ze względu na sposób visual funkcje składników Web part są wycofany w programie SharePoint. Aby pomyślnie wdrożyć składnik Web part programu visual, wdrożenie ponownie, wybierając **F5** klucza.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>W przypadku wdrażania kontrolek użytkownika zagnieżdżonych pojawi się ostrzeżenie
 To ostrzeżenie występuje, gdy należy wdrożyć rozwiązania programu SharePoint, które ma formantów zagnieżdżonych użytkownika, takich jak visual składnika Web part, który zawiera kontrolki użytkownika lub formant użytkownika, który zawiera składnika Web part programu visual lub inny formant użytkownika. To ostrzeżenie występuje, czy dodawanie formantu do projektanta, przeciągając je z przybornika lub za pomocą @Register dyrektywy w widoku źródła.

### <a name="error-message"></a>Komunikat o błędzie
 Ostrzeżenie 1 Element "[*nazwa formantu*]" nie jest elementem znane. Może to wystąpić, jeśli wystąpi błąd kompilacji w witrynie sieci Web, lub Brak pliku web.config.

### <a name="resolution"></a>Rozwiązanie
 Jeśli [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] system projektów nie został powiadomiony o kontrolkę użytkownika zagnieżdżonych, nie można udostępnić IntelliSense i jego emituje to ostrzeżenie. System projektu nie rozpoznaje kontrolki użytkownika zagnieżdżonych Jeśli projekt nie jest skompilowany i nie zamknięciu i ponownym otwarciu projektanta lub wycofać automatycznie opcja jest włączona, co powoduje, że formant użytkownika ma zostać wycofane z gałęzi SharePoint po debugowaniu.

 Aby usunąć to ostrzeżenie, skompilować projekt i następnie zamknij i ponownie otwórz projektanta lub wyłącz automatyczne wycofać opcji dla projektu. Aby to zrobić, należy wyczyścić **wycofać automatycznie po debugowaniu** pole wyboru na **SharePoint** karty w oknie dialogowym właściwości projektu.

## <a name="see-also"></a>Zobacz także
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

