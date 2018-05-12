---
title: ResumeProfile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1572f1473e2da8f84887b6571755dc259e19762b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="resumeprofile"></a>ResumeProfile
`ResumeProfile` Metody zmniejsza wstrzymań/wznowień licznika dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
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
 Początkowa wartość licznika wstrzymań/wznowień to 0. Każde wywołanie SuspendProfile dodaje 1 Liczba wstrzymań/wznowień; Każde wywołanie ResumeProfile odejmuje 1.  
  
 Gdy liczba wstrzymań/wznowień jest większa niż 0, stan wstrzymań/wznowień poziomu został WYŁĄCZONY. Gdy ta liczba jest mniejsza lub równa 0, stan wstrzymań/wznowień ma wartość ON.  
  
 Podczas uruchamiania i zatrzymywania stan i stan wstrzymań/wznowień są na, stan profilowania poziomu ma wartość ON. Dla wątku być profilowane, proces globalnych i Stany poziomu wątku dla wątku wszystkie muszą być ON.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacji o funkcji  
 Nagłówek: Zadeklarowany w VSPerf.h  
  
 Importuj biblioteki: VSPerf.lib  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia funkcję ResumeProfile. W przykładzie założono wprowadzono dla tego samego wątku lub procesu identyfikowane przez wywołanie do metody SuspendProfile [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```cpp  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy API profilera Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)