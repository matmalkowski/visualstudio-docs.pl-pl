---
title: "Określanie ścieżki do profilowania narzędzia wiersza polecenia narzędzia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b33ee79d51dfcdb3db9021d3613672c44aef8956
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Określanie ścieżki do narzędzi wiersza polecenia narzędzi profilowania
Ścieżka [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzi profilowania nie została dodana do zmiennej środowiskowej PATH. Na komputerach z 32-bitowego narzędzia znajdują się w jeden katalog. Istnieje 32-bitowe i 64-bitowe wersje narzędzi profilowania na komputerach 64-bitowych.  
  
## <a name="32-bit-computers"></a>32-bitowych komputerów  
 Na komputerach z 32-bitowy, domyślny katalog narzędzia profiler jest *dysków*\Program Files\Microsoft 11.0\Team programu Visual Studio Tools narzędzia.  
  
## <a name="64-bit-computers"></a>Komputery 64-bitowe  
 Na komputerach 64-bitowych należy określić ścieżkę zgodnie z platformą docelową PROFILOWANEGO aplikacji.  
  
-   Dla 32-bitowych aplikacji domyślny katalog narzędzia profiler jest:  
  
     *Dysk*\Program pliki (x86) \Microsoft Visual Studio 11.0\Team narzędzia Tools  
  
-   Dla 64-bitowych aplikacji domyślny katalog narzędzia profiler jest:  
  
     *Dysk*\Program pliki (x86) \Microsoft Visual Studio 11.0\Team narzędzia Tools\x64