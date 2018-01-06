---
title: "Rozwiązywanie problemów z wdrażaniem rozwiązań Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
ms.assetid: 2206aeb6-44b3-4786-ba99-9c7dad5cce7c
caps.latest.revision: "74"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a778aa9e257773ca186bba8b99d5e426f8f26aed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-office-solution-deployment"></a>Rozwiązywanie problemów z wdrażaniem rozwiązań Office
  Ten temat zawiera informacje dotyczące rozwiązywania typowych problemów, które mogą wystąpić podczas wdrażania rozwiązań pakietu Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshooting-office-solutions-by-using-the-event-viewer"></a>Rozwiązywanie problemów z rozwiązań pakietu Office za pomocą Podglądu zdarzeń  
 Możesz użyć Podglądu zdarzeń w systemie Windows można wyświetlić komunikaty o błędach, które są przechwytywane przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] po zainstalowaniu lub odinstalowaniu rozwiązań pakietu Office. Te komunikaty z Rejestratora zdarzeń służy do rozwiązywania instalacji i problemy z wdrażaniem. Aby uzyskać więcej informacji, zobacz [rejestrowania zdarzeń dla rozwiązań pakietu Office](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="changing-the-assembly-name-causes-conflicts"></a>Zmiana nazwy zestawu powoduje konflikt  
 Jeśli zmienisz **nazwy zestawu** wartość w **aplikacji** strony **projektanta projektu** po wdrożeniu już rozwiązania, publikowania narzędzi spowoduje jej modyfikacji Pakiet instalacyjny mieć jeden plik Setup.exe i dwa manifesty wdrożenia. W przypadku wdrażania dwa pliki manifestu, mogą wystąpić następujące warunki:  
  
-   Jeśli użytkownik końcowy instaluje obie wersje, aplikacja zostanie załadowany zarówno dodatków VSTO.  
  
-   Jeśli dodatku VSTO została zainstalowana przed zmianą nazwy zestawu, użytkownik końcowy nigdy nie będzie otrzymywać aktualizacje.  
  
 Aby uniknąć tych warunków, nie należy zmieniać tego rozwiązania **nazwy zestawu** wartość po wdrożeniu rozwiązania.  
  
## <a name="checking-for-updates-takes-a-long-time"></a>Sprawdzanie dostępności aktualizacji trwa zbyt długo  
 Visual Studio 2010 Tools for Office Runtime zawiera wpis rejestru, który administratorzy mogą używać, aby ustawić wartość limitu czasu pobierania manifestów i rozwiązania.  
  
#### <a name="to-set-the-time-out-value"></a>Aby ustawić wartość limitu czasu  
  
1.  W rejestrze przejdź do następującego klucza:  
  
     HKEY_CURRENT_USER\Software\Microsoft\VSTA  
  
2.  W **AddInTimeout** podkluczy, należy ustawić wartość limitu czasu w milisekundach.  
  
     Jeśli **AddInTimeout** podklucz nie istnieje, utwórz go jako wartość typu DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Nie można zaktualizować lub opublikować w sieciowym udziale plików  
 Rozwiązań pakietu Office, które znajdują się w sieciowym udziale plików może być wyświetlany komunikat mylących podczas aktualizacji, jeśli plik Setup.exe rozwiązania jest zablokowane w procesie, gdy aktualizacja jest publikowana. Powiedzieć poniższy komunikat: "nie można dodać"setup.exe"w sieci Web. Plik setup.exe już istnieje w tej witrynie sieci Web."  
  
 Aby zapobiec blokowania plików, należy wybrać udziału tylko do odczytu dla użytkowników końcowych. Jednak w przypadku dokumentów w udziale, one również staną się tylko do odczytu dla użytkowników końcowych.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Nie są zainstalowane wstępnie wymagane składniki pakietu Microsoft Office  
 .NET Framework, można dodać [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]i podstawowe zestawy międzyoperacyjne pakietu Office do pakiet Instalatora jako wymagań wstępnych, które zostały wdrożone za pomocą rozwiązania do pakietu Office. Aby uzyskać informacje o sposobie instalowania podstawowe zestawy międzyoperacyjne, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) i [porady: Zainstaluj Office podstawowe zestawy międzyoperacyjne](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publishing-using-localhost-can-cause-installation-problems"></a>Publikowanie za pomocą "Localhost" może spowodować problemy z instalacją  
 Gdy używasz "http://localhost" jako lokalizację publikowania lub instalacji rozwiązań na poziomie dokumentu, **Kreator publikowania** nie konwertuje ciąg na nazwę komputera prawdziwe. W takim przypadku rozwiązanie należy zainstalować na komputerze dewelopera. Aby można było wdrożonej rozwiązań usług IIS na komputerze dewelopera, należy użyć pełni kwalifikowanej nazwy dla wszystkich lokalizacji FTP-HTTP/HTTPS zamiast localhost.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Pamięci podręcznej zestawów są ładowane zamiast aktualizowane zestawy  
 Fusion, moduł ładujący zestawu .NET Framework ładuje buforowaną kopię zestawy po ścieżce danych wyjściowych projektu znajduje się w sieciowym udziale plików, zestaw jest podpisany przy użyciu silnej nazwy i wersji zestawu dostosowania nie zmieniają się. Jeśli aktualizacja zestawu, który spełnia te warunki, aktualizacja nie będzie dłużej wyświetlane przy następnym uruchomieniu projektu, ponieważ jest załadowana kopia pamięci podręcznej.  
  
 Visual Studio można skonfigurować tak, aby Fusion pobierze zestawy zawsze uruchamiany projektu.  
  
#### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Aby pobrać zestawów, zamiast ładowania zbuforowane kopie  
  
1.  Na pasku menu wybierz **projektu**, *ProjectName***właściwości**.  
  
2.  Na **aplikacji** wybierz pozycję **informacji o zestawie**.  
  
3.  W pierwszym **wersja zestawu** Wprowadź znak gwiazdki (\*), a następnie wybierz pozycję **OK** przycisku.  
  
 Po zmianie wersji zestawu, możesz zarejestrować używanemu zestawowi silną nazwą, a Fusion pobierze najnowszą wersję dostosowań.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-aret-us-ascii"></a>Instalacja nie powiedzie się, jeśli identyfikator URI zawiera znaki tego Are't US ASCII  
 Podczas publikowania rozwiązania do pakietu Office lokalizacji FTP-HTTP/HTTPS, ścieżka nie może zawierać dowolne znaki Unicode, których nie ma w US-ASCII. Takie znaki może spowodować niespójne działanie Instalatora. Ścieżki instalacji, należy użyć znaków US-ASCII.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Podczas publikowania i zainstalować na komputerze dewelopera rozwiązanie zostanie wyświetlony monit, aby ręcznie odinstalować  
 Podczas kompilowania rozwiązania do pakietu Office, wersja wbudowanych automatycznie jest zarejestrowany. Jeśli został wcześniej publikowane i nie zostały zainstalowane na tym samym rozwiązaniu na komputerze deweloperskim [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wykrywa, że ścieżki instalacji dla opublikowanej wersji i wbudowanych wersji różnią się po rozwiązaniu obok odbudować lub opublikowane. Komunikat o błędzie informujący, "nie można zainstalować dostosowań, ponieważ aktualnie jest zainstalowana inna wersja nie może zostać uaktualnione z tej lokalizacji." Klucze rejestru są aktualizowane przy każdym rozwiązanie zostanie odtworzony. W związku z tym przed publikowania, debugować ani uruchamiać nowej wersji należy odinstalować poprzednią wersję.  
  
 Aby zapobiec wyświetlaniu wiadomości, Utwórz kolejne konto użytkownika na komputerze deweloperskim, aby przetestować wdrożenie. Alternatywnie można odinstalować tę wersję z listy zainstalowanych programów na komputerze, aby obok publikowania, debugowanie lub ponownie skompiluj rozwiązanie.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nieprzechwycony wyjątek lub metody nie można odnaleźć błąd podczas instalowania rozwiązania  
 Po zainstalowaniu rozwiązań pakietu Office, otwierając manifest rozmieszczenia (plik .vsto), mogą pojawić się Office aplikacji, dokumentu lub skoroszyt, komunikaty o błędach dla następujących warunków:  
  
-   Nie znaleziono metody.  
  
-   Missingmethodexception —.  
  
-   Nieprzechwycony wyjątek.  
  
 Aby zapobiec te komunikaty o błędach, należy zainstalować rozwiązania, uruchamiając Instalatora.  
  
 Po zainstalowaniu rozwiązania bez konieczności uruchamiania programu instalacyjnego Instalatora nie sprawdzaj lub instalowanie wymagań wstępnych. Program instalacyjny sprawdza poprawną wersję wymagania wstępne i instaluje je w razie potrzeby.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest kluczy rejestru dla dodatków zmiany po utworzeniu projektu programu InstallShield Limited Edition  
 Klucz rejestru manifestu, który jest częścią Instalatora dodatku VSTO programu czasami zmiany z .vsto aby. dll.manifest podczas kompilowania projektu InstallShield Limited Edition.  
  
 Aby obejść ten problem, Utwórz projekt InstallShield Limited Edition w różnych rozwiązaniach lub użyj CompanyName.AddinName jako wartość klucza rejestru, który zawiera nazwę dodatku VSTO.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Instalator ClickOnce dla rozwiązań pakietu Office nie instaluje podstawowe zestawy międzyoperacyjne  
 Po uruchomieniu programu instalacyjnego, który tworzy ClickOnce dla rozwiązań pakietu Office, Instalator podstawowe zestawy międzyoperacyjne pakietu Office (PIAs) jest uruchamiana tylko wtedy, gdy PIAs nie są już zainstalowane.  
  
 Jeśli Instalator nie instaluje PIAs poprawnie, zainstaluj je ręcznie, uruchamiając plik Instalatora o nazwie o2007pia.msi z katalogu instalacyjnego.  
  
## <a name="reinstalling-office-solutions-causes-an-argument-out-of-range-exception"></a>Ponowna instalacja rozwiązań pakietu Office powoduje, że Argument wyjątek poza zakresem  
 Podczas ponownej instalacji rozwiązania do pakietu Office, <xref:System.ArgumentOutOfRangeException> wyjątku może pojawić się następujący komunikat o błędzie: określony argument jest spoza zakresu prawidłowych wartości.  
  
 Ta sytuacja występuje, jeśli różni się małych i wielkich liter adresu URL dla lokalizacji instalacji. Na przykład ten błąd pojawią się po zainstalowaniu rozwiązania do pakietu Office z [http://fabrikam.com/ExcelSolution.vsto](http://fabrikam.com/ExcelSolution.vsto) po raz pierwszy, a następnie użyć [http://fabrikam.com/excelsolution.vsto](http://fabrikam.com/excelsolution.vsto) po raz drugi.  
  
 Aby zapobiec wyświetlaniu komunikatu, należy użyć tej samej wielkości liter podczas instalowania rozwiązań pakietu Office.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Nie można zainstalować rozwiązania ClickOnce, otwierając Manifest wdrażania w sieci Web  
 Użytkownicy mogą instalować rozwiązań pakietu Office, otwierając manifest wdrażania w sieci Web. Jednak niektóre instalacje programu Internetowe usługi informacyjne (IIS) blokuje .vsto rozszerzenie nazwy pliku. Należy zdefiniować typu MIME w usługach IIS przed użyciem go do wdrożenia rozwiązania pakietu Office.  
  
 Aby dowiedzieć się, jak zdefiniować typu MIME w usługach IIS 6, zobacz [Konfigurowanie typów MIME (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Aby dowiedzieć się, jak zdefiniować typu MIME w usługach IIS 7, zobacz [Dodawanie typu MIME (program IIS7).](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Ustaw rozszerzenie **.vsto** i typ MIME do **application/x-ms-vsto**.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  