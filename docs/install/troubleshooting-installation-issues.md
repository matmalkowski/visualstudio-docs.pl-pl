---
title: Rozwiązywanie problemów z instalacją | Dokumentacja firmy Microsoft
description: Czasami może wystąpienia problemów. Jeśli z instalacją programu Visual Studio lub uaktualnienie nie powiedzie się, może pomóc tej strony.
ms.date: 11/21/2017
ms.technology:
- vs-acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 346ee102b7c6db1494b831cd03a1e68632bbda38
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Rozwiązywanie problemów instalacji i uaktualniania programu Visual Studio 2017 r.

## <a name="symptoms"></a>Symptomy
Podczas próby zainstalowania lub aktualizacji programu Visual Studio 2017 kończy się niepowodzeniem.

## <a name="workaround"></a>Obejście
Aby obejść ten problem, wykonaj następujące kroki.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 — Sprawdź, czy ten problem występuje znany problem
Brak niektórych znanych problemów z programem Instalator programu Visual Studio, które firma Microsoft pracuje rozwiązanie problemu. Aby sprawdzić, czy istnieje obejście tego problemu, sprawdź [sekcji Znane problemy z naszym informacje o wersji](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#known-issues).

### <a name="step-2---check-with-the-developer-community"></a>Krok 2 — wyboru z społeczność deweloperów
Wyszukaj użytkownika komunikat o błędzie z [Visual Studio Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html). Rozwiązanie tego problemu może udokumentowanych innych członków społeczności.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 3 — Usuń katalog Instalator programu Visual Studio, aby rozwiązać problemy z uaktualnianiem
Program inicjujący Instalator programu Visual Studio jest minimalnym pliku wykonywalnego lekki, który instaluje reszty Instalator programu Visual Studio. Usuwanie plików Instalator programu Visual Studio i następnie ponowne uruchomienie inicjujący może rozwiązać niektóre błędy aktualizacji.

>[!NOTE]
Wykonaj następujące czynności ponownie instaluje pliki Instalator programu Visual Studio i resetuje metadanych instalacji.

1. Zamknij Instalatora programu Visual Studio.
2. Usuń katalog Instalator programu Visual Studio. Zazwyczaj jest katalog `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Uruchom program inicjujący Instalator programu Visual Studio. Program inicjujący można znaleźć w folderze pobrane przy użyciu nazwy pliku, który następuje `vs_[Visual Studio edition]__*.exe` wzorca. Nie można znaleźć tej aplikacji, możesz pobrać inicjujący, przechodząc do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/) strony i klikając **Pobierz** używanej wersji programu Visual Studio. Uruchom plik wykonywalny do zresetowania metadanych instalacji.
4. Spróbuj zainstalować lub aktualizacji programu Visual Studio. Jeśli Instalator zakończy się niepowodzeniem, przejdź do następnego kroku.

### <a name="step-4---report-a-problem"></a>Krok 4 — Zgłoś problem
W niektórych sytuacjach, takich jak powiązane z uszkodzone pliki problemów może być konieczne rozważyć w przypadku przez:

1. Zbieranie dzienników Instalatora. Zobacz [jak uzyskać dzienniki instalacji programu Visual Studio](#how-to-get-the-visual-studio-installation-logs) szczegółowe informacje.
2. Otwórz Instalator programu Visual Studio, a następnie kliknij przycisk **zgłosić problem** aby otworzyć narzędzie Visual Studio opinii.
![Można karty, aby przycisk Podaj opinię, aby otworzyć narzędzie opinii](media/report-a-problem.png)
3. Przypisz tytuł raport o problemie i podaj odpowiednie dane. Kliknij przycisk **dalej** można przejść do **załączników** sekcji, a następnie dołącz plik dziennika wygenerowany (zazwyczaj plik jest w `%TEMP%\vslogs.zip`).
4. Kliknij przycisk **dalej** Przejrzyj raport o błędach, a następnie kliknij przycisk **przesyłania**.

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Krok 5. Uruchom InstallCleanup.exe do usunięcia plików instalacyjnych
W ostateczności można [usuwanie programu Visual Studio](remove-visual-studio.md) usunąć wszystkie pliki instalacyjne i informacji o produkcie.

1. Postępuj zgodnie z instrukcjami [usunięcie programu Visual Studio](remove-visual-studio.md).
2. Uruchom ponownie program inicjujący opisany w [krok 3 — Usuń katalog Instalator programu Visual Studio, aby rozwiązać problemy z uaktualnianiem](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Spróbuj zainstalować lub aktualizacji programu Visual Studio.

### <a name="step-6---contact-us-optional"></a>Krok 6 — skontaktuj się z nami (opcjonalnie)
Jeśli żadne inne czynności nie zezwalać na pomyślnie zainstalować, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

## <a name="how-to-troubleshoot-an-offline-installer"></a>Jak rozwiązywać problemy z Instalatora w trybie offline
Oto tabelę znane problemy i rozwiązania niektórych podczas instalowania z układu lokalne, które mogą pomóc.

| Problem       | Element                   | Rozwiązanie |
| ----------- | ---------------------- | -------- |
| Użytkownicy nie mieli dostępu do plików. | uprawnienia (kontroli dostępu ACL) | Upewnij się, że dostosowanie uprawnień (kontroli dostępu ACL), dzięki czemu przyznają dostęp do odczytu do innych użytkowników *przed* udostępnianie instalację w trybie offline. |
| Nowe obciążenia, składników i językach uniemożliwić instalację.  | `--layout`  | Upewnij się, że masz dostęp do Internetu, jeśli został zainstalowany z częściowa układu, wybierz obciążeń, składniki oraz języki, które nie zostały pobrane wcześniej w tym układzie częściowej. |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Jak uzyskać dzienniki instalacji programu Visual Studio
Dzienniki instalacji są wymagane w rozwiązywaniu większości problemów instalacji. Po przesłaniu problemu za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) w Instalatorze programu Visual Studio, te dzienniki są automatycznie uwzględnione w raporcie.

Jeśli zamierzasz zgłosić Support firmy Microsoft, może być konieczne podanie tych dzienników instalacji przy użyciu [programu Microsoft Visual Studio i .NET Framework dziennika kolekcji narzędzia](https://aka.ms/vscollect). Narzędzie do zbierania dzienników zbiera dzienniki Instalatora wszystkie składniki zainstalowane przez Visual Studio 2017 r, łącznie z .NET Framework, zestaw Windows SDK i programu SQL Server. Ponadto zbiera informacje o komputerze, Instalator Windows spisu i informacji dziennika zdarzeń systemu Windows, Instalator programu Visual Studio, Instalator systemu Windows i przywracanie systemu.

Aby zebrać dzienniki:

1. [Pobierz narzędzie](https://aka.ms/vscollect).
2. Otwórz administracyjny wiersz polecenia.
3. Uruchom `Collect.exe` z katalogu, w którym zapisano narzędzie.
4. Znajdź powstałe w ten sposób `vslogs.zip` plików w sieci `%TEMP%` katalogu, na przykład `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Narzędzie musi działać dla tego samego konta użytkownika, która była uruchamiana instalacja nie powiodła się. Jeśli używasz narzędzia z innego konta użytkownika, należy ustawić `–user:<name>` opcję, aby określić konto użytkownika, w którym zostało uruchomione instalacja nie powiodła się. Uruchom `Collect.exe -?` z wiersza polecenia administratora, aby uzyskać dodatkowe informacje opcje i użycia.

## <a name="more-support-options"></a>Dodatkowe opcje pomocy technicznej

Jeśli żadne inne czynności nie zezwalać na pomyślnie zainstalować, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka dodatkowych opcji:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Wymaga to [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Usunięcie programu Visual Studio 2017 r.](remove-visual-studio.md)
