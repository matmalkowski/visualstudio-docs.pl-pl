---
title: CommentMarkAtProfile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0eaaac47470378730c526b01b2ce2b637af5cd6
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36233701"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile` Metody wstawia wartość sygnatury czasowej, znacznik liczbowych i ciąg komentarza w. *Vsp* pliku. Wartość znacznika czasu może być używana do synchronizowania zdarzenia zewnętrzne. Dla tego znaku i komentarza do wstawienia profilowanie dla wątku, który zawiera funkcję CommentMarkAtProfile musi mieć wartość ON.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dnTimestamp`  
  
 64-bitowa liczba całkowita, która reprezentuje wartość sygnatury czasowej.  
  
 `lMarker`  
  
 Liczbowa znacznika do wstawienia. Znacznika musi być większa lub równa 0 (zero).  
  
 `szComment`  
  
 Wskaźnik do ciągu tekstowego do wstawienia. Ciąg musi być mniejsza niż 256 znaków włącznie z terminatorem NULL.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości wartość/powrotu  
 Funkcja wskazuje powodzenie lub Niepowodzenie przy użyciu **PROFILE_COMMAND_STATUS** wyliczenia. Zwracana wartość może być jedną z następujących czynności:  
  
|Moduł wyliczający|Opis|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Parametr jest mniejsza lub równa 0. Te wartości są zastrzeżone. Znaczników i komentarzy nie są rejestrowane.|  
|MARK_ERROR_MODE_NEVER|Tryb profilowania została ustawiona na nie, gdy została wywołana funkcja. Znaczników i komentarzy nie są rejestrowane.|  
|MARK_ERROR_MODE_OFF|Tryb profilowania została ustawiona wartość OFF, gdy funkcja została wywołana. Znaczników i komentarzy nie są rejestrowane.|  
|MARK_ERROR_NO_SUPPORT|Brak obsługi znacznik, w tym kontekście. Znaczników i komentarzy nie są rejestrowane.|  
|MARK_ERROR_OUTOFMEMORY|Pamięć nie był dostępny do rejestrowania zdarzenia. Znaczników i komentarzy nie są rejestrowane.|  
|MARK_TEXTTOOLONG|Ciąg przekracza maksymalną 256 znaków. Ciąg komentarz został obcięty i znaczników i komentarzy są rejestrowane.|  
|MARK_OK|MARK_OK jest zwracany, informując o powodzeniu.|  
  
## <a name="remarks"></a>Uwagi  
 Stan profilowania dla wątku, który zawiera funkcję profilu znak musi być na, jeśli znaczniki i komentarze wstawione przy użyciu polecenia znak lub z funkcji API (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile). Znaczniki profilu są globalne w zakresie. Na przykład profilu znacznik wstawiony w jeden wątek może służyć do oznaczania początek lub koniec segmentu danych w którymkolwiek wątku w pliku Vsp.  
  
> [!IMPORTANT]
>  Metody CommentMarkAtProfile powinien być używany z tylko instrumentacji.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Informacji o funkcji  
  
|||  
|-|-|  
|**Nagłówek**|Obejmują *VSPerf.h*|  
|**Biblioteka**|Użyj *VSPerf.lib*|  
|**Unicode**|Zaimplementowane jako CommentMarkAtProfileW (Unicode) i CommentMarkAtProfileA (ANSI).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia użycie CommentMarkAtProfile wywołania funkcji ogólnego. W przykładzie założono użycie makra ciąg Win32 i ustawienia kompilatora ANSI, czy kod wywołuje ANSI włączone funkcji.  
  
```cpp  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie w Visual Studio API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)