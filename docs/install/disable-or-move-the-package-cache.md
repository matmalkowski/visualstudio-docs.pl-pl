---
title: "Wyłącz lub Przenieś pamięć podręczną pakietów | Dokumentacja firmy Microsoft"
description: "Wyłączanie, włączanie lub przenieść pamięć podręczną pakietów dla wdrożeń programu Visual Studio."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 768446797558dec103927f251867ab78cd3edf0a
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="disable-or-move-the-package-cache"></a>Wyłącz lub Przenieś pamięć podręczną pakietów

Pamięć podręczną pakietów zawiera źródło pakietów zainstalowanych w razie potrzeby napraw program Visual Studio lub innych pokrewnych produktów w przypadkach, gdy mają Brak połączenia internetowego. Niektóre dyski lub system ustawienie ups, jednak nie można zachować tych pakietów wokół.
Instalator pobierze je w razie potrzeby, więc jeśli chcesz zapisać lub odzyskać miejsce na dysku można wyłączyć, lub Przenieś pamięć podręczną pakietów.

## <a name="disable-the-package-cache"></a>Wyłącz pamięć podręczną pakietów

Aby zainstalować, zmodyfikować lub napraw program Visual Studio lub innych produktów z nowym Instalatorem, możesz uruchomić Instalatora z `--nocache` przełącznika Instalatora.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Żadnej operacji wykonywanych na jakimkolwiek produktem usunie wszystkie istniejące pakiety dla tego produktu i uniknąć zapisywania wszystkie pakiety po ich zainstalowaniu. Jeśli zmodyfikować lub napraw program Visual Studio i pakiety są wymagane, będzie można automatycznie pobierane i usunąć po ich zainstalowaniu.

Jeśli chcesz ponownie włączyć pamięć podręczną, Przekaż `--cache` zamiast tego. Tylko pakiety, które są wymagane będą buforowane, więc należy przywrócić wszystkie pakiety należy naprawić Visual Studio przed odłączyć od sieci.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Można również ustawić `KeepDownloadedPayloads` [zasad rejestru](set-defaults-for-enterprise-deployments.md) wyłączenie pamięci podręcznej, aby zainstalować, zmodyfikować lub napraw program Visual Studio.

## <a name="move-the-package-cache"></a>Przenieś pamięć podręczną pakietów

Typowa konfiguracja systemu jest mieć systemu Windows zainstalowaną na dysk SSD na większy dysk twardy (lub więcej) dla rozwoju musi, takich jak kodu źródłowego, pliki binarne programu i inne. Aby pracować w trybie offline można zamiast tego Przenieś pamięć podręczną pakietów.

Obecnie można tylko w tym przypadku ustawienia `CachePath` [zasad rejestru](set-defaults-for-enterprise-deployments.md) przed zainstalować, zmodyfikować lub napraw program Visual Studio.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także

 * [Zainstaluj program Visual Studio](install-visual-studio.md)
 * [Ustawianie wartości domyślnych do wdrożeń w przedsiębiorstwie](set-defaults-for-enterprise-deployments.md)
 * [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
