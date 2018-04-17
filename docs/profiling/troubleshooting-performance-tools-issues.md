---
title: Rozwiązywanie problemów z wydajnością narzędzi problemów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f280fbe73e44062b3a5e53083a9ab7de643dde34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-performance-tools-issues"></a>Rozwiązywanie problemów z wydajnością narzędzi problemów
Korzystając z narzędzi profilowania mogą wystąpić jeden z następujących problemów:  
  
-   [Żadne dane nie są zbierane za pomocą narzędzi do profilowania](#NoDataCollected)  
  
-   [Numery wyświetlania raportów dla nazwy funkcji i widokach wydajności](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Żadne dane nie są zbierane za pomocą narzędzi do profilowania  
 Po profilu aplikacji, nie utworzono profilowania plik danych (Vsp) i w oknie danych wyjściowych lub w oknie wiersza polecenia pojawi się następujące ostrzeżenie:  
  
 PRF0025: Zbierane żadne dane.  
  
 Ten problem może być spowodowana przez kilka problemów:  
  
-   Proces, który został profilowany przy użyciu próbki lub metody pamięci .NET uruchamia proces podrzędny, które staje się proces, który wykonuje pracę aplikacji. Na przykład niektóre aplikacje odczytać wiersza polecenia, aby określić, czy zostały one uruchomione jako aplikacji systemu Windows lub wiersza polecenia aplikacji. Jeśli zażądano aplikacji systemu Windows, proces oryginalnego uruchamiany nowy proces, skonfigurowany jako aplikacji systemu Windows i pierwotny proces kończy pracę. Ponieważ profilowania narzędzia nie zbierają automatycznie danych dla procesów podrzędnych, zbierane żadne dane.  
  
     Do zbierania danych profilowania w takiej sytuacji, dołączanie profilera do procesu podrzędnego zamiast uruchamiania aplikacji przy użyciu profilera. Aby uzyskać więcej informacji, zobacz [porady: dołączanie i odłączanie narzędzi wydajności do uruchamiania procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [Attach (VSPerfCmd)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Numery wyświetlania raportów dla nazwy funkcji i widokach wydajności  
 Po profilu aplikacji, możesz wyświetlić numery zamiast nazwy funkcji w raportach i widokach.  
  
 Przyczyną tego problemu jest aparat analizy narzędziach profilowania nie będzie w stanie odnaleźć plików .pdb, które zawierają informacje symbol mapowanego informacji dotyczących kodu źródłowego, takich funkcji nazwy i numery wierszy skompilowanego pliku. Domyślnie kompilator tworzy plik PDB podczas tworzenia pliku aplikacji. Odwołanie do katalogu lokalnego pliku PDB jest przechowywany w skompilowanej aplikacji. Aparat analizy wygląda w katalogu przywoływanego pliku .pdb, a następnie w pliku zawierającego plik aplikacji. Jeśli nie znaleziono pliku PDB, aparat analizy używa funkcji przesunięcia zamiast nazwy funkcji.  
  
 Można rozwiązać ten problem w jednym z dwóch sposobów:  
  
-   Znajdź .pdb, pliki i umieścić je w tym samym katalogu co pliki aplikacji.  
  
-   Osadzanie informacji o symbolach w pliku danych (Vsp) do profilowania. Aby uzyskać więcej informacji, zobacz [zapisywania informacji o symbolach z plikami danych wydajności](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Aparat analizy wymaga pliku .pdb wersji zgodnej z wersją pliku skompilowanej aplikacji. Plik PDB z wcześniejszych lub nowszej kompilacji pliku aplikacji nie będzie działać.