---
title: Tworzenie Portable profilowania pliki danych z poziomu wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25f2faf1be7f2e8ff5c96eca16ef2de9be2514db
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815852"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Tworzenie przenośnych plików danych profilowania z wiersza polecenia
Aby udostępnianie danych profilowania, można użyć [VSPerfReport](../profiling/vsperfreport.md) narzędzia wiersza polecenia do osadzenia symboli dla przebiegu do profilowania. *Vsp* pliku.  
  
 Można również utworzyć wstępnie analizowanych danych profilowania (. *vsps*) pliku, który jest mniejszy szybszą obciążenia w środowisku IDE.  
  
> [!NOTE]
>  Upewnij się, że symbol (. *PDB*) pliki są dostępne dla **VSPerfReport**. Aby uzyskać więcej informacji, zobacz [porady: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Aby uzyskać informacje o ścieżce do **VSReport**, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Dane profilowania. *vsps* pliku nie można filtrować.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Aby osadzić symboli dla profilowania funkcjonowaniem danych profilowania (. *Vsp*) pliku  
  
-   W oknie wiersza polecenia wpisz następujące polecenie:  
  
     \<Ścieżka >**VSPerfReport \<** pliku VSP > **/PackSymbols**  
  
     Domyślnie. *vsps* nosi nazwę pliku o nazwie podstawowej z. *Vsp* pliku. Można określić nazwę alternatywną, za pomocą **dane wyjściowe** opcji.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Aby utworzyć plik podsumowania danych profilowania  
  
-   W oknie wiersza polecenia wpisz następujące polecenie:  
  
     \<Ścieżka >**VSPerfReport \<** pliku VSP > **/SummaryFile** [**/Output:**\<nazwa pliku >]  
  
     Domyślnie. *vsps* nosi nazwę pliku o nazwie podstawowej z. *Vsp* pliku. Można określić nazwę alternatywną, za pomocą **dane wyjściowe** opcji.