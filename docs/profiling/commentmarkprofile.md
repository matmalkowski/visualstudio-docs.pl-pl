---
title: CommentMarkProfile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aaae7a6ce1185426f23a8182ddcdf0c969f39a4b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691046"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
`CommentMarkProfile` Funkcja wstawia znacznik liczbowych i ciągu tekstowego w. *Vsp* pliku. Dla tego znaku i komentarza do wstawienia, profilowanie dla wątku, który zawiera `CommentMarkProfile` funkcji musi mieć wartość ON.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametry  
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
 Stan profilowania dla wątku, który zawiera funkcję profilu znak musi być na, jeśli znaczniki i komentarze wstawione przy użyciu polecenia VSInstr znak lub funkcje (CommentMarkAtProfile, CommentMarkProfile lub MarkProfile).  
  
 Znaczniki profilu są globalne w zakresie. Na przykład profilu znacznik wstawiony w jeden wątek można oznaczyć początek lub koniec segmentu danych w którymkolwiek wątku w. *vsp* pliku.  
  
> [!IMPORTANT]
>  CommentMarkProfile metody można użyć tylko z Instrumentacji.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacji o funkcji  
  
|||  
|-|-|  
|**Nagłówek**|Obejmują VSPerf.h|  
|**Biblioteka**|Użyj VSPerf.lib|  
|**Unicode**|Zaimplementowane jako `CommentMarkProfileW` (Unicode) i `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje CommentMarkProfile wywołania funkcji. W przykładzie założono użycie makra ciąg Win32 i ustawienia kompilatora Unicode w celu określenia, czy kod wywołuje [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] wywołania funkcji.  
  
```cpp  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio interfejsy API profilera (native)](../profiling/visual-studio-profiler-api-reference-native.md)