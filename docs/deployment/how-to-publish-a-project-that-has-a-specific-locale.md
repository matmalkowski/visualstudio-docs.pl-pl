---
title: 'Porady: publikowanie projektu o specyficznych ustawieniach regionalnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e67a44efface97c1cbcf0bd96756467268416ee2
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234130"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Porady: publikowanie projektu o specyficznych ustawieniach regionalnych
Nie jest rzadko aplikacji zawiera składniki, które mają różne ustawienia regionalne. W tym scenariuszu czy tworzenia rozwiązania, które ma kilka projektów, a następnie opublikuj oddzielnych projektów dla poszczególnych ustawień regionalnych. W tej procedurze pokazano, jak opublikować pierwszy projekt w rozwiązaniu przy użyciu ustawień regionalnych "PL" przy użyciu makra. Jeśli chcesz wypróbować tę procedurę za pomocą ustawień regionalnych innych niż "en", należy ustawić `localeString` w makrze zgodne z ustawieniami regionalnymi, którego używasz (na przykład "de" lub "de-DE").  
  
> [!NOTE]
>  Korzystając z tego makra, publikowanie Lokalizacja powinna być udział prawidłowy adres URL lub Universal Naming Convention (UNC). Ponadto Internet Information Services (IIS) musi być zainstalowany na tym komputerze. Aby zainstalować usługi IIS, na **Start** menu, kliknij przycisk **Panelu sterowania**. Kliknij dwukrotnie **Dodaj lub usuń programy**. W **Dodaj lub usuń programy**, kliknij przycisk **Dodaj/Usuń składniki systemu Windows**. W **Kreatora składników systemu Windows**, wybierz pozycję **Internet Information Services (IIS)** pole wyboru w **składniki** listy. Następnie kliknij przycisk **Zakończ** aby zamknąć kreatora.  
  
### <a name="to-create-the-publishing-macro"></a>Aby utworzyć publikowania — makro  
  
1.  Aby otworzyć Eksploratora makra w **narzędzia** menu wskaż **makra**, a następnie kliknij przycisk **Explorer makro**.  
  
2.  Utwórz nowy moduł makra. W Eksploratorze makro wybierz **MyMacros**. Na **narzędzia** menu wskaż **makra**, a następnie kliknij przycisk **nowy moduł makro**. Nazwa modułu **PublishSpecificCulture**.  
  
3.  W Eksploratorze makro rozwiń **MyMacros** węzeł, a następnie otwórz **PublishAllProjects** modułu, kliknij go dwukrotnie (lub z **narzędzia** menu wskaż **Makra**, a następnie kliknij przycisk **IDE makra**).  
  
4.  W środowisku IDE makra, Dodaj następujący kod do modułu, po `Import` instrukcji:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certficate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Zamknij makra IDE. Fokus powróci do programu Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Aby opublikować projekt dla ustawień regionalnych  
  
1.  Aby utworzyć projekt aplikacji systemu Windows w języku Visual Basic w **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji systemu Windows** z **Visual Basic** węzła. Nazwij projekt **PublishLocales**.  
  
3.  Kliknij przycisk Form1. W **właściwości** okna, w obszarze **projekt**, zmień **języka** właściwość z **(domyślna)** do **wjęzykuangielskim**. Zmień **tekst** właściwości formularza, aby **MyForm**.  
  
     Należy pamiętać, że zlokalizowanych zasobów biblioteki DLL nie są tworzone aż są potrzebne. Na przykład są one tworzone po zmianie tekstu lub jego formantów formularza po określeniu nowych ustawień regionalnych.  
  
4.  Publikowanie PublishLocales przy użyciu programu Visual Studio IDE.  
  
     W **Eksploratora rozwiązań**, wybierz PublishLocales. Na **projektu** menu, wybierz opcję **właściwości**. W Projektancie projektu na **publikowania** Określ lokalizację publikowania **http://localhost/PublishLocales**, a następnie kliknij przycisk **opublikować teraz**.  
  
     Po wyświetleniu strony publikowania w sieci Web, należy go zamknąć. (W tym kroku należy opublikować projekt, nie trzeba go zainstalować.)  
  
5.  Ponownie opublikować PublishLocales przez wywołanie makra w oknie Wiersz polecenia programu Visual Studio. Aby wyświetlić okno wiersza polecenia na **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **okno polecenia**, lub naciśnij klawisz **Ctrl** + **Alt**+**A**. W oknie wiersza polecenia, wpisz `macros`; funkcja automatycznego uzupełniania będzie zawierają listę dostępnych makr. Wybierz następujące makra, a następnie naciśnij klawisz ENTER:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Gdy proces publikowania zakończy się pomyślnie, zostanie wygenerowany komunikat "Publikuj zakończyło się pomyślnie PublishLocales\PublishLocales.vbproj. Publikowanie języka został "en". " Kliknij przycisk **OK** w oknie komunikatu. Gdy zostanie wyświetlona strona sieci Web publikowanie, kliknij przycisk **zainstalować**.  
  
7.  Szukaj w C:\Inetpub\wwwroot\PublishLocales\en. Powinny pojawić się zainstalowane pliki takie jak manifesty, setup.exe i publikowania strony sieci Web, oprócz zlokalizowana Biblioteka DLL zasobów. (Domyślnie ClickOnce dołącza rozszerzenie .deploy na plików exe i dll, po wdrożeniu można usunąć tego rozszerzenia.)  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Środowisko projektowe makra](http://msdn.microsoft.com/en-us/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Okno Eksploratora — makro](http://msdn.microsoft.com/en-us/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Porady: edytowanie i programowo tworzenia makr](http://msdn.microsoft.com/en-us/6716f820-1feb-48ad-a718-27eb6b473c5a)