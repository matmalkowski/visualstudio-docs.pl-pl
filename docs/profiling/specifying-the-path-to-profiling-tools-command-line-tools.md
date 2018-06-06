---
title: Określanie ścieżki do profilowania narzędzia wiersza polecenia narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1afb0b00a7e121c611dedbc235684a67cc9cec53
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814498"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Określ ścieżkę do narzędzia wiersza polecenia narzędzi profilowania
Ścieżka [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzi profilowania nie została dodana do zmiennej środowiskowej PATH. Na komputerach z 32-bitowego narzędzia znajdują się w jeden katalog. Istnieje 32-bitowe i 64-bitowe wersje narzędzi profilowania na komputerach 64-bitowych.  
  
## <a name="32-bit-computers"></a>32-bitowych komputerów  
 Na komputerach z 32-bitowy, domyślny katalog narzędzia profiler jest *: dysk rozruchowy\Program 11.0\Team Files\Microsoft Visual Studio Tools narzędzia*.  
  
## <a name="64-bit-computers"></a>Komputery 64-bitowe  
 Na komputerach 64-bitowych należy określić ścieżkę zgodnie z platformą docelową PROFILOWANEGO aplikacji.  
  
-   Dla 32-bitowych aplikacji domyślny katalog narzędzia profiler jest:  
  
     *: dysk rozruchowy\Program pliki (x86) \Microsoft Visual Studio 11.0\Team narzędzia narzędzia*  
  
-   Dla 64-bitowych aplikacji domyślny katalog narzędzia profiler jest:  
  
     *: dysk rozruchowy\Program pliki (x86) \Microsoft Visual Studio 11.0\Team Tools\x64 narzędzia*