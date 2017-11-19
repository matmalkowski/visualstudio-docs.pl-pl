---
title: CommentMarkProfile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0cb46497c8e00cedeb4056571d8fa1d19eb26c0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
`CommentMarkProfile` Funkcja wstawia znacznik liczbowych i ciągu tekstowego w pliku Vsp. Dla tego znaku i komentarza do wstawienia, profilowanie dla wątku, który zawiera `CommentMarkProfile` funkcji musi mieć wartość ON.  
  
## <a name="syntax"></a>Składnia  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lMarker`  
  
 Liczbowa znacznika do wstawienia. Znacznika musi być większa lub równa 0 (zero).  
  
 `szComment`  
  
 Wskaźnik do ciągu tekstowego do wstawienia. Ciąg musi być mniejsza niż 256 znaków włącznie z terminatorem NULL.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
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
  
 Znaczniki profilu są globalne w zakresie. Na przykład profilu znacznik wstawiony w jeden wątek może służyć do oznaczania początek lub koniec segmentu danych w którymkolwiek wątku w pliku Vsp.  
  
> [!IMPORTANT]
>  CommentMarkProfile metody można użyć tylko z Instrumentacji.  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Informacji o funkcji  
  
|||  
|-|-|  
|**Nagłówek**|Obejmują VSPerf.h|  
|**Biblioteka**|Użyj VSPerf.lib|  
|**Unicode**|Zaimplementowane jako `CommentMarkProfileW` (Unicode) i `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje CommentMarkProfile wywołania funkcji. W przykładzie założono użycie makra ciąg Win32 i ustawienia kompilatora Unicode w celu określenia, czy kod wywołuje [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] wywołania funkcji.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy API profilera Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)