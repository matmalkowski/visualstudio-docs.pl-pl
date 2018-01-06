---
title: Tworzenie aplikacji dla platformy uniwersalnej systemu Windows (UWP) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 10/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: "48"
author: stevehoag
ms.author: shoag
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: a696a0b827cc8fe367390efbba01c2a18ff178bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Tworzenie aplikacji dla platformy uniwersalnej systemu Windows (UWP)
Za pomocą platformy uniwersalnej systemu Windows i naszego jednego rdzenia systemu Windows można uruchomić tej samej aplikacji na dowolnym urządzeniu z systemem Windows 10 z telefonów do komputerów stacjonarnych. Tworzenie tych aplikacji uniwersalnych systemu Windows z programu Visual Studio i narzędzia deweloperskie uniwersalnej aplikacji systemu Windows.  
  
 ![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")  
  
 Uruchamianie aplikacji na telefon Windows 10, Windows 10 desktop lub Xbox. To tego samego pakietu aplikacji! Wprowadzenie core jednej, ujednoliconej systemu Windows 10 jeden pakiet aplikacji umożliwia uruchamianie na wszystkich platformach. Wiele platform mają rozszerzenie zestawów SDK, które można dodać do aplikacji w taki sposób, aby móc korzystać z zachowania specyficzne dla platformy. Na przykład rozszerzenia SDK dla urządzeń przenośnych obsługuje przycisku Wstecz naciśniętym na urządzeniu z systemem Windows phone. Jeśli odwołanie rozszerzenia SDK w projekcie, wystarczy dodać sprawdzanie czasu wykonania, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. To, jak może mieć tej samej pakiet aplikacji dla poszczególnych platform!  
  
 **Co to jest Windows core?**  
  
 Po raz pierwszy systemu Windows ma został zrefaktoryzowany mają wspólne rdzeni na wszystkich platformach systemu Windows 10. Istnieje jeden wspólne źródło, co typowe jądra systemu Windows, jeden stos we/wy pliku i jednego modelu aplikacji. Dla interfejsu użytkownika istnieje tylko jeden framework XAML interfejsu użytkownika i jeden framework interfejsu użytkownika HTML. Można skoncentrować się na tworzenie wspaniałych aplikacji, ponieważ ułatwiliśmy ułatwia mieć aplikację, uruchom na różnych urządzeniach z systemem Windows 10.  
  
 **Co to jest dokładnie platformy uniwersalnej systemu Windows?**  
  
Platforma uniwersalna systemu Windows jest po prostu kolekcji kontrakty i wersje. Umożliwiają one należy do obiektu docelowego, których można uruchomić aplikacji. Nie jest już docelową będzie system operacyjny; teraz zostanie rozpoczęta dla przynajmniej jednej rodziny urządzeń. Dowiedz się więcej szczegółów, odczytując [wprowadzenie do platformy uniwersalnej systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).  
  
## <a name="requirements"></a>Wymagania  
 Narzędzia deweloperskie uniwersalnej aplikacji systemu Windows są dostarczane z emulatory, których można zobaczyć, jak wygląda aplikacji na różnych urządzeniach. Jeśli chcesz użyć te emulatory, musisz zainstalować tego oprogramowania na komputerze fizycznym. Fizyczny komputer należy uruchomić Windows 8.1 (x64) Professional edition lub nowszy, i mieć procesor obsługujący funkcję Hyper-V klienta i translację adresów drugiego poziomu (SLAT). Nie można użyć emulatorów, po zainstalowaniu programu Visual Studio na maszynie wirtualnej.  
  
 Poniżej przedstawiono listę oprogramowania, które są potrzebne:  
  
-   [Windows 10](http://windows.microsoft.com/windows/downloads). Visual Studio 2017 obsługuje programowanie platformy uniwersalnej systemu Windows tylko w systemie Windows 10. Aby uzyskać więcej informacji, zobacz Visual Studio [obsługiwane platformy](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs) i [wymagania systemowe](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).   
  
-   [Visual Studio](https://www.visualstudio.com/downloads/). Należy również opcjonalne obciążenie rozwoju platformy uniwersalnej systemu Windows.  

     ![Obciążenie platformy uniwersalnej systemu Windows](media/uwp_workload.png)
  
Po zainstalowaniu tego oprogramowania, musisz włączyć urządzenia z systemem Windows 10 na potrzeby programowania. Zobacz [włączyć urządzenia na potrzeby programowania](/windows/uwp/get-started/enable-your-device-for-development). Nie są już potrzebne licencję dewelopera dla każdego urządzenia z systemem Windows 10.  
    
## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows  
Wybierz język programowanie preferowanego języka C#, Visual Basic, C++ lub JavaScript umożliwiające utworzenie aplikacji platformy uniwersalnej systemu Windows dla urządzeń z systemem Windows 10. Odczyt [tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app) lub Obejrzyj [narzędzi dla systemu Windows 10 — omówienie](http://channel9.msdn.com/Series/ConnectOn-Demand/229) wideo.
  
Jeśli masz istniejące aplikacje Sklepu Windows 8.1, aplikacje Windows Phone 8.1 lub aplikacji uniwersalnych systemu Windows, które zostały utworzone za pomocą programu Visual Studio 2015, konieczne będzie port tych aplikacji, aby użyć najnowszej platformy uniwersalnej systemu Windows. Zobacz [przenoszenia ze środowiska wykonawczego systemu Windows 8.x do platformy uniwersalnej systemu Windows](/windows/uwp/porting/w8x-to-uwp-root).
  
Po utworzeniu aplikacji uniwersalnych systemu Windows, należy spakować aplikację, aby ją zainstalować na urządzeniu z systemem Windows 10 lub przesłać je do Sklepu Windows. Zobacz [pakowanie aplikacji](/windows/uwp/packaging/index).

## <a name="see-also"></a>Zobacz także
[Tworzenie aplikacji mobilnych na wiele platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)  
