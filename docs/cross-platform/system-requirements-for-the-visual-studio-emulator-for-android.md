---
title: "Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: def17f215bd157da8d0e31f400e6b353a4d38f12
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android
Visual Studio Emulator for Android działa jako maszyny wirtualnej w funkcji Hyper-V, technologii wirtualizacji systemu Windows 8 i nowszych. Aby uruchomić emulatora, komputer musi spełniać wymagań dotyczących uruchamiania funkcji Hyper-V, zgodnie z opisem w tym temacie.  
  
 Program instalacyjny próbuje dyskretnie konfigurowanie wymagań wstępnych dla Ciebie po zainstalowaniu emulatora. Gdy Instalator pomyślnie konfiguruje wymagania wstępne, po prostu emulator działa zgodnie z oczekiwaniami. W przeciwnym razie należy ręcznie włączyć te wymagania wstępne. W przypadku ręcznego konfigurowania wymagań wstępnych, narzędzia i kroki są te same kroki opisane [tutaj](/previous-versions/windows/apps/jj863509\(v=vs.105\)) dla emulatora Windows Phone.  
  
> [!IMPORTANT]
>  Program instalacyjny dla emulatora sprawdza wymagania wstępne dotyczące uruchamiania programu Visual Studio Emulator for Android. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są dostępne, ale go nie wymaga.  
  
 Ten temat zawiera następujące sekcje.  
  
-   [Quick Checklist](#Checklist)  
  
-   [Wymagania systemowe](#System)  
  
-   [Wymagania dotyczące sieci](#Network)  
  
-   [Wymagania dotyczące funkcji Hyper-V](#HyperV)  
  
-   [Uruchamianie emulatora z rozruchowego dysku VHD nie jest obsługiwane.](#BootableVHD)  
  
-   [Funkcja Hyper-V wymaga bez kompresji i szyfrowania plików](#Files)  
  
##  <a name="Checklist"></a> Lista kontrolna szybkiego  
 Oto lista kontrolna szybkiego wymagania dotyczące uruchamiania programu Visual Studio Emulator for Android. Aby uzyskać bardziej szczegółowe informacje Zobacz następne sekcje w tym temacie.  
  
 Wymagania systemowe  
  
-   Obsługa funkcji Hyper-V (zobacz poniższe wymagania funkcji Hyper-V)  
  
-   6 GB lub więcej pamięci RAM.  
  
-   wersji 64-bitowej wersji Pro Windows10 systemu Windows 8, Windows 8.1 lub nowszy  
  
-   Procesor obsługujący instrukcji SSSE3 lub nowszym.  
  
 Wymagania dotyczące sieci  
  
-   DHCP  
  
-   Automatycznie skonfigurowana DNS i ustawień bramy  
  
 Wymagania dotyczące funkcji Hyper-V  
  
-   W systemie BIOS musi być obsługiwane następujące funkcje:  
  
    -   Wirtualizacja sprzętowa  
  
    -   Drugi translacji adresów poziomu (SLAT)  
  
    -   Zapobieganie wykonywaniu danych oparte na sprzęcie (DEP)  
  
-   W systemie Windows funkcji Hyper-V musi być włączona i uruchomiona.  
  
-   Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.  
  
##  <a name="System">Wymagania systemowe</a>  
 Komputer musi spełniać następujące wymagania:  
  
-   Obsługa funkcji Hyper-V (zobacz [wymagania dotyczące funkcji Hyper-V](#HyperV))  
  
-   6 GB lub więcej pamięci RAM.  
  
-   wersja 64-bitowej wersji Pro Windows10 systemu Windows 8, Windows 8.1 lub nowszy.  
  
 Aby sprawdzić wymagania dotyczące pamięci RAM i systemu Windows w Panelu sterowania, wybierz pozycję System i zabezpieczenia, a następnie wybierz pozycję System.  
  
 ![Sprawdź wymagania systemowe](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")  
  
##  <a name="Network">Wymagania dotyczące sieci</a>  
 Sieć musi spełniać następujące wymagania:  
  
-   DHCP  
  
     Emulator wymaga protokołu DHCP, ponieważ konfiguruje się jako osobne urządzenia w sieci za pomocą adresu IP.  
  
-   Automatycznie skonfigurowana DNS i ustawień bramy  
  
     Nie jest możliwe do skonfigurowania ustawień DNS i bramy ręcznie dla emulatora.  
  
 Aby rozwiązać problemy z siecią w emulatorze, zobacz następujące tematy:  
  
-   [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)  
  
##  <a name="HyperV">Wymagania dotyczące funkcji Hyper-V</a>  
 Wymagania dotyczące funkcji Hyper-V w systemie BIOS  
  
 System BIOS komputera musi obsługiwać następujące wymagania i musi być włączone:  
  
-   Wirtualizacja sprzętowa  
  
-   Drugi translacji adresów poziomu (SLAT)  
  
-   Zapobieganie wykonywaniu danych oparte na sprzęcie (DEP)  
  
 Wymagania dotyczące funkcji Hyper-V w systemie Windows  
  
 Gdy komputer i ustawienia systemu BIOS są już skonfigurowane do obsługi funkcji Hyper-V, program instalacyjny włącza i uruchamia funkcji Hyper-V. W przeciwnym razie należy ręcznie włączyć te wymagania.  
  
|Wymaganie|Jak można sprawdzić i włączyć to wymaganie|  
|-----------------|----------------------------------------------|  
|Musi być zainstalowana funkcja Hyper-V|Postępuj zgodnie z instrukcjami tego samego używany do [Włączanie funkcji Hyper-V dla emulatora Windows Phone](https://msdn.microsoft.com/en-us/library/windows/apps/jj863509\(v=vs.105\).aspx).<br /><br /> Sprawdź stan **zarządzania maszynami wirtualnymi funkcji Hyper-V** usługi w przystawce usług.|  
|Musi być uruchomiona funkcja Hyper-V.|Aby uzyskać więcej informacji na temat zarządzania usługami zobacz następujące tematy:<br /><br /> -   [Uruchomić, zatrzymać, wstrzymać, wznowić lub ponowne uruchamianie usługi](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurowanie sposobu uruchamiania usługi](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|  
  
 Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.  
  
 Aby uruchomić program Visual Studio Emulator for Android bez cyklicznego monit o podniesienie uprawnień użytkownika, należy być członkiem lokalnej grupy Administratorzy funkcji Hyper-V. Jeśli masz już administratora lokalnego na komputerze podczas instalacji zestawu SDK, program instalacyjny dla tego zestawu SDK dodaje do grupy Administratorzy funkcji Hyper-V. W przeciwnym razie należy włączyć to wymaganie ręcznie.  
  
 Po uruchomieniu emulatora, jeśli nie jesteś już członkiem grupy Administratorzy funkcji Hyper-V, zostanie wyświetlony monit na dołączenie do grupy (okno dialogowe odwołuje się do emulatora Windows Phone). Dołączenia do grupy wymaga uprawnień administratora.  
  
> [!IMPORTANT]
>  Po dołączeniu do grupy, wylogowania lub ponownie uruchomić system, aby zmiany zostały wprowadzone.  
  
 ![Przyłączanie funkcji Hyper- &#45; Grupy zabezpieczeń Administratorzy V](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")  
  
 Aby samodzielnie ręcznie dodać do grupy, otwórz lokalnych użytkowników i grup przystawki. Aby uzyskać więcej informacji, zobacz [dodać konto użytkownika do grupy](http://windows.microsoft.com/en-us/windows/add-user-account-to-group#1TC=windows-7). (W tym temacie Windows 7 jest również zastosowanie do systemu Windows 8).  
  
##  <a name="BootableVHD">Uruchamianie emulatora z rozruchowego dysku VHD nie jest obsługiwane.</a>  
 Próby uruchomienia aplikacji w Visual Studio Emulator for Android podczas uruchamiania systemu Windows z rozruchowego dysku VHD, emulator zwykle może zająć kilka minut, aby uruchomić lub nie została uruchomiona. Gdy emulator nie powiedzie się, zostanie wyświetlony następujący komunikat: Wdrażanie aplikacji nie powiodło się. Spróbuj ponownie.  
  
 Ta konfiguracja nie jest obsługiwana. Informacje dotyczące problemów pokrewnych, zobacz [Rozwiązywanie problemów z programu Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Files">Funkcja Hyper-V wymaga bez kompresji i szyfrowania plików</a>  
 Na dysku twardym skonfigurowane przy użyciu systemu plików NTFS pliki wirtualnych dysków twardych, używany przez funkcję Hyper-V należy nieskompresowane i bez szyfrowania. Upewnij się, że następujące katalogi nie są skompresowane lub zaszyfrowane:  
  
-   %localappdata%\Microsoft\XDE  
  
-   C:\Program Files (x86)\Microsoft Emulator Manager  
  
-   C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android  
  
-   %localappdata%\Microsoft\VisualStudioEmulator  
  
 W systemie plików ReFS pliki wirtualnego dysku twardego musi nie mają ustawionego bitu integralności.  
  
## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Wymagania dotyczące sprzętu grafiki przekazywania (Obsługa OpenGL ES)  
 Aby emulatora emulować wywołania do procesora GPU, takich jak zasoby używane przez interfejsy OpenGL ES komputera musi mieć zgodną jednostkę GPU DirectX z zainstalowane odpowiednie sterowniki DirectX.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)