---
title: "Widok linii - dane próbkowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d08d090ad8e130e209af0d2057a065ed0bc474a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lines-view---sampling-data"></a>Widok linii - dane próbkowania
Uruchom wierszy widok danych próbkowania wyświetla dane wydajności dla instrukcji, które były wykonywane w chwili przykłady zostały zebrane w profilowania.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 W pliku źródłowym instrukcję może obejmować więcej niż jeden wiersz w pliku źródłowym, a jednym wierszu może zawierać więcej niż jedną instrukcję. Instrukcja jest identyfikowany przez następujące czynności:  
  
-   Plik źródłowy, który zawiera deklarację funkcji.  
  
-   Funkcja, która zawiera instrukcję.  
  
-   Wiersza źródłowego, od której rozpoczyna się instrukcji.  
  
-   Po znaku wiersza źródłowego, w którym rozpoczyna się instrukcji.  
  
-   Wiersza źródłowego, w którym kończy się instrukcji.  
  
-   Po znaku wiersza źródłowego, w którym kończy się instrukcji.  
  
 Kolumna nazw wiersza zawiera sortowanie łączenia danych identyfikator.  
  
 Zgodnie z definicją instrukcję nie wywołuje inne funkcje. W związku z tym są wyświetlane tylko wartości wyłącznego.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa moduł, który zawiera wiersz funkcji.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera wiersz funkcji.|  
|**Plik źródłowy**|Plik źródłowy zawiera wiersz funkcji.|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Początkowy adres funkcji.|  
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym zostały zebrane w tym przykładzie.|  
|**Źródło końca wiersza**|Końcowy numer wiersza pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Rozpocznij znaków źródła**|Przesunięcie początkowy znak w wiersza pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Źródło znak końcowy**|Przesunięcie znak końcowy w wiersza pliku źródłowego, w którym zostały zebrane w tym przykładzie.|  
|**Nazwa linii**|Generowane przez profiler identyfikator wiersza przy użyciu następującej składni:`Source File`**; [**  `Line Number Start` **,**`Character Start`**] ->; [** `Line Number End`**,**`Character End`**]**|  
|**Wyłącznych próbek**|Łączna liczba próbek, które zostały zebrane podczas wykonywania funkcji wiersza.|  
|**% Wyłącznych próbek**|Procent wszystkich próbek w przebiegu profilowania, które zostały zebrane podczas wykonywania funkcji wiersza.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok linii - próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)