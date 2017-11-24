---
title: "Usunięcie programu Visual Studio 2017 | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak usunąć Visual Studio, krok po kroku."
ms.custom: 
ms.date: 09/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: heaths
manager: erickn
ms.openlocfilehash: 3c859b0023c9ea282afde837b17b7c93f3f4fbd7
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="remove-visual-studio"></a>Usuwanie programu Visual Studio

Jeśli wystąpi błąd krytyczny i nie można naprawić lub odinstaluj program Visual Studio, można uruchomić `InstallCleanup.exe` narzędzie do usuwania plików instalacyjnych i informacji o produkcie. To narzędzie ma zostać wykonane w ostateczności, jeśli napraw lub odinstaluj błędów i może odinstalować funkcje z innych instalacji programu Visual Studio lub innych produktów, które wymagają naprawy.

W poniższych instrukcjach można uruchomić narzędzie z różnych przełączników wiersza polecenia z następujące działania:

| Przełącznik | Zachowanie |
| ------ | -------- |
| `-i`   | Ta opcja jest domyślnie Jeśli przełączników nie została przekazana i usuwa tylko głównego katalogu i produktu informacje o instalacji. To zachowanie jest preferowana, jeśli planujesz ponownie zainstalować tę samą wersję, po uruchomieniu `InstallCleanup.exe` narzędzia. |
| `-f`   | Określenie tego przełącznika usuwa katalog główny instalacji, informacje o produkcie i większości innych funkcji zainstalowane poza katalog instalacyjny, która może być współużytkowana z innych instalacji programu Visual Studio lub innych produktów. To zachowanie jest preferowana, jeśli zamierzasz usunąć Visual Studio bez ponowną instalację później. |

1. Zamknij Instalatora programu Visual Studio.
2. Otwórz wiersz polecenia administratora. Aby otworzyć wiersz polecenia administratora, wykonaj następujące kroki:
   * Na **Start** menu, kliknij przycisk **Uruchom** (Start + R).
   * Typ **cmd**.
   * Kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.
3. Wpisz pełną ścieżkę `InstallCleanup.exe` narzędzia i niezależnie od przełącznika wiersza polecenia, które chcesz przekazać. Domyślnie ścieżkę narzędzia następująco:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Jeśli nie znajdziesz `InstallCleanup.exe` w katalogu Instalator programu Visual Studio — zawsze znajdujący się w `%ProgramFiles(x86)%\Microsoft Visual Studio` — postępuj zgodnie z instrukcjami, aby [zainstalować program Visual Studio](install-visual-studio.md) i po wyświetleniu ekranu wyboru obciążenia Zamknij okna i wykonaj poprzednie kroki ponownie.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także
* [Zainstaluj program Visual Studio 2017 r.](install-visual-studio.md)
* [Aktualizacja programu Visual Studio 2017 r.](update-visual-studio.md)
* [Modyfikowanie Visual Studio 2017 r.](modify-visual-studio.md)
* [Odinstaluj program Visual Studio 2017 r.](uninstall-visual-studio.md)
