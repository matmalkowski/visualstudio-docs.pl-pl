---
title: Dołączanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98e18456ad4665359e33d7a9b5f064585f8195be
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="attach"></a>Dołącz
VSPerfCmd.exe **Attach** opcji rozpoczyna próbki profilowanie uruchomiony proces określony przez identyfikator PID procesu.  
  
 Aby użyć **Attach** opcji, należy określić **próbki** w opcji uruchamiania metody.  
  
> [!NOTE]
>  Jeśli **Start** określono opcję z **Crosssession** opcję wszelkie wywołania **VSPerfCmd /Attach** lub **VSPerfCmd /Detach** musi Określ również **Crosssession**.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ProcessID`  
 Identyfikator PID procesu uruchomionego procesu. Identyfikator PID uruchomionego procesu znajduje się na karcie Procesy Menedżera zadań systemu Windows.  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Następujące **VSPerfCmd** opcje można łączyć z **Attach** opcji w jednym wierszu polecenia.  
  
 **Crosssession**  
 Włącza profilowanie aplikacji w sesji innej niż sesji logowania. Jeśli wymagane **Start** określono opcję z **Crosssession** opcji.  
  
 **Uruchom:** `Method`  
 Inicjuje sesję wiersza polecenia profilera i ustawia określonej metody profilowania.  
  
 **TargetCLR**  
 Określa wersję programu .NET Framework wspólnego języka środowiska uruchomieniowego (CLR) do profilu, gdy więcej niż jedna wersja jest ładowany w sesji profilowania. Domyślnie jest profilowane pierwszy załadowano wersję.  
  
 **GlobalOn GlobalOff**  
 Wznawia (**GlobalOn**) lub wstrzymuje (**GlobalOff**) profilowania, ale nie kończy się sesja profilowania.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Wznawia (**ProcessOn**) lub wstrzymuje (**ProcessOff**) profilowania dla określonego procesu.  
  
## <a name="interval-options"></a>Opcje interwału  
 W wierszu polecenia Attach można określić jedną z następujących opcji interwału próbkowania. Domyślny interwał próbkowania wynosi 10 000 000 cykli zegara procesora.  
  
 **Czasomierz**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:** Zdarzenia]**licznika**[**:**`Name`,`Reload`,`FriendlyName`]  
 Określa liczbę i typ interwału próbkowania.  
  
-   **Czasomierz** — przykłady co `Cycles` cykle zegara procesora. Jeśli `Cycles` nie zostanie określony, 10 000 000 cykle są używane.  
  
-   **PF** — przykłady co `Events` błędów stron. Jeśli `Events` nie jest określona, używane są 10 błędów stron.  
  
-   **Sys** — przykłady co `Events` wywołań do systemu operacyjnego. Jeśli `Events` nie zostanie określony, 10 wywołań systemowych są używane.  
  
-   **Licznik** — przykłady co `Reload` liczba wydajności procesora CPU licznika określony przez `Name`. Opcjonalnie `FriendlyName` można określić ciąg do użycia w nagłówku kolumny raportów profilera.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak dołączyć do działającego wystąpienia aplikacji o identyfikatorze procesu 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)