---
title: Zainstaluj certyfikaty wymagane do instalacji w trybie offline program Visual Studio | Dokumentacja firmy Microsoft
description: "W tym artykule opisano kroki niezbędne do zainstalowania certyfikatów dla programu Visual Studio instalacji w trybie offline"
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: timsneath
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4d462120e7b51551ca7f15cc2d23387824a1f9f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Zainstaluj certyfikaty wymagane do instalacji w trybie offline program Visual Studio

Program Visual Studio jest przeznaczony głównie do zainstalowania na komputerze z podłączonego do Internetu, ponieważ wiele składników są regularnie aktualizowane. Jednak pewne dodatkowe kroki, jest można wdrożyć w środowisku Visual Studio, gdzie działającego połączenia internetowego jest niedostępny.

Aparat Instalatora programu Visual Studio instaluje tylko zawartości, który jest zaufany. Robi to poprzez sprawdzenie sygnatur Authenticode zawartości pobierany i sprawdzanie, czy cała zawartość jest zaufany, przed zainstalowaniem. Dzięki temu środowiska przed atakami gdzie zostanie naruszony lokalizacji pobierania. Instalator wymaga kilka standardowych główny firmy Microsoft i certyfikaty pośrednie są zainstalowane program Visual Studio i w górę do daty na komputerze użytkownika. Jeśli komputer został zachowany na bieżąco z usługą Windows Update, certyfikaty podpisywania zwykle są aktualne. Jeśli komputer jest połączony z Internetem, podczas instalacji programu Visual Studio może odświeżyć certyfikaty w razie potrzeby do weryfikowania podpisów plików. Jeśli komputer jest w trybie offline, certyfikaty muszą być odświeżane w inny sposób.

## <a name="how-to-refresh-certificates-when-offline"></a>Jak odświeżyć certyfikatów w trybie offline

Dostępne są trzy opcje do instalowania lub aktualizowanie certyfikatów w środowisku w trybie offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Opcja 1 — ręcznie instalować certyfikaty z folderu układu

Podczas tworzenia układu sieci wymagane certyfikaty są pobierane do folderu certyfikatów. Następnie można ręcznie zainstalować certyfikaty dwukrotnie każdy plik certyfikatu, a następnie klikając polecenie za pomocą Kreatora Menedżera certyfikatów. Jeśli pojawi się monit o podanie hasła, pozostaw to pole puste.

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Opcja 2 — rozpowszechniania zaufanych certyfikatów głównych certyfikatów w środowisku przedsiębiorstwa

Dla przedsiębiorstw mających maszyny w trybie offline, które nie mają najnowszego certyfikatów głównych, administrator może użyć zgodnie z instrukcjami na [Konfigurowanie zaufanych certyfikatów głównych i certyfikatów niedopuszczalne](https://technet.microsoft.com/library/dn265983.aspx) strony, aby je aktualizować.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Opcja 3 - instalacji certyfikatów jako część wdrożenia przy użyciu skryptu programu Visual Studio

Jeśli skrypt jest wykonywany wdrożenia programu Visual Studio w środowisku w trybie offline na klienckich stacjach roboczych, powinien wykonaj następujące czynności:

1. Kopiuj [Certificate Manager — narzędzie](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) w udziale instalacji (na przykład \\server\share\vs2017). Certmgr.exe nie jest dołączana jako część systemu Windows, ale jest dostępna jako część [zestaw Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Utwórz plik wsadowy za pomocą następujących poleceń:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Wdróż plik wsadowy do klienta. To polecenie należy uruchomić z procesów z podwyższonym poziomem uprawnień.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Co to są pliki certyfikatów w folderze certyfikatów?

Trzy. Pliki p12, w tym folderze każdego zawierają certyfikatu pośredniego i certyfikatu głównego. Większość systemów, które są aktualne z usługą Windows Update ma już zainstalowane te certyfikaty.

* **ManifestSignCertificates.p12** zawiera:
    * Certyfikat pośredniego: **2011 PCA podpisywania kodu firmy Microsoft**
        * Nie jest wymagane. Umożliwia zwiększenie wydajności w niektórych scenariuszach, jeśli jest obecny.
    * Certyfikat główny: **Microsoft główny certyfikat urzędu 2011**
        * Wymagany w systemach Windows 7 z dodatkiem Service Pack 1, które nie mają zainstalowane najnowsze aktualizacje systemu Windows.
* **ManifestCounterSignCertificates.p12** zawiera:
    * Certyfikat pośredniego: **Microsoft sygnatury czasowej PCA 2010**
        * Nie jest wymagane. Umożliwia zwiększenie wydajności w niektórych scenariuszach, jeśli jest obecny.
    * Certyfikat główny: **Microsoft główny certyfikat urzędu 2010**
        * Wymagany w przypadku systemów Windows 7 z dodatkiem Service Pack 1, które nie mają zainstalowane najnowsze aktualizacje systemu Windows.
* **Vs_installer_opc. SignCertificates.p12** zawiera:
    * Certyfikat pośredniego: **PCA podpisywania kodu firmy Microsoft**
        * Wymagane we wszystkich systemach. Należy pamiętać, że systemy dla wszystkich aktualizacji z witryny Windows Update nie mogą mieć tego certyfikatu.
    * Certyfikat główny: **główny urząd certyfikacji firmy Microsoft**
        * Wymagany. Ten certyfikat jest dostarczany z komputerów z systemami Windows 7 lub nowszy.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Dlaczego są certyfikaty z folderu certyfikaty nie są instalowane automatycznie?

Podpis zostanie zweryfikowany w środowisku, w trybie online, interfejsów API systemu Windows są używane do pobierania i Dodaj certyfikaty do systemu. Weryfikacja, czy certyfikat jest zaufany i mogą za pomocą ustawień administracyjnych występuje w trakcie tego procesu. Ten proces sprawdzania poprawności nie może wystąpić w środowiskach najbardziej w trybie offline. Ręczne instalowanie certyfikatów umożliwia Administratorzy przedsiębiorstwa certyfikaty były zaufanych i spełnia zasady zabezpieczeń organizacji.

## <a name="checking-if-certificates-are-already-installed"></a>Sprawdzanie, czy certyfikaty są już zainstalowane

Jednym ze sposobów sprawdzenia instalowania systemu jest wykonanie następujących czynności:
1. Uruchom **mmc.exe**.<br/>
  a. Kliknij plik, a następnie wybierz **Dodaj/Usuń przystawkę**.<br/>
  b. Kliknij dwukrotnie **certyfikaty**, wybierz pozycję **konto komputera**, a następnie kliknij przycisk **dalej**.<br/>
  c. Wybierz **komputera lokalnego**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  d. Rozwiń węzeł **certyfikaty (komputer lokalny)**.<br/>
  e. Rozwiń węzeł **zaufane główne urzędy certyfikacji**, a następnie wybierz **certyfikaty**.<br/>
    * Sprawdź certyfikaty główne na potrzeby tej listy.<br/>

   f. Rozwiń węzeł **pośrednie urzędy certyfikacji**, a następnie wybierz **certyfikaty**.<br/>
    * Sprawdź tę listę pod kątem wymagane certyfikaty pośrednie.<br/>

2. Kliknij plik, a następnie wybierz **Dodaj/Usuń przystawkę**.<br/>
  a. Kliknij dwukrotnie **certyfikaty**, wybierz pozycję **Moje konto użytkownika**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**.<br/>
  b. Rozwiń węzeł **Certyfikaty — bieżący użytkownik**.<br/>
  c. Rozwiń węzeł **pośrednie urzędy certyfikacji**, a następnie wybierz **certyfikaty**.<br/>
    * Sprawdź tę listę pod kątem wymagane certyfikaty pośrednie.<br/>

Jeśli nazwy certyfikatów nie były w **wystawiony** kolumn, musi być zainstalowany.  Jeśli certyfikat pośredniego była tylko w **bieżącego użytkownika** certyfikatu pośredniego przechowywania, wówczas jest dostępne tylko dla użytkownika, który jest zalogowany. Może być konieczne zainstalowanie go dla innych użytkowników.

## <a name="install-visual-studio"></a>Zainstaluj program Visual Studio

Po zainstalowaniu certyfikatów, wdrażania programu Visual Studio można kontynuować, korzystając z instrukcji z [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) sekcji "Tworzenie instalacji sieciowej programu Visual Studio" strona.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także
* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
