---
title: WaitStart | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 059f05d25f1882cd857dd1e39ea40a58a7c5e1d3
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571373"
---
# <a name="waitstart"></a>WaitStart
Przyczyny opcja WaitStart *VSPerfCmd.exe* podpolecenie Start, aby przywrócić tylko wtedy, gdy profilera został zainicjowany lub po upływie określonej liczby sekund. Domyślnie polecenia Start zwraca natychmiast. Jeśli polecenie sub Start zwraca bez podczas inicjowania profilera, zwracany jest błąd. Jeśli nie określono liczbę sekund, przez czas nieokreślony oczekuje polecenia uruchomienia.  
  
 Opcja WaitStart jest przydatna w plikach wsadowych, aby upewnić się, że profiler ten został zainicjowany.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Seconds`  
 Liczba sekund oczekiwania przed powrotem z podpolecenie rozpoczęcia.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja WaitStart można tylko z podpolecenie rozpoczęcia.  
  
 **Dane wyjściowe:** `filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pliku wsadowego polecenia Start będzie oczekiwał na 5 sekund w celu inicjowania profilera.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```