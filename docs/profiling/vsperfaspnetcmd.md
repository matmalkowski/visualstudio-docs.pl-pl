---
title: VSPerfASPNetCmd | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 424bc775e335c093dfbd89dfd0488a545bed7563
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** narzędzie wiersza polecenia umożliwia profilu ASP.Net witryn sieci Web bez konieczności Ustaw zmienne środowiskowe, lub uruchom ponownie komputer. Użyj **VSPerfASPNetCmd.exe** zamiast [VSPerfCmd](../profiling/vsperfcmd.md) kiedy są profilowania witryn sieci Web ASP.NET i nie są dodatkowe funkcje udostępniane przez **VSPerfCmd**. Aby uzyskać więcej informacji na temat **VSPerfASPNetCmd**, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** to narzędzie wiersza polecenia preferowany do użycia, gdy jest używany autonomiczny profiler profilowanie witryny sieci Web ASP.NET.  
  
## <a name="syntax"></a>Składnia  
 **vsperfaspnetcmd** [/*opcje*] *witryny sieci Web*  
  
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ Przykładowy** lub   **/s**|Profile witryny sieci Web za pomocą metody pobierania próbek. **/ Przykładowy** jest domyślną metodą. / Sample nie można używać z **/Trace**.|  
|**/ Trace** lub **/t**|Profile witryny sieci Web przy użyciu metody instrumentacji. / Śledzenia nie można używać z **/przykładowe**.|  
|**/ Pamięci**[**:**`Type`] lub **/m**[**:**{****&#124; **l**}]|Alokacja pamięci, profile i opcjonalnie profili okresy istnienia obiektu (pamięci). **/ Pamięci** może być używany z próbki lub metody instrumentacji.<br /><br /> *Typ* może być jedną z następujących czynności:<br /><br /> -   **Alokacja** (lub ****) zbiera tylko dane alokacji pamięci.<br />-   **okres istnienia** (lub **l**) zbiera dane okresu istnienia alokacji i obiektu pamięci.<br /><br /> Wartość domyślna `Type` jest **alokacji**.|  
|**/ Tip** lub **/i**|Dodaje szczegółowe żądania programu ASP.NET i informacji o wywołaniu ADO.NET do danych profilowania. **/ Tip** mogą być używane z próbki lub metody Instrumentacji i może być używany z **/Memory** opcji.|  
|**/ Output:** `File` lub   **/o:**`File`|Określa ścieżkę i nazwę profilowania plik danych (Vsp).|  
|**/ NoWait** lub**/n**|Zwraca polecenie monitu natychmiast, dzięki czemu można użyć dodatkowych poleceń w oknie wiersza polecenia. Należy wpisać **polecenie VSPerfASPNETCmd/shutdown** w osobnym wierszu polecenia, aby wyłączyć profilowania.|  
|**/ PackSymbols**[: {**na**&#124; **Wyłącz**} lub **/p**[: {**na**&#124; **Wyłącz**}|Osadza symboli (nazwy funkcji i parametr itp.) w pliku danych (Vsp) profilowania.|  
|**/ Shutdown:** `Website`lub   **/d:**`Website`|Włącza profilowanie. Użyj tylko opcji wiersza polecenia po użyciu **/nowait** opcji do uruchomienia profilowania, lub jeśli profilera kończy się nieoczekiwanie. Określ ten sam adres url, który został użyty w oryginalnym **VSPerfASPNETCmd** polecenia.|  
|`Website`|Adres url witryny sieci Web do profilowania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Szybkie profilowanie za pomocą VSPerfASPNETCmd witryny sieci Web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)