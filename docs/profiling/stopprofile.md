---
title: StopProfile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52dd9ccce2d7ea2aab36895c186c25ad5207de7a
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="stopprofile"></a>StopProfile
`StopProfile` Funkcja ustawia licznik 0 (wyłączone) dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Level`  
  
 Wskazuje poziom profilu do wydajności, które mogą być stosowane zbierania danych. Następujące **PROFILE_CONTROL_LEVEL** moduły wyliczające można oznaczać jeden z trzech poziomów do wydajności, które mogą być stosowane zbierania danych:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globalne ustawienia poziomu dotyczą wszystkich procesów i wątków w przebiegu profilowania.|  
|PROFILE_PROCESSLEVEL|Ustawienie poziomu proces wpływają na wszystkie wątki, które są częścią określony proces.|  
|PROFILE_THREADLEVEL|Wątek profilowania ustawienie poziomu dotyczy określonego wątku.|  
  
 `dwId`  
  
 Proces lub wątek identyfikator generowany przez system.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Funkcja wskazuje powodzenie lub Niepowodzenie przy użyciu **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących czynności:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Identyfikator elementu profilowania nie istnieje.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Określony poziom profilowania nie istnieje.|  
|PROFILE_ERROR_MODE_NEVER|Tryb profilowania została ustawiona na nie, gdy została wywołana funkcja.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profilowania wywołanie funkcji, profilowania poziomu lub kombinacja wywołania i poziomu nie została jeszcze zaimplementowana.|  
|PROFILE_OK|Wywołanie zakończyło się pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 StartProfile i StopProfile kontrolować stan uruchamiania i zatrzymywania profilowania poziomu. Wartość domyślna uruchamiania i zatrzymywania wynosi 1. Wartość początkowa można zmienić w rejestrze. Każde wywołanie StartProfile ustawia uruchamiania i zatrzymywania 1; Każde wywołanie StopProfile ustawia ją na 0.  
  
 Podczas uruchamiania/zatrzymywania jest większa niż 0, stan uruchamiania i zatrzymywania poziomu ma wartość ON. Gdy jest mniejsza lub równa 0, uruchamiania i zatrzymywania stan został WYŁĄCZONY.  
  
 Podczas uruchamiania i zatrzymywania stan i stan wstrzymań/wznowień są na, stan profilowania poziomu ma wartość ON. Dla wątku być profilowane, proces globalnych i poziomu stany wątku dla wątku musi mieć wartość ON.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacji o funkcji  
 Nagłówek: Zadeklarowany w VSPerf.h  
  
 Importuj biblioteki: VSPerf.lib  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metodę StopProfile. W przykładzie założono wprowadzono dla tego samego wątku lub procesu identyfikowane przez wywołanie do metody StartProfile [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```cpp  
void ExerciseStopProfile()  
{  
    // StartProfile and StopProfile control the   
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy API profilera Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)