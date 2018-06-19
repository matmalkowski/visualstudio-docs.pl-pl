---
title: 'Porady: określanie wersji programu .NET Framework do debugowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb8da54b53814e7f044c67855e8071c627cf2e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476676"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Porady: określanie wersji programu .NET Framework do debugowania
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] Debuger obsługuje debugowanie starsze wersje programu Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] oraz bieżącej wersji. Po uruchomieniu aplikacji w programie Visual Studio debuger zawsze można zidentyfikować poprawną wersję [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] debugowania aplikacji. Jeśli aplikacja jest już uruchomiona i używana będzie **dołączyć do**, debuger może nie zawsze można zidentyfikować starszej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. W takim przypadku otrzymasz komunikat o błędzie informujący,  
  
 Debuger wykonał nieprawidłowe założenie dotyczące [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji aplikacji zamierza użyć.  
  
 W rzadkich przypadkach można ustawić klucz rejestru, aby wskazać debugera wersji do użycia.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Aby określić .NET Framework w wersji do debugowania  
  
1.  Szukaj w katalogu Windows\Microsoft.NET\Framework można odnaleźć wersji programu .NET Framework na komputerze jest zainstalowany. Numery wersji wyglądać mniej więcej tak:  
  
     `V1.1.4322`  
  
     Określ liczbę poprawnej wersji i zapisz go.  
  
2.  Uruchom **Edytora rejestru** (regedit).  
  
3.  W **Edytora rejestru**, otwórz HKEY_LOCAL_MACHINE folder.  
  
4.  Przejdź do: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine i kliknij przycisk **nowy klucz**. Nazwa nowego klucza `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Po nawigowania do {449EC4CC-30D2-4032-9256-EE18EB41B62B}, Szukaj w **nazwa** kolumny i Znajdź klucz CLRVersionForDebugging.  
  
    1.  Jeśli klucz nie istnieje, kliknij prawym przyciskiem myszy {449EC4CC-30D2-4032-9256-EE18EB41B62B} i kliknij przycisk **nową wartość ciągu**. Kliknij prawym przyciskiem myszy nową wartość ciągu, kliknij przycisk **zmienić**i wpisz `CLRVersionForDebugging`.  
  
6.  Kliknij dwukrotnie **CLRVersionForDebugging**.  
  
7.  W **Edytowanie ciągu** wpisz numer wersji .NET Framework w **wartość** pole. Na przykład: V1.1.4322  
  
8.  Kliknij przycisk **OK**.  
  
9. Zamknij **Edytora rejestru**.  
  
     Jeśli nadal zostanie wyświetlony komunikat o błędzie podczas uruchamiania debugowania, sprawdź, czy wprowadzony numer wersji, który jest poprawnie w rejestrze. Sprawdź również, że używasz wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] obsługiwane przez program Visual Studio. Debuger jest zgodny z bieżącą wersją .NET Framework i poprzednich wersji, ale może nie być zgodne wprzód w przyszłych wersjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)