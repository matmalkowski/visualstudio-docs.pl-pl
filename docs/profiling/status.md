---
title: Stan | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1168fb27330f49a714e64478fc7ab167569dadb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="status"></a>Stan
VSPerfCmd.exe **stan** opcja powoduje wyświetlenie informacji o stanie profilera i wszystkie procesy, które są aktualnie PROFILOWANEGO.  
  
 **Stan** opcja musi być jedyną opcją określona w wierszu polecenia. Profiler musi zostać zainicjowany z VSPerfCmd.exe **Start** opcji przed wyświetleniem o stanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 **Stan** opcja wyświetla następujące informacje o stanie dla profilera.  
  
 **Nazwa pliku wyjściowego**  
 Nazwa i ścieżka pliku bieżącego pliku danych profilera.  
  
 **Tryb kolekcji**  
 Przykładowe lub śledzenia  
  
 **Maksymalna procesów**  
 Liczba obecnie aktywnych procesów, a maksymalna liczba procesów, które mogą być profilowane w tym samym czasie.  
  
 **Maksymalna liczba wątków**  
 Maksymalna liczba wątków, które mogą być profilowane w tym samym czasie.  
  
 **Liczba buforów**  
 Liczba buforów pamięci przeznaczona do zapisywania danych profilowania.  
  
 **Rozmiar buforów**  
 Rozmiar w bajtach buforu pamięci.  
  
 **Stan** opcja wyświetla następujące informacje o stanie dla każdego procesu, który jest poddawany profilowaniu.  
  
 **Proces**  
 Nazwa PROFILOWANEGO procesu.  
  
 **Identyfikator procesu**  
 Systemowy identyfikator procesu.  
  
 **Liczba wątków**  
 Liczba aktualnie wykonywanych wątków.  
  
 **Liczba uruchomień/zatrzymań**  
 Licznik podstawowy wewnętrzny profilera, do kontrolowania funkcji zbierania danych dla tego procesu. Wartość licznika musi być równa jeden do zbierania danych. Liczbę uruchomień/zatrzymań może manipulować profilera interfejsów API i opcje narzędzia VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, i **ThreadOff**.  
  
 **Wstrzymanie/wznowienie liczby**  
 Liczba dodatkowej wewnętrzny profilera do kontrolowania funkcji zbierania danych dla tego procesu. Liczba musi być mniejsza lub równa zero do zbierania danych. **Wstrzymań/wznowień** liczba może używać tylko interfejsów API profilera.  
  
 **Użytkownicy z prawami dostępu do monitorowania**  
 Wyświetla nazwy użytkowników, którzy mają dostęp do profilera. Dodatkowym użytkownikom można udzielić dostępu za pomocą VSPerfCmd.exe **Admin** opcji  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)