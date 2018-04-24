---
title: SuspendProfile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b807076e56037344a360fb93f89da46eba1221a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="suspendprofile"></a>SuspendProfile
`SuspendProfile` Metody zwiększa Licznik wstrzymań/wznowień dla określonego poziomu profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
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
 Poniższy przykład przedstawia metodę SuspendProfile. W tym przykładzie założono wprowadzono proces lub wątek identyfikowane przez poprzednie wywołanie StartProfile [PROFILE_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy API profilera Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)