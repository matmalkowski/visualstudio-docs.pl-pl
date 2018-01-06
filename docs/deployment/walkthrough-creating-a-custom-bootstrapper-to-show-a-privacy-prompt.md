---
title: "Wskazówki: Tworzenie niestandardowego programu inicjującego wyświetlającego zasad ochrony prywatności Prompt | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 97b5ba379eb715c63e5432b22999e2c4f12bf50d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Wskazówki: tworzenie niestandardowego programu inicjującego wyświetlającego prywatny monit
Można skonfigurować ClickOnce — aplikacje mają być automatycznie aktualizowane, gdy będą dostępne zestawy za pomocą nowszej wersji plików i wersji zestawu. Aby upewnić się, że klienci zgodę na to zachowanie, można wyświetlić monit o prywatności dla nich. Następnie w ich zdecydować, czy można udzielić uprawnienia do aplikacji automatycznej aktualizacji. Jeśli aplikacja nie może automatycznie zaktualizować, nie jest instalowana.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Program Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Tworzenie aktualizacji zgody — okno dialogowe  
 Aby wyświetlić monit o ochronie prywatności, tworzenie aplikacji z pytaniem, czytelnika wyrażenia zgody na automatyczne aktualizacje aplikacji.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Aby utworzyć okno dialogowe zgody  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, kliknij przycisk **Windows**, a następnie kliknij przycisk **WindowsFormsApplication**.  
  
3.  Dla **nazwa**, typ **ConsentDialog**, a następnie kliknij przycisk **OK**.  
  
4.  W Projektancie kliknij formularz.  
  
5.  W **właściwości** Zmień **tekst** właściwości **aktualizacji zgody w oknie dialogowym**.  
  
6.  W **przybornika**, rozwiń węzeł **wszystkich formularzy systemu Windows**, a następnie przeciągnij **etykiety** sterowania do formularza.  
  
7.  W Projektancie kliknij formantu etykiety.  
  
8.  W **właściwości** Zmień **tekst** właściwości w **wygląd** do następującego:  
  
     Sprawdza aplikację, którą zamierzasz zainstalować najnowsze aktualizacje w sieci Web. Klikając "Zgadzam się", należy zezwolić aplikacji, aby sprawdzić i automatyczne instalowanie aktualizacji z Internetu.  
  
9. W **przybornika**, przeciągnij **wyboru** kontroli w środku formularza.  
  
10. W **właściwości** Zmień **tekst** właściwości w **układu** do **zgadzam się**.  
  
11. W **przybornika**, przeciągnij **przycisk** kontrolki do lewej dolnej części formularza.  
  
12. W **właściwości** Zmień **tekst** właściwości w **układu** do **Kontynuuj**.  
  
13. W **właściwości** Zmień **(nazwa)** właściwości w **projekt** do **ProceedButton**.  
  
14. W **przybornika**, przeciągnij **przycisk** formantu prawym dolnym rogu formularza.  
  
15. W **właściwości** Zmień **tekst** właściwości w **układu** do **anulować**.  
  
16. W **właściwości** Zmień **(nazwa)** właściwości w **projekt** do **CancelButton**.  
  
17. W projektancie, kliknij dwukrotnie **zgadzam się** pole wyboru, aby wygenerować CheckedChanged obsługi zdarzeń.  
  
18. W pliku kodu Form1 Dodaj następujący kod obsługi zdarzenia CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Zaktualizować konstruktora klasy, aby wyłączyć **Kontynuuj** przycisk domyślny.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. W pliku kodu Form1 Dodaj następujący kod do zmiennej typu Boolean do śledzenia, jeśli użytkownik zgodził się aktualizacje w trybie online.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. W projektancie, kliknij dwukrotnie **Kontynuuj** przycisk, aby wygenerować obsługi zdarzenia kliknięcia.  
  
22. W pliku kodu Form1, Dodaj następujący kod do obsługi zdarzenia kliknięcia dla **Kontynuuj** przycisku.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. W projektancie, kliknij dwukrotnie **anulować** przycisk, aby wygenerować obsługi zdarzenia kliknięcia.  
  
24. W pliku kodu Form1, Dodaj następujący kod do obsługi zdarzenia kliknięcia dla **anulować** przycisku.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Aktualizuj aplikację do zwraca błąd, jeśli użytkownik końcowy nie zgadza się na aktualizacje w trybie online.  
  
     Visual Basic tylko dla deweloperów:  
  
    1.  W **Eksploratora rozwiązań**, kliknij przycisk **ConsentDialog**.  
  
    2.  Na **projektu** menu, kliknij przycisk **Dodawanie modułu**, a następnie kliknij przycisk **Dodaj**.  
  
    3.  W pliku kodu Module1.vb Dodaj następujący kod.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Na **projektu** menu, kliknij przycisk **właściwości ConsentDialog**, a następnie kliknij przycisk **aplikacji** kartę.  
  
    5.  Usuń zaznaczenie pola wyboru **struktury aplikacji Włącz**.  
  
    6.  W **obiekt uruchomieniowy** menu rozwijanego wybierz **Module1**.  
  
        > [!NOTE]
        >  Wyłączenie struktury aplikacji wyłącza funkcje, takie jak style wizualne XP systemu Windows, zdarzeń aplikacji, ekran powitalny i pojedyncze wystąpienie aplikacji. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Visual C# tylko dla deweloperów:  
  
     Otwórz plik kodu Program.cs i Dodaj następujący kod.  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Na **kompilacji** menu, kliknij przycisk **BuildSolution**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Tworzenie niestandardowy pakiet programu inicjującego  
 Aby wyświetlić wiersz prywatności dla użytkowników końcowych, można utworzyć niestandardowy pakiet programu inicjującego stosowania aktualizacji zgody w oknie dialogowym i dołącz ją jako warunek wstępny we wszystkich aplikacjach ClickOnce.  
  
 W tej procedurze pokazano, jak utworzyć niestandardowy pakiet programu inicjującego, tworząc w następujących dokumentach:  
  
-   Product.xml manifest pliku do opisania zawartości inicjujący.  
  
-   Plik package.xml pliku manifestu do listy lokalizacji specyficznych aspektów pakietu, takich jak parametry i postanowienia licencyjne dotyczące oprogramowania.  
  
-   Dokument postanowienia licencyjne dotyczące oprogramowania.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Krok 1: Można utworzyć katalogu programu inicjującego  
  
1.  Utwórz katalog o nazwie **UpdateConsentDialog** w %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Uprawnienia administracyjne, aby utworzyć ten folder może być konieczne.  
  
2.  W katalogu UpdateConsentDialog utworzyć podkatalogu o nazwie en.  
  
    > [!NOTE]
    >  Utwórz nowy katalog dla poszczególnych ustawień regionalnych. Na przykład można dodać podkatalogi fr i de ustawień regionalnych. Te katalogi zawiera ciągi francuskim i niemieckim i pakiety językowe, jeśli to konieczne.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Krok 2: Aby utworzyć plik manifestu product.xml  
  
1.  Utwórz plik tekstowy o nazwie `product.xml`.  
  
2.  W pliku product.xml Dodaj następujący kod XML. Upewnij się, że nie zastępuj istniejącego kodu XML.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Zapisz plik w katalogu programu inicjującego UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Krok 3: Aby utworzyć plik package.xml manifestu plików i oprogramowania postanowienia licencyjne  
  
1.  Utwórz plik tekstowy o nazwie `package.xml`.  
  
2.  W pliku plik package.xml Dodaj następujący kod XML do definiowania ustawień regionalnych i zawierają postanowienia licencyjne dotyczące oprogramowania. Upewnij się, że nie zastępuj istniejącego kodu XML.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Zapisz plik do en podkatalogu w katalogu programu inicjującego UpdateConsentDialog.  
  
4.  Utwórz dokument o nazwie eula.rtf dla postanowienia licencyjne dotyczące oprogramowania.  
  
    > [!NOTE]
    >  Postanowienia licencyjne dotyczące oprogramowania powinna zawierać informacje dotyczące licencjonowania, żadnych gwarancji, zobowiązań i prawa miejscowego. Te pliki powinny być specyficzne dla ustawień regionalnych, dlatego należy upewnić się, że plik jest zapisywany w formacie, który obsługuje znaki MBCS lub UNICODE. Zapoznaj się dział prawny o treści postanowień licencyjnych dotyczących oprogramowania.  
  
5.  Zapisz dokument w podkatalogu en w katalogu programu inicjującego UpdateConsentDialog.  
  
6.  Jeśli to konieczne, Utwórz nowy plik manifestu plik package.xml i nowy dokument eula.rtf dla postanowienia licencyjne dotyczące oprogramowania dla poszczególnych ustawień regionalnych. Na przykład jeśli utworzono podkatalogi dla ustawień regionalnych fr i de, utworzyć oddzielny plik package.xml pliki manifest i postanowienia licencyjne dotyczące oprogramowania i zapisać je w podkatalogach fr i de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Ustawienie aplikacji zgody aktualizacji jako warunek wstępny  
 W programie Visual Studio można ustawić jako warunek wstępny zgody aktualizacji aplikacji.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Aby ustawić aktualizacji aplikacji zgodę jako warunek wstępny  
  
1.  W **Eksploratora rozwiązań**, kliknij nazwę aplikacji, który chcesz wdrożyć.  
  
2.  Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
3.  Kliknij przycisk **publikowania** , a następnie kliknij przycisk **wymagania wstępne**.  
  
4.  Wybierz **aktualizacji okna dialogowego zgody**.  
  
    > [!NOTE]
    >  Może być konieczne zamknięcie i ponowne otwarcie programu Visual Studio, aby wyświetlić okno dialogowe zgody aktualizacji w oknie dialogowym wymagania wstępne.  
  
5.  Kliknij przycisk **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Tworzenie i testowanie Program instalacyjny  
 Po ustawieniu zgody aktualizacji aplikacji jako warunek wstępny, można wygenerować Instalatora i programu inicjującego dla aplikacji.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Aby utworzyć i przetestować program instalacyjny, nie klikając zgadzam się  
  
1.  W **Eksploratora rozwiązań**, kliknij nazwę aplikacji, który chcesz wdrożyć.  
  
2.  Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
3.  Kliknij przycisk **publikowania** , a następnie kliknij przycisk **opublikować teraz**.  
  
4.  Jeśli dane wyjściowe publikowania nie zostanie uruchomiony automatycznie, przejdź do publikowanych danych wyjściowych.  
  
5.  Uruchom Setup.exe program.  
  
     Program instalacyjny zawiera Umowa licencyjna na aktualizację zgody w oknie dialogowym oprogramowania.  
  
6.  Przeczytaj umowę licencyjną, a następnie kliknij przycisk **Akceptuj**.  
  
     Aplikacja aktualizacji zgody w oknie dialogowym zostanie wyświetlona i zawiera następujący tekst: sprawdza aplikację, którą zamierzasz zainstalować najnowsze aktualizacje w sieci Web. Klikając zgadzam się, należy zezwolić aplikacji, aby wyszukać aktualizacje automatyczne w Internecie.  
  
7.  Zamknij aplikację, lub kliknij przycisk Anuluj.  
  
     Aplikacja zawiera błąd: Wystąpił błąd podczas instalowania składników systemowych dla *ApplicationName*. Instalator nie może kontynuować dopóki wszystkie składniki systemowe zostały pomyślnie zainstalowane.  
  
8.  Kliknij przycisk Szczegóły, aby wyświetlić komunikat o błędzie: Aktualizuj składnik zgody okna dialogowego nie można zainstalować z następujący komunikat o błędzie: "Umowa aktualizacji automatycznych nie została zaakceptowana." Nie można zainstalować następujących składników:-aktualizacji zgody w oknie dialogowym  
  
9. Kliknij przycisk **Zamknij**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Aby utworzyć i przetestować Instalatora, klikając zgadzam się  
  
1.  W **Eksploratora rozwiązań**, kliknij nazwę aplikacji, który chcesz wdrożyć.  
  
2.  Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
3.  Kliknij przycisk **publikowania** , a następnie kliknij przycisk **opublikować teraz**.  
  
4.  Jeśli dane wyjściowe publikowania nie zostanie uruchomiony automatycznie, przejdź do publikowanych danych wyjściowych.  
  
5.  Uruchom Setup.exe program.  
  
     Program instalacyjny zawiera Umowa licencyjna na aktualizację zgody w oknie dialogowym oprogramowania.  
  
6.  Przeczytaj umowę licencyjną, a następnie kliknij przycisk **Akceptuj**.  
  
     Aplikacja aktualizacji zgody w oknie dialogowym zostanie wyświetlona i zawiera następujący tekst: sprawdza aplikację, którą zamierzasz zainstalować najnowsze aktualizacje w sieci Web. Klikając zgadzam się, należy zezwolić aplikacji, aby wyszukać aktualizacje automatyczne w Internecie.  
  
7.  Kliknij przycisk **zgadzam się**, a następnie kliknij przycisk **Kontynuuj**.  
  
     Aby zainstalować uruchamiania aplikacji.  
  
8.  Jeśli zostanie wyświetlone okno dialogowe instalacji aplikacji, kliknij przycisk **zainstalować**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)   
 [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)   
 [Porady: tworzenie manifestu produkt](../deployment/how-to-create-a-product-manifest.md)   
 [Porady: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)   
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)