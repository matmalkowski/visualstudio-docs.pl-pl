---
title: 'Porady: publikowanie aplikacji WPF przy włączonej funkcji stylów wizualnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0111226fdd3de300265f69930b7e9e56f90876c8
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816019"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Porady: publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych
Style wizualne umożliwić wyświetlanie formantów standardowych można zmieniać w oparciu o motywu wybierany przez użytkownika. Domyślnie style wizualne nie są włączone dla aplikacji Windows Presentation Foundation (WPF), dlatego należy je włączyć ręcznie. Włączanie style wizualne dla aplikacji WPF i opublikować rozwiązania spowoduje wystąpienie błędu. W tym temacie opisano sposób rozwiązania tego błędu i proces publikowania aplikacji WPF przy włączonej funkcji stylów wizualnych. Aby uzyskać więcej informacji na temat stylów wizualnych, zobacz [omówienie Visual Style](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Aby uzyskać więcej informacji o komunikat o błędzie, zobacz [Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Usuń błąd i publikowanie rozwiązania, należy wykonać następujące zadania:  
  
-   [Publikowanie rozwiązania bez włączonej funkcji stylów wizualnych](#BKMK_publishsolwovs).  
  
-   [Utwórz plik manifestu](#BKMK_CreateManifest).  
  
-   [Osadzanie pliku manifestu w pliku wykonywalnego opublikowanych rozwiązania](#BKMK_embedmanifest).  
  
-   [Podpisać manifestów aplikacji i wdrażania](#BKMK_signappdeplyman).  
  
 Następnie można przenieść opublikowane pliki do lokalizacji, z którego mają zostać użytkowników końcowych do zainstalowania aplikacji.  
  
##  <a name="BKMK_publishsolwovs"></a> Publikowanie rozwiązania bez włączonej funkcji stylów wizualnych  
  
1.  Upewnij się, że projekt nie ma włączonej funkcji stylów wizualnych. Najpierw sprawdź plik manifestu projektu dla następującego pliku XML. Następnie jeśli istnieje plik XML, ujmij XML znacznika komentarza.  
  
     Domyślnie style wizualne nie są włączone.  
  
    ```xml  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Poniższe procedury pokazują, jak można otworzyć pliku manifestu skojarzone z projektu.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Aby otworzyć pliku manifestu w projektach Visual Basic  
  
    1.  Na pasku menu wybierz **projektu**, * ProjectName ***właściwości**, gdzie *ProjectName* to nazwa projektu WPF.  
  
         Są wyświetlane na stronach właściwości projektu WPF.  
  
    2.  Na **aplikacji** , wybierz pozycję **ustawienia systemu Windows widoku**.  
  
         Otworzy się w pliku app.manifest **edytora kodu**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Aby otworzyć pliku manifestu w projekcie C#  
  
    1.  Na pasku menu wybierz **projektu**, * ProjectName ***właściwości**, gdzie *ProjectName* to nazwa projektu WPF.  
  
         Są wyświetlane na stronach właściwości projektu WPF.  
  
    2.  Na **aplikacji** karcie, zanotuj nazwę wyświetlaną w polu manifestu. Jest to nazwa manifestu, który jest skojarzony z projektu.  
  
        > [!NOTE]
        >  Jeśli **osadzania manifestu z ustawieniami domyślnymi** lub **Utwórz aplikację bez manifestu** są wyświetlane w polu manifestu style wizualne nie są włączone. Jeśli nazwa pliku manifestu jest wyświetlana w polu manifestu, przejdź do następnego kroku tej procedury.  
  
    3.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** ().  
  
         Ten przycisk zawiera wszystkie elementy projektu, w tym te, które zostały wykluczone, które zwykle są ukryte. Plik manifestu jest wyświetlany jako element projektu.  
  
2.  Tworzenie i publikowanie rozwiązania. Aby uzyskać więcej informacji o sposobie publikowania rozwiązania, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Utwórz plik manifestu  
  
1.  Wklej następujący kod XML w pliku Notatnika.  
  
     Plik XML zawiera opis zestawu, który zawiera formanty, które obsługują stylów wizualnych.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  W programie Notatnik, kliknij przycisk **pliku**, a następnie kliknij przycisk **Zapisz jako**.  
  
3.  W **Zapisz jako** okna dialogowego, **Zapisz jako typ** listy rozwijanej wybierz **wszystkie pliki**.  
  
4.  W **nazwę pliku** polu, nazwę pliku i Dołącz **manifest** na końcu nazwy pliku. Na przykład: **themes.manifest**.  
  
5.  Wybierz **Przeglądaj foldery** przycisku Wybierz dowolnego folderu, a następnie kliknij przycisk **zapisać**.  
  
    > [!NOTE]
    >  W pozostałych procedurach założono, że nazwa tego pliku jest **themes.manifest** oraz że plik jest zapisywany w katalogu C:\temp na komputerze.  
  
##  <a name="BKMK_embedmanifest"></a> Osadzanie pliku manifestu w pliku wykonywalnego opublikowanych rozwiązania  
  
1.  Otwórz **wiersz polecenia programu Visual Studio**.  
  
     Aby uzyskać więcej informacji o sposobie otwierania **wiersz polecenia programu Visual Studio**, zobacz [wiersze polecenia](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
    > [!NOTE]
    >  Pozostałe kroki zakładają następujące rozwiązania:  
    >   
    >  -   Nazwa rozwiązania jest **MyWPFProject**.  
    > -   Rozwiązanie znajduje się w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      Rozwiązania została opublikowana do następującego katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   Najnowszą wersję plików opublikowanej aplikacji znajduje się w następującym katalogu: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Nie trzeba używać nazwy lub lokalizacji katalogu opisane powyżej. Nazwy i lokalizacje opisane powyżej są używane tylko w celu zilustrowania kroki wymagane do opublikowania rozwiązania.  
  
2.  W wierszu polecenia należy zmienić ścieżkę do katalogu, który zawiera najnowszą wersję plików opublikowanej aplikacji. W poniższym przykładzie pokazano, w tym kroku.  
  
    ```  
cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  W wierszu polecenia Uruchom następujące polecenie, aby osadzić pliku manifestu w plik wykonywalny aplikacji.  
  
    ```
    mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> Podpisać manifestów aplikacji i wdrażania  
  
1.  W wierszu polecenia Uruchom następujące polecenie, aby usunąć `.deploy` rozszerzenia pliku wykonywalnego w bieżącym katalogu.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  W tym przykładzie przyjęto założenie, że tylko jeden plik ma `.deploy` rozszerzenia pliku. Upewnij się, że zmiany nazwy wszystkich plików w tym katalogu, które mają `.deploy` rozszerzenia pliku.  
  
2.  W wierszu polecenia Uruchom następujące polecenie, aby podpisać manifest aplikacji.  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  W tym przykładzie założono podpisywania manifestu przy użyciu `.pfx` pliku projektu. Jeśli nie są podpisywanie manifestu, można pominąć `-cf` parametr, który jest używany w tym przykładzie. Jeśli tworzysz manifest przy użyciu certyfikatu, który wymaga hasła, określ `-password` opcji (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3.  W wierszu polecenia Uruchom następujące polecenie, aby dodać `.deploy` rozszerzenia nazwy pliku, którego nazwa została zmieniona w poprzednim kroku tej procedury.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  W tym przykładzie przyjęto założenie, że tylko jeden plik ma `.deploy` rozszerzenia pliku. Upewnij się, że zmiany nazwy wszystkich plików w tym katalogu, który miał poprzednio `.deploy` rozszerzenia nazwy pliku.  
  
4.  W wierszu polecenia Uruchom następujące polecenie, aby podpisać manifest wdrażania.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  W tym przykładzie założono podpisywania manifestu przy użyciu `.pfx` pliku projektu. Jeśli nie są podpisywanie manifestu, można pominąć `-cf` parametr, który jest używany w tym przykładzie. Jeśli tworzysz manifest przy użyciu certyfikatu, który wymaga hasła, określ `-password` opcji, jak w poniższym przykładzie:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
 Po wykonaniu tych kroków można przenieść opublikowane pliki do lokalizacji, z którego mają zostać użytkowników końcowych do zainstalowania aplikacji. Jeśli planujesz zaktualizować rozwiązania często, można przenieść te polecenia do skryptu i uruchom skrypt w każdym publikowaniu nowej wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z określonymi błędami wdrożeń technologii ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Omówienie style wizualne](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Włączanie style wizualne](https://msdn.microsoft.com/library/bb773175.aspx)   
 [Wiersze polecenia](/dotnet/framework/tools/developer-command-prompt-for-vs)