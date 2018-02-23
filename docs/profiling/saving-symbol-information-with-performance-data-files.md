---
title: "Zapisywanie informacji o symbolach z plikami danych wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c92373294392dcbf78e57c096f40b0de5d63291a
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach z plikami danych wydajności

Jeśli używasz środowiska IDE programu Visual Studio do analizowania plików i planujesz przeniesienie pliku VSP na inny komputer, musisz ustawić wydajność ustawienia projektu, aby zapisać lub *serializować* symboli w pliku raportu. Powoduje to zwiększenie rozmiaru pliku raportu. Serializacja symboli jest dwóch powodów:

- Aby osadzić kod symbole w raporcie wydajności przed zestawy docelowe zostaną utracone z lokalizacji w tymczasowej.

- Aby zachować symbole, dzięki czemu raport wydajności z profilowanego komputera przenośnego i wysyła te same informacje po otwarciu raportu analizy na innym komputerze, które mogą mieć różnych symboli.

Może wykonywać serializację symbole z programu Visual Studio IDE lub z wiersza polecenia:

- Do zserializowania symboli w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, wskaż **narzędzia** na pasku menu, a następnie kliknij przycisk **opcje**. W **opcje** wybierz **narzędzi wydajności**, a następnie wybierz **automatycznie serializuj informacje dotyczące symboli** pole wyboru.

- PACKSYMBOLS jest równoważne opcji wiersza polecenia podczas zapisywania pliku raportu. Do zserializowania symboli, wpisz **vsperfreport /summary:all /packsymbols filename.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów — Symbol

Jeśli nie ma żadnych symboli w swoim własnym kodem, dostępne są niektóre typowe rozwiązania:

- Uruchom vsperfreport /debugsympath w wierszu polecenia, aby wyświetlić listę wszystkich lokalizacji, gdzie składniki profilera ładowania informacji o symbolach i określa, czy pliki symboli, które są używane zgodne pliki, które Twoim projekcie są używani.

- Upewnij się, że uruchomienie polecenia vsperfreport z flagą /PACKSYMBOLS lub w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, czy masz serializacja symbol informacji zaznaczoną opcją w opcjach explorer ogólnej wydajności.

- Jeśli zbierane dane typu, należy dodać /SUMMARY:TYPE do wiersza polecenia vsperfreport.

 Jeśli nie ma symboli z systemu Windows lub innych programów firmy Microsoft:

- Upewnij się, że ustawiono ścieżkę symboli pamięci podręcznej systemu Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:

  - Zestaw debuger -> symbole w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE w celu poprawną ścieżkę.

  - Dodaj opcję - symbolpath do wiersza polecenia VSPerfReport dołączać symbole użytkownika.

- Jeśli nie ma żadnych symboli w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], upewnij się, że masz serwera symboli poprawnie skonfigurowane dla serwera ASP.

## <a name="repacking-symbols"></a>Przepakowaniu symboli

Jeśli chcesz ponownie spakować symboli do raportu, można to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy polecenia:

VsPerfReport — clearpackedsymbols filename.vsp

VsPerfReport — packsymbols — Podsumowanie: all filename.vsp

## <a name="see-also"></a>Zobacz także

[Zapisywanie i eksportowanie wydajności narzędzi danych](../profiling/saving-and-exporting-performance-tools-data.md)  
[Porady: odwołania informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)  
[VSPerfReport](../profiling/vsperfreport.md)