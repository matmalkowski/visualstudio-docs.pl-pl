---
title: "Określ ustawienia domyślne dla wdrożeń w przedsiębiorstwie programu Visual Studio | Dokumentacja firmy Microsoft"
description: "Zasady domeny i inne operacje konfiguracji wdrażania w przedsiębiorstwie programu Visual Studio."
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 11bcc331150b1e1ab9a8058b3538bca411345c19
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Określ ustawienia domyślne dla wdrożeń w przedsiębiorstwie programu Visual Studio

Można ustawić zasady rejestru, które mają wpływ na wdrożenie programu Visual Studio. Te zasady są globalne dla nowego Instalatora i wpływają na:

- Zainstalowaną niektórych pakietów współużytkowane z innymi wersjami lub wystąpień
- Gdzie są buforowane pakietów
- Określa, czy wszystkie pakiety są buforowane

Można ustawić niektóre z tych zasad przy użyciu [opcje wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md), ustaw wartości rejestru na komputerze, lub nawet przekazać je za pomocą zasad grupy w organizacji.

## <a name="registry-keys"></a>Klucze rejestru

Istnieje kilka lokalizacji, w którym można ustawić wartości domyślne przedsiębiorstwa, aby włączyć kontrolę za pomocą zasad grupy lub bezpośrednio w rejestrze. Visual Studio sprawdza kolejno Jeśli ustawiono żadnych zasad organizacji; jak wartość zasad został odnaleziony w poniższej kolejności, pozostałe klucze są ignorowane.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup`(w systemach 64-bitowe)

> [!IMPORTANT]
> Jeśli nie ustawisz `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` klucza i zamiast tego Ustaw jeden z innych kluczy, należy ustawić obu kluczy w 64-bitowych systemach operacyjnych. Ten problem został rozwiązany w przyszłej aktualizacji.

Niektóre wartości rejestru są ustawiane automatycznie po raz pierwszy one są używane jeśli nie jest już skonfigurowane. Daje to gwarancję, że kolejne instaluje używać tych samych wartości. Te wartości są przechowywane w kluczu rejestru drugi `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Można ustawić następujące wartości rejestru:

| **Nazwa** | **Typ** | **Domyślne** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ`lub`REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym manifesty pakietu i, opcjonalnie, ładunki są przechowywane. Jak do odczytu do [wyłączone lub Przenieś pamięć podręczną pakietów](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachowaj ładunków pakietu, nawet po ich zainstalowaniu. W każdej chwili można zmienić wartości. Wyłączenie zasad usuwa żadnych ładunków pakietu w pamięci podręcznej dla tego wystąpienia, napraw lub zmodyfikować. Jak do odczytu do [wyłączone lub Przenieś pamięć podręczną pakietów](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `SharedInstallationPath` | `REG_SZ`lub`REG_EXPAND_SZ` | % ProgramFiles (x86) %\Microsoft Visual Studio\Shared | Katalog, w którym są zainstalowane niektórych pakietów współużytkowane przez wersje wystąpienia programu Visual Studio. Zmień wartość w dowolnym momencie, ale który mają wpływ tylko na przyszłe instaluje. Nie należy przenieść wszystkie produkty już zainstalowane do poprzedniej lokalizacji lub może nie działać prawidłowo. |

> [!IMPORTANT]
> Jeśli zmienisz `CachePath` zasad rejestru po wszelkich instalacji, należy przenieść istniejący pakiet pamięci podręcznej do nowej lokalizacji i sprawdzać, czy jest zabezpieczony, aby `SYSTEM` i `Administrators` mają pełną kontrolę i `Everyone` ma dostęp do odczytu.
> Nie można przenieść istniejący pamięci podręcznej lub zabezpieczanie go może spowodować problemy z przyszłych instaluje.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także

 * [Zainstaluj program Visual Studio](install-visual-studio.md)
 * [Wyłącz lub Przenieś pamięć podręczną pakietów](disable-or-move-the-package-cache.md)
 * [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
