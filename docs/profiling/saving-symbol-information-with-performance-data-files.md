---
title: "Zapisywanie informacji o symbolach z plikami danych wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd963c269ee5fe18d3f490bf85bab5dcf3afbf9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach z plikami danych wydajności
Jeśli używasz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) do analizowania plików, a ma zostać przeniesiona do pliku VSP na innym komputerze, należy ustawić wydajność ustawienia projektu, aby zapisać lub *serializować* symboli w pliku raportu. Powoduje to zwiększenie rozmiaru pliku raportu. Serializacja symboli jest dwóch powodów:  
  
-   Aby osadzić kod symbole w raporcie wydajności przed zestawy docelowe zostaną utracone z lokalizacji w tymczasowej.  
  
-   Aby zachować symbole, dzięki czemu raport wydajności z profilowanego komputera przenośnego i wysyła te same informacje po otwarciu raportu analizy na innym komputerze, które mogą mieć różnych symboli.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Może wykonywać serializację symbole z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE lub z wiersza polecenia:  
  
-   Do zserializowania symboli w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, wskaż **narzędzia** na pasku menu, a następnie kliknij przycisk **opcje**. W **opcje** wybierz **narzędzi wydajności**, a następnie wybierz **automatycznie serializuj informacje dotyczące symboli** pole wyboru.  
  
-   PACKSYMBOLS jest równoważne opcji wiersza polecenia podczas zapisywania pliku raportu. Do zserializowania symboli, wpisz **vsperfreport /summary:all /packsymbols filename.vsp**.  
  
## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów — Symbol  
 Jeśli nie ma żadnych symboli w swoim własnym kodem, dostępne są niektóre typowe rozwiązania:  
  
-   Uruchom vsperfreport /debugsympath w wierszu polecenia, aby wyświetlić listę wszystkich lokalizacji, gdzie składniki profilera ładowania informacji o symbolach i określa, czy pliki symboli, które są używane zgodne pliki, które Twoim projekcie są używani.  
  
-   Upewnij się, że uruchomienie polecenia vsperfreport z flagą /PACKSYMBOLS lub w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, czy masz serializacja symbol informacji zaznaczoną opcją w opcjach explorer ogólnej wydajności.  
  
-   Jeśli zbierane dane typu, należy dodać /SUMMARY:TYPE do wiersza polecenia vsperfreport.  
  
 Jeśli nie ma symboli z systemu Windows lub innych programów firmy Microsoft:  
  
-   Upewnij się, że ustawiono ścieżkę symboli pamięci podręcznej systemu Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:  
  
    -   Zestaw debuger -> symbole w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE w celu poprawną ścieżkę.  
  
    -   Dodaj opcję - symbolpath do wiersza polecenia VSPerfReport dołączać symbole użytkownika.  
  
-   Jeśli nie ma żadnych symboli w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], upewnij się, że masz serwera symboli poprawnie skonfigurowane dla serwera ASP.  
  
## <a name="repacking-symbols"></a>Przepakowaniu symboli  
 Jeśli chcesz ponownie spakować symboli do raportu, można to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy polecenia:  
  
 VsPerfReport — clearpackedsymbols filename.vsp  
  
 VsPerfReport — packsymbols — Podsumowanie: all filename.vsp  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie i eksportowanie wydajności narzędzi danych](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Porady: odwołania informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)