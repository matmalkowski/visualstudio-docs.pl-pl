---
title: Stan | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a786954884ab0a654246a46f88f6a270e4088cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679893"
---
# <a name="status"></a>Stan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [stan](https://docs.microsoft.com/visualstudio/profiling/status).  
  
VSPerfCmd.exe **stan** opcji wyświetla informacje o stanie programu profilującego i wszystkie procesy, które są obecnie poddawany profilowaniu.  
  
 **Stan** opcja musi być jedyną opcją, określone w wierszu polecenia. Program profilujący musi zostać zainicjowany z VSPerfCmd.exe **Start** opcji, przed wyświetleniem dowolny stan.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 **Stan** opcja wyświetla następujące informacje o stanie programu Profiler.  
  
 **Nazwa pliku wyjściowego**  
 Ścieżka i nazwa bieżącego pliku danych profilera.  
  
 **Tryb kolekcji**  
 PRZYKŁAD lub śledzenia  
  
 **Maksymalna liczba procesów**  
 Maksymalna liczba procesów, które mogą być profilowane, w tym samym czasie i Liczba obecnie aktywnych procesów.  
  
 **Maksymalna liczba wątków**  
 Maksymalna liczba wątków, które mogą być profilowane, w tym samym czasie.  
  
 **Liczba buforów**  
 Liczba buforów pamięci przeznaczone do zapisywania danych profilowania.  
  
 **Rozmiar buforów**  
 Rozmiar w bajtach bufora pamięci.  
  
 **Stan** opcja wyświetla następujące informacje o stanie dla każdego procesu, który jest obecnie poddawany profilowaniu.  
  
 **Proces**  
 Nazwa PROFILOWANEGO procesu.  
  
 **Identyfikator procesu**  
 Identyfikator systemu procesu.  
  
 **Liczba wątków**  
 Liczba wątków w trakcie wykonywania.  
  
 **Liczba uruchomień/zatrzymań**  
 Licznik podstawowy wewnętrzny profilera można kontrolować zbieranie danych dla tego procesu. Liczba musi być równa jeden do zbierania danych. Liczba uruchomień/zatrzymań może być manipulowane przez profiler interfejsów API i opcji VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, i **ThreadOff**.  
  
 **Liczba wstrzymań/wznowień**  
 Liczba pomocniczych wewnętrzny profilera można kontrolować zbieranie danych dla tego procesu. Liczba musi być mniejsza lub równa zero do zbierania danych. **Wstrzymań/wznowień** liczba może używać tylko interfejsów API profilera.  
  
 **Użytkownicy z prawami dostępu w celu monitorowania**  
 Wyświetla listę nazw użytkowników, którzy mają dostęp do programu profilującego. Dodatkowym użytkownikom można udzielić dostępu przy użyciu VSPerfCmd.exe **administratora** opcji  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



