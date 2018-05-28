---
title: Rozwiązywanie problemów z wydajnością narzędzi problemów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e78013c97bf7f2cf3bcd60f642f51e9da01b25d
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="troubleshoot-performance-tools-issues"></a>Narzędzia do rozwiązywania problemów z wydajnością
Korzystając z narzędzi profilowania mogą wystąpić jeden z następujących problemów:  
  
-   [Żadne dane nie są zbierane za pomocą narzędzi do profilowania](#NoDataCollected)  
  
-   [Raportach i widokach wydajności wyświetlać numery dla nazwy funkcji](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a>Żadne dane nie są zbierane za pomocą narzędzi do profilowania  
 Po profilu aplikacji, danych profilowania (. *Vsp*) nie jest tworzony plik i w oknie danych wyjściowych lub w oknie wiersza polecenia pojawi się następujące ostrzeżenie:  
  
 PRF0025: Zbierane żadne dane.  
  
 Ten problem może być spowodowana przez kilka problemów:  
  
-   Proces, który został profilowany przy użyciu próbki lub metody pamięci .NET uruchamia proces podrzędny, które staje się proces, który wykonuje pracę aplikacji. Na przykład niektóre aplikacje odczytać wiersza polecenia, aby określić, czy zostały one uruchomione jako aplikacji systemu Windows lub wiersza polecenia aplikacji. Jeśli zażądano aplikacji systemu Windows, proces oryginalnego uruchamiany nowy proces, skonfigurowany jako aplikacji systemu Windows i pierwotny proces kończy pracę. Ponieważ profilowania narzędzia nie zbierają automatycznie danych dla procesów podrzędnych, zbierane żadne dane.  
  
     Do zbierania danych profilowania w takiej sytuacji, dołączanie profilera do procesu podrzędnego zamiast uruchamiania aplikacji przy użyciu profilera. Aby uzyskać więcej informacji, zobacz [porady: dołączanie i odłączania narzędzi wydajności do uruchomionego procesu](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [Attach (VSPerfCmd)](../profiling/attach.md)  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Raportach i widokach wydajności wyświetlać numery dla nazwy funkcji  
 Po profilu aplikacji, możesz wyświetlić numery zamiast nazwy funkcji w raportach i widokach.  
  
 Przyczyną tego problemu w narzędziach profilowania aparat analizy, nie można odnaleźć *.pdb* pliki, które zawierają informacje o symbolach czy mapy źródła kodu, takie nazwy funkcji i numery wierszy do skompilowanego pliku. Domyślnie tworzy kompilator *.pdb* pliku po utworzeniu pliku aplikacji. Odwołanie do katalogu lokalnego *.pdb* plik jest przechowywany w skompilowanej aplikacji. Aparat analizy wygląda w katalogu przywoływanego *.pdb* plików i następnie w pliku obecnie zawiera pliku aplikacji. Jeśli *.pdb* nie znaleziono pliku, aparat analizy korzysta z funkcji przesunięcia zamiast nazwy funkcji.  
  
 Można rozwiązać ten problem w jednym z dwóch sposobów:  
  
-   Znajdź. *pdb* pliki i umieścić je w tym samym katalogu co pliki aplikacji.  
  
-   Osadzanie informacji o symbolach w danych profilowania (. *Vsp*) pliku. Aby uzyskać więcej informacji, zobacz [zapisać informacji o symbolach z wydajnością pliki danych](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Wymaga aparatu analizy. *pdb* plik jest w wersji zgodnej z wersją pliku skompilowanej aplikacji. A *.pdb* pliku z wcześniejszych lub nowszej kompilacji pliku aplikacji nie będą działać.