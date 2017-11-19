---
title: 'Porady: Instalowanie autonomiczny profilera | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0799a5da2b1596c79a57a6960283c62fca709a8a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Porady: instalowanie autonomiczny profilera
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zawiera autonomiczny profilera, który można uruchomić bez konieczności instalowania na podstawie wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Ta sytuacja występuje, gdy komputer nie obsługuje lub nie może mieć zainstalowane środowisko deweloperskie. Na przykład nie należy instalować Środowisko deweloperskie na serwerze sieci Web w środowisku produkcyjnym.  
  
> [!NOTE]
>  Gdy jest używany autonomiczny profilera do zbierania danych wydajności dla witryny sieci Web ASP.NET [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) narzędzie Linia zaleca się za pośrednictwem [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Aby zainstalować autonomiczny profilera  
  
1.  Zlokalizuj profilu Autonomiczny Instalator (vs_profiler.exe) na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nośnika instalacyjnego w katalogu, który zawiera ścieżki profilera \Standalone i uruchom go.  
  
2.  Dodaj ścieżki vsintr.exe i msdis150.dll do ścieżki systemowej.  
  
    > [!NOTE]
    >  W domyślnej instalacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vsinstr.exe i msdis150.dll znajdują się w \Program Files\Visual Studio 10\Team narzędzia Tools.  
  
3.  W wierszu polecenia wpisz **VSInstr**.  
  
    > [!NOTE]
    >  Jeśli informacje o użyciu dla vsinstr.exe jest wyświetlany, wszystko jest poprawnie skonfigurowany. Jeśli zostanie wyświetlony błąd informujący vsinstr.exe lub jednej z jego zależności nie zostanie odnaleziony, upewnij się, że Twoje ścieżek poprawnie skonfigurowane zgodnie z opisem w kroku 2.  
  
4.  Konfigurowanie serwera symboli przez ustawienie Twojego **_NT_SYMBOL_PATH** zmienną **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5.  Po skonfigurowaniu serwera symboli za pomocą zmiennych środowiskowych systemu jednocześnie profilera z wiersza polecenia narzędzia nowego wiersza polecenia. Dzięki temu nowe zmienne środowiskowe zaczęły obowiązywać. W oknie wiersza polecenia wpisz następujące polecenie:  
  
     **Uruchom COMSPEC %**  
  
    > [!NOTE]
    >  Aby uzyskać szczegółowe instrukcje dotyczące sposobu konfigurowania pakietu serwera symboli, zobacz [porady: odwołanie do systemu Windows — informacje o symbolach](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Użyj [VSPerfReport](../profiling/vsperfreport.md) narzędzia do serializacji z symboli do profilowania plik danych (Vsp). Użyj **VSPerfReport /summary:all /packsymbols** przełączników. Jeśli nie ma symboli wstawione w pliku danych, upewnij się, że masz _NT_SYMBOL_PATH zestaw zmiennych środowiska.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Wskazówki: Profilowanie wiersza polecenia przy użyciu pobierania próbek](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Wskazówki: Profilowanie wiersza polecenia przy użyciu Instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Porady: odwołania informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)