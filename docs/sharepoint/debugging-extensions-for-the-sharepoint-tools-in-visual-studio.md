---
title: Debugowanie rozszerzeń dla narzędzi SharePoint w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 366103b7912491bca5c614e3681ab53e1c9f7257
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238072"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Debugowanie rozszerzeń dla narzędzi SharePoint w Visual Studio
  Można debugować rozszerzeń narzędzi SharePoint w eksperymentalnym wystąpieniu lub prawidłowe wystąpienie programu Visual Studio. Jeśli potrzebujesz rozwiązać problem z rozszerzeniem, można również zmodyfikować wartości rejestru, aby wyświetlić dodatkowe informacje o błędzie i skonfigurować sposób wykonuje polecenia SharePoint w Visual Studio.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Debugowanie rozszerzeń eksperymentalne wystąpienie programu Visual Studio
 Do ochrony środowiska deweloperskiego Visual Studio przed przypadkowym uszkodzeniem przez rozszerzenia zastosowaniem, programu Visual Studio SDK oferuje alternatywne wystąpienie programu Visual Studio o nazwie *eksperymentalne wystąpienie*, którego można używać Aby zainstalować i przetestować rozszerzenia. Tworzenie nowych rozszerzeń przy użyciu prawidłowe wystąpienie programu Visual Studio, ale debugowania i uruchamiać je w eksperymentalnym wystąpieniu. Aby uzyskać więcej informacji, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).

 Jeśli wdrażania rozszerzenia przy użyciu projektu VSIX, projektu VSIX jest projekt startowy w rozwiązaniu Visual Studio automatycznie instalowany i uruchamiany rozszerzenia w eksperymentalnym wystąpieniu, podczas debugowania rozwiązania. Projekt startowy jest projekt, który jest uruchamiany podczas debugowania rozwiązania, które zawiera wiele projektów. Aby uzyskać więcej informacji o używaniu projektu VSIX do wdrażania rozszerzenia, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Aby uzyskać przykłady pokazujące, które pokazują, jak można debugować różne typy rozszerzeń eksperymentalne wystąpienie programu Visual Studio zobacz następujące wskazówki:

-   [Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu — część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [Przewodnik: Wywoływanie modelu obiektów klienta SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Debugowanie rozszerzeń w regularnych wystąpienie programu Visual Studio
 Jeśli chcesz debugować projekt rozszerzenia w regularnych wystąpienie programu Visual Studio, należy najpierw zainstalować rozszerzenie w regularnych wystąpienia. Następnie dołącz debuger do drugiego proces programu Visual Studio. Po zakończeniu można usunąć rozszerzenia, aby nie ładuje na komputerze dewelopera.

#### <a name="to-install-the-extension"></a>Aby zainstalować to rozszerzenie

1.  Zamknij wszystkie wystąpienia programu Visual Studio.

2.  Otwórz w folderze wyjściowym kompilacji projektu rozszerzenia *.vsix* pliku, kliknij go dwukrotnie lub otwieranie menu skrótów, a następnie wybierając **Otwórz**:

3.  W **Instalator rozszerzenia programu Visual Studio** oknie dialogowym Wybierz wersji programu Visual Studio, do której chcesz zainstalować rozszerzenie, a następnie wybierz pozycję **zainstalować** przycisku.

     Visual Studio instaluje pliki rozszerzeń %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*nazwisko autora*\\*Nazwa rozszerzenia* \\ *wersji*. Ostatnie trzy foldery w tej ścieżce są tworzone na podstawie `Author`, `Name`, i `Version` elementów w *extension.vsixmanifest* pliku rozszerzenia.

4.  Po zainstalowaniu rozszerzenia programu Visual Studio wybierz **Zamknij** przycisku.

#### <a name="to-debug-the-extension"></a>Debugowanie rozszerzeń

1.  Uruchom program Visual Studio z uprawnieniami administratora, a następnie otwórz projekt rozszerzenia. Poniższe kroki odwoływać się do tego wystąpienia programu Visual Studio jako *pierwsze wystąpienie*.

2.  Uruchomić inne wystąpienie programu Visual Studio z uprawnieniami administratora. Poniższe kroki odwoływać się do tego wystąpienia programu Visual Studio jako *drugie wystąpienie*.

3.  Przejdź do pierwszego wystąpienia programu Visual Studio.

4.  Na pasku menu wybierz **debugowania**, **dołączyć do procesu**.

5.  W **dostępne procesy** wybierz *devenv.exe*. Ten wpis odwołuje się do drugiego wystąpienia programu Visual Studio; to wystąpienie chcesz debugować rozszerzenia projektu w.

6.  Wybierz **Attach** przycisku.

     Visual Studio działa projekt rozszerzenia w trybie debugowania.

7.  Przełącz się do drugiego wystąpienia programu Visual Studio.

8.  Utwórz nowy projekt programu SharePoint, który ładuje Twoje rozszerzenie. Na przykład w przypadku debugowania rozszerzenie dla elementów projektu definicji listy utworzyć **definicji listy** projektu.

9. Wykonaj wszelkie kroki są wymagane do testowania kodu rozszerzenia.

10. Po zakończeniu rozszerzenie do debugowania, zamknij drugie wystąpienie programu Visual Studio.

#### <a name="to-remove-the-extension"></a>Aby usunąć rozszerzenia

1.  W programie Visual Studio na pasku menu wybierz **narzędzia**, **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2.  Na liście rozszerzeń, wybierz nazwę rozszerzenia, a następnie wybierz **Odinstaluj** przycisku.

3.  W oknie dialogowym wybierz **tak** przycisk, aby potwierdzić, że chcesz odinstalować rozszerzenia.

4.  Wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.

## <a name="debug-sharepoint-commands"></a>SharePoint — polecenia Debug
 Jeśli chcesz debugować polecenie programu SharePoint, która jest częścią rozszerzeń narzędzi SharePoint, należy dołączyć debugera do *vssphost4.exe* procesu. Jest to proces 64-bitowego hosta, który wykonuje polecenia programu SharePoint. Aby uzyskać więcej informacji dotyczących poleceń programu SharePoint i *vssphost4.exe*, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Aby dołączyć debuger do procesu vssphost4.exe

1.  Uruchom profilowanie rozszerzenie eksperymentalne wystąpienie programu Visual Studio lub prawidłowe wystąpienie programu Visual Studio, postępując zgodnie z instrukcjami.

2.  W wystąpieniu programu Visual Studio debugger, w którym jest uruchomiony na pasku menu, wybierz **debugowania**, **dołączyć do procesu**.

3.  W **dostępne procesy** wybierz *vssphost.exe*.

    > [!NOTE]
    >  Jeśli vssphost.exe nie ma na liście, należy uruchomić *vssphost4.exe* procesów w wystąpieniu programu Visual Studio, w którym są uruchomione rozszerzenia. Zazwyczaj polega to na wykonywanie akcję wywołującą Visual Studio, aby połączyć się z witryną programu SharePoint na komputerze dewelopera. Na przykład Visual Studio rozpoczyna *vssphost4.exe* po rozwinięciu węzła połączenie lokacji (węzła, który zawiera adres URL witryny) w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera**  okna, lub po dodaniu niektórych elementów projektu SharePoint, takich jak **wystąpienia listy** lub **odbiorcy zdarzeń** elementy do projektu programu SharePoint.

4.  Wybierz **Attach** przycisku.

5.  W wystąpieniu programu Visual Studio, która jest debugowana wykonaj kroki, które są wymagane do wykonania polecenia.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Zmodyfikuj wartości rejestru w celu debugowania rozszerzeń narzędzi SharePoint
 Podczas debugowania rozszerzeń narzędzi SharePoint w Visual Studio można zmodyfikować wartości rejestru, aby ułatwić rozwiązywanie problemów z rozszerzeniem. Wartości istnieje w obszarze **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** klucza. Domyślnie te wartości nie istnieje.

 Aby ułatwić rozwiązywanie problemów z wszelkich rozszerzeń narzędzi SharePoint, można utworzyć i ustawić wartość EnableDiagnostics. W poniższej tabeli opisano tę wartość.

|Wartość|Opis|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD, który określa, czy komunikaty diagnostyczne są wyświetlane w **dane wyjściowe** okna.<br /><br /> Aby wyświetlić komunikaty diagnostyczne, ustaw tę wartość 1. Aby zatrzymać wyświetlanie wiadomości, ustaw tę wartość na 0 lub Usuń tę wartość.<br /><br /> Komunikaty, aby zapisać **dane wyjściowe** rozszerzenia narzędzi w oknie programu SharePoint, należy użyć usługi projektu SharePoint. Aby uzyskać więcej informacji, zobacz [przy użyciu usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Jeśli rozszerzenie zawiera polecenie programu SharePoint, można tworzyć i ustaw dodatkowe wartości, aby ułatwić rozwiązywanie problemów z polecenia. W poniższej tabeli opisano te wartości.

|Wartość|Opis|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD, który określa, czy wyświetlać okno dialogowe, które umożliwia dołączanie debugera do *vssphost4.exe* zaraz po jego uruchomieniu. Jest to przydatne, jeśli polecenie, które chcesz debugować jest wykonywane przez vssphost.exe natychmiast po jej uruchomieniu, a nie jest wystarczająco dużo czasu, można ręcznie dołączyć debugera przed wykonaniem polecenia. Aby wyświetlić okno dialogowe *vssphost4.exe* wywołania <xref:System.Diagnostics.Debugger.Break%2A> metody podczas jej uruchamiania.<br /><br /> Aby włączyć to zachowanie, ustaw tę wartość 1. Aby wyłączyć to zachowanie, ustaw tę wartość na 0, lub Usuń tę wartość.<br /><br /> Jeśli ta wartość jest ustawiona na 1, możesz zwiększyć wartość HostProcessStartupTimeout w celu utworzenia wystarczająco dużo czasu, można dołączyć debugera przed Visual Studio oczekuje *vssphost4.exe* sygnalizują, że uruchomiona pomyślnie.|
|ChannelOperationTimeout|REG_DWORD, który określa czas w sekundach, przez Visual Studio czeka na wykonanie polecenia programu SharePoint. Jeśli polecenie nie zostanie wykonane w czasie, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> jest generowany.<br /><br /> Wartość domyślna to 120 sekund.|
|HostProcessStartupTimeout|REG_DWORD, który określa czas w sekundach, że program Visual Studio czeka na *vssphost4.exe* sygnalizują, że uruchomiona pomyślnie. Jeśli *vssphost4.exe* nie można sygnalizować pomyślne uruchomienie w czasie, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> jest generowany.<br /><br /> Wartość domyślna to 60 sekund.|
|MaxReceivedMessageSize|REG_DWORD, który określa maksymalny dozwolony rozmiar w bajtach wiadomości WCF, które są przekazywane między Visual Studio i *vssphost4.exe*.<br /><br /> Wartość domyślna to 1048576 bajtów (1 MB).|
|MaxStringContentLength|REG_DWORD, który określa maksymalny dozwolony rozmiar w bajtach ciągów, które są przekazywane między Visual Studio i *vssphost4.exe*.<br /><br /> Wartość domyślna to 1048576 bajtów (1 MB).|

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie narzędzi SharePoint w Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)