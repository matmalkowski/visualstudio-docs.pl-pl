---
title: Debugowanie kontenera i serwera COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4c23d362a930f28ccb1a097de44a936e55cacf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="com-server-and-container-debugging"></a>Debugowanie kontenera i serwera COM
Aplikacje COM wykonać szereg zadań poza programisty bezpośrednią kontrolę. Komunikacja między bibliotek DLL, użycie Zlicza na obiektach, a operacje schowka przedstawiono kilka obszarów, w którym mogą wystąpić nieoczekiwane zachowanie. W takim przypadku pierwszym krokiem jest śledzenie źródła problemu.  
  
 Debuger programu Visual Studio obsługuje wykonywanie krok po kroku bok i w kontenery i serwery. Obejmuje to możliwość krok w zdalnych wywołań procedur (RPC).  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Debugowanie kontenera, w tym samym rozwiązaniu i serwera COM  
 Można debugować przy użyciu dwa projekty w tym samym rozwiązaniu kontenera i serwera COM. Ustaw odpowiednie punkty przerwania w każdym projekcie i debugowania. Gdy kontener wywołuje na serwerze, na którym trafienia punktu przerwania, kontener będzie czekał zwraca kod serwera (oznacza to, aż do zakończenia jej debugowanie).  
  
 Debugowanie kontenera COM jest podobny do debugowania program standardowy. Jeden różnica polega na podczas debugowania zdarzenie powodujące wygenerowanie wywołanie zwrotne (na przykład przeciąganie danych za pośrednictwem aplikacji kontenera). W takim przypadku należy ustawić punkt przerwania w funkcji wywołania zwrotnego.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debugowanie aplikacji serwera bez informacji o kontenerze  
 Jeśli nie masz lub nie chcesz użyć informacji debugowania dla aplikacji kontenera, uruchamianie do debugowania aplikacji serwera jest procesem trzech etapów:  
  
1.  Uruchom profilowanie na serwerze jako normalne aplikacji.  
  
2.  Ustaw punkty przerwania, zgodnie z potrzebami.  
  
3.  Uruchom aplikację kontenera.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debugowanie serwera i domeny aplikacji izolacji (SDI)  
 Jeśli debugujesz aplikację serwera SDI, należy określić `/Embedding` lub `/Automation` w **argumenty wiersza polecenia** właściwości w *projektu* okno dialogowe strony właściwości dla C/C++, C# lub Projekty Visual Basic.  
  
 Argumenty wiersza polecenia debuger można uruchomić aplikacji serwera tak, jakby były go uruchomić z kontenera. Kontener, począwszy od programu menedżera lub pliku spowoduje następnie kontenera do korzystania z wystąpienia serwera usługi uruchomione w debugerze.  
  
 Aby uzyskać dostęp do *projektu* strony właściwości — okno dialogowe, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie z menu skrótów wybierz polecenie Właściwości. Aby znaleźć właściwości argumenty wiersza polecenia, rozwiń kategorię właściwości konfiguracji, a następnie kliknij przycisk Strona debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)