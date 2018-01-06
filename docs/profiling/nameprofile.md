---
title: NameProfile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: be7e6b2e29ed74fe57016bb286b54742b0add632
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="nameprofile"></a>NameProfile
`NameProfile` Funkcja przypisuje ciąg określony proces lub wątek.  
  
 Interfejs API NameProfile jest dostępna tylko w przypadku profilowanie instrumentacji. Interfejs API NameProfile nie jest obsługiwana dla profilowanie próbkowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
  
 Nazwa elementu profilowania. Nazwa jest nieprawidłowa, (co spowoduje NAME_ERROR_INVALID_NAME zwrotu NameProfileA), jeśli:  
  
-   Wskaźnik przekazany NameProfileA jest wartość NULL  
  
-   Dane ciągu pszName rozpoczyna się od numeru  
  
-   Dane ciągu pszName zawiera spację  
  
-   Dane ciągu pszName zawiera żadnego z następujących znaków:,. ' ~! @# $% ^ & * () = [] {} &#124; \\? / <>  
  
 `Level`  
  
 Wskazuje poziom profilu do wydajności, które mogą być stosowane zbierania danych. Następujące **PROFILE_CONTROL_LEVEL** wartości można oznaczać jeden z trzech poziomów do wydajności, które mogą być stosowane zbierania danych:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Globalne ustawienia poziomu dotyczą wszystkich procesów i wątków w przebiegu profilowania.|  
|PROFILE_PROCESSLEVEL|Ustawienie poziomu proces wpływają na wszystkie wątki, które są częścią określony proces.|  
|PROFILE_THREADLEVEL|Wątek profilowania ustawienie poziomu dotyczy określonego wątku.|  
  
 `dwId`  
  
 Identyfikator poziomu profilowania. Proces lub wątek identyfikator, który jest generowany przez system.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Funkcja wskazuje powodzenie lub Niepowodzenie przy użyciu **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących czynności:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|Określony element profilowania nie istnieje.|  
|NAME_ERROR_INVALID_NAME|Nazwa jest nieprawidłowa.|  
|NAME_ERROR_LEVEL_NOEXIST|Profil określony poziom nie istnieje.|  
|NAME_ERROR_NO_SUPPORT|Określona operacja nie jest obsługiwana.|  
|NAME_ERROR_OUTOFMEMORY|Pamięć nie był dostępny do rejestrowania zdarzenia.|  
|NAME_ERROR_REDEFINITION|Nazwa została już przypisana do elementu profilu. Nazwa tej funkcji jest ignorowana.|  
|NAME_ERROR_TEXTTRUNCATED|Tekst nazwa przekracza 32 znaków, łącznie ze znakiem null i dlatego została obcięta.|  
|NAME_OK|Nazwa została pomyślnie zarejestrowana.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko jedną nazwę można przypisać do każdego proces lub wątek. Po nazwie elementu profilowania kolejnych wywołań NameProfile dla tego elementu są ignorowane.  
  
 Jeśli tej samej nazwie znajduje się na inne wątki lub procesy, w raporcie zostaną uwzględnione danych z wszystkich elementów na tym poziomie o tej nazwie.  
  
 Jeśli określisz proces lub wątek inny niż bieżący, należy się upewnić, czy został zainicjowany i uruchomienia przed nadaj jej nazwę. W przeciwnym razie metoda NameProfile kończy się niepowodzeniem.  
  
> [!IMPORTANT]
>  Funkcje CreateProcess() i interfejsu API CreateThread() może zwrócić przed wątku lub procesu jest zainicjowany.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacji o funkcji  
  
|||  
|-|-|  
|**Nagłówek**|Obejmują VSPerf.h|  
|**Biblioteka**|Użyj VSPerf.lib|  
|**Unicode**|Zaimplementowane jako `NameProfileW` (Unicode) i `NameProfileA` (ANSI).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje NameProfile wywołania funkcji. W przykładzie założono użycie makra ciąg Win32 i ustawienia kompilatora ANSI, czy kod wywołuje ANSI włączone funkcji.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy API profilera Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)