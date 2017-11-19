---
title: WaitStart | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ee49ea6e9aecbd3f2a71a20f512e6d482a85d53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="waitstart"></a>WaitStart
Opcja WaitStart powoduje, że podpolecenie VSPerfCmd.exe Start przywrócić tylko wtedy, gdy profilera został zainicjowany lub po upływie określonej liczby sekund. Domyślnie polecenia Start zwraca natychmiast. Jeśli polecenie sub Start zwraca bez podczas inicjowania profilera, zwracany jest błąd. Jeśli nie określono liczbę sekund, przez czas nieokreślony oczekuje polecenia uruchomienia.  
  
 Opcja WaitStart jest przydatna w plikach wsadowych, aby upewnić się, że profiler ten został zainicjowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Seconds`  
 Liczba sekund oczekiwania przed powrotem z podpolecenie rozpoczęcia.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja WaitStart można tylko z podpolecenie rozpoczęcia.  
  
 **Dane wyjściowe:**`filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pliku wsadowego polecenia Start będzie oczekiwał na 5 sekund w celu inicjowania profilera.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```