---
title: Widok wskaźników instrukcji (IP) - dane próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d23c04906c9f1d3cd28ded7b88ee225c13240f53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629496"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Widok wskaźników instrukcji (IP) — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [widok wskaźników instrukcji (IP) - dane z próbkowania](https://docs.microsoft.com/visualstudio/profiling/instruction-pointers-ips-view-sampling-data).  
  
Widok adresy IP próbkuje dane wydajności wyświetla dane dla instrukcje montażu, które wykonywały bezpośrednio po przykłady zostały zebrane podczas uruchomienia profilowania.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|  
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Początkowy adres pamięci funkcja w załadowano danych binarnych.|  
|**Początkowy wiersz w źródle**|Numer wiersza początkowego w pliku źródłowym, w którym zostały zebrane w tym przykładzie.|  
|**Końcowy wiersz w źródle**|Końcowy numer wiersza w pliku źródłowym, w którym zostały zebrane w tym przykładzie.|  
|**Początkowy znak w źródle**|Przesunięcie początkowy znak w wierszu pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Końcowy znak w źródle**|Przesunięcie końcowy znak w wierszu pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Adres instrukcji**|Adres instrukcji w załadowano danych binarnych.|  
|**Próbki wyłączne**|Łączna liczba próbek, które zostały zebrane podczas wykonywania instrukcji.|  
|**% Wyłącznych próbek**|Procent wszystkich przykładów podczas uruchomienia profilowania, które zostały zebrane podczas wykonywania instrukcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wskaźników instrukcji (IP) View - próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)



