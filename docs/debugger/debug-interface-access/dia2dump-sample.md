---
title: "Dia2dump — przykład | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd21806dee94031c6d5486daf1696e1f97e2956f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dia2dump-sample"></a>Dia2dump — Przykład
Dia2dump — przykład jest zainstalowany program Visual Studio i zawiera plik źródłowy Dia2dump.cpp. Skompilowany plik wykonywalny uruchamiany z poziomu wiersza polecenia i wyświetla zawartość pliku bazy danych (.pdb) całego programu.  
  
### <a name="to-install-the-sample"></a>Aby zainstalować przykład  
  
1.  Sprawdź, że komputer spełnia wszystkie wymagania dotyczące konfiguracji opisanych w strony początkowej Instalatora programu Visual Studio.  
  
2.  Zainstaluj program Visual Studio i wykonaj wszystkie instrukcje instalacji i konfiguracji załączone przykłady.  
  
#### <a name="to-build-the-sample"></a>Aby samodzielnie tworzyć przykładowy  
  
1.  Otwórz plik Dia2dump.sln w programie Visual Studio. (Jeśli to konieczne, Visual Studio najpierw pomoże Ci uaktualniania projektu dia2dump —.)  
  
2.  Na stronach właściwości projektu w **C/C++** &#124; **Ogólne** &#124; **Dodatkowe katalogi dołączenia** właściwości, określ `..\DIA SDK\include` katalogu. Gwarantuje to, że kompilator można znaleźć pliku dia2.h.  
  
3.  Na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.  
  
4.  Zamknij program Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz wiersz polecenia i wpisz następujące polecenie:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik źródłowy Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)