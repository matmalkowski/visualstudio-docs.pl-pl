---
title: Funkcja SccSetOption | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 70fe624984adce58191ee7d354185eac0bb527ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccsetoption-function"></a>Funkcja SccSetOption
Ta funkcja ustawia opcje kontrolujące zachowanie wtyczkę kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 nOption  
 [in] Opcja, która jest ustawiona.  
  
 dwVal  
 [in] Ustawienia opcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie ustawiono opcję.|  
|SCC_I_SHARESUBPROJOK|Jeśli zwrócony `nOption` został `SCC_OPT_SHARESUBPROJ` i IDE ustawić folder docelowy umożliwia wtyczkę kontroli źródła.|  
|SCC_E_OPNOTSUPPORTED|Opcja nie została ustawiona i nie powinno być stosowane.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołanie tej funkcji do sterowania zachowaniem wtyczkę kontroli źródła. Pierwszy parametr `nOption`, wskazuje wartość, która jest ustawiona, a druga, `dwVal`, wskazuje, co należy zrobić z daną wartością. Wtyczka przechowuje te informacje skojarzone z `pvContext``,` tak IDE musi wywoływać tej funkcji po wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md) (ale niekoniecznie po każdym wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Podsumowanie opcji i ich wartości:  
  
|`nOption`|`dwValue`|Opis|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Włącza/wyłącza tła zdarzeń usługi kolejkowania wiadomości.|  
|`SCC_OPT_USERDATA`|Dowolne wartości|Określa wartość użytkownika do przekazania do [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funkcja wywołania zwrotnego.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Wskazuje, czy IDE obsługuje obecnie trwa anulowanie operacji.|  
|`SCC_OPT_NAMECHANGEPFN`|Wskaźnik do [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funkcja wywołania zwrotnego|Ustawia wskaźnik do funkcji wywołania zwrotnego zmiany nazwy.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Wskazuje, czy IDE umożliwia sprawdzanie poza jego pliki ręcznie (za pośrednictwem interfejsu użytkownika kontroli źródła) lub czy one musi być wyewidencjonowany tylko za pośrednictwem wtyczkę kontroli źródła.|  
|`SCC_OPT_SHARESUBPROJ`|Brak|Jeśli wtyczka do kontroli źródła umożliwia IDE określić folder lokalny projektu, zwraca wtyczki `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Jeśli `nOption` jest `SCC_OPT_EVENTQUEUE`, IDE jest wyłączenie (lub ponowne włączenie) przetwarzanie w tle. Na przykład podczas kompilacji, IDE nakazać zatrzymania przetwarzania na bezczynności dowolnego rodzaju wtyczkę kontroli źródła. Po kompilacji będzie on ponownie włączyć przetwarzanie w tle aktualności plug w kolejce zdarzeń. Odpowiadający `SCC_OPT_EVENTQUEUE` wartość `nOption`, istnieją dwie możliwe wartości `dwVal`, to znaczy, `SCC_OPT_EQ_ENABLE` i `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Jeśli wartość `nOption` jest `SCC_OPT_HASCANCELMODE`, IDE pozwala użytkownikom na anulowanie operacji długo. Ustawienie `dwVal` do `SCC_OPT_HCM_NO` (domyślnie) wskazuje, że IDE ma nie w trybie Anuluj. Wtyczka do kontroli źródła musi oferować własny przycisk Anuluj, jeśli chce, aby użytkownik mógł anulować. `SCC_OPT_HCM_YES`Wskazuje, czy IDE pozwala, aby anulować operację dzięki SCC wtyczka nie trzeba wyświetlić własny przycisk Anuluj. Jeśli ustawia IDE `dwVal` do `SCC_OPT_HCM_YES`, jest gotowa na odpowiadanie na `SCC_MSG_STATUS` i `DOCANCEL` komunikaty wysyłane do `lpTextOutProc` funkcja wywołania zwrotnego (zobacz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Jeśli środowisko IDE nie ustaw wartość tej zmiennej, wtyczkę najlepiej nie przesyłać tych dwóch komunikatów.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Jeśli ustawiono nOption `SCC_OPT_NAMECHANGEPFN`i obie źródła pozwalają na to wtyczka do kontroli i IDE, wtyczka może faktycznie zmiany nazwy lub przeniesienia pliku podczas operacji kontroli źródła. `dwVal` Zostanie ustawiona na wskaźnik funkcji typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Podczas operacji kontroli źródła wtyczka może wywołanie tej funkcji, przekazując trzy parametry. Są to stara nazwa pliku, Nowa nazwa (z w pełni kwalifikowana) tego pliku i wskaźnika do informacji, które ma znaczenie dla IDE (z w pełni kwalifikowanej ścieżki). IDE wysyła w ostatnim wskaźnik przez wywołanie metody `SccSetOption` z `nOption` ustawioną `SCC_OPT_USERDATA`, z `dwVal` wskazujący danych. Obsługa tej funkcji jest opcjonalne. Podłączenia VSSCI — że używa tę możliwość musi inicjować funkcja wskaźnik i użytkownika danych zmienne do `NULL`, i nie musi wywoływać funkcję zmiany nazwy, chyba że przekazania jeden. On również powinna być przygotowana do przechowywania wartości podano lub je zmienić w odpowiedzi na nowe wywołanie w celu `SccSetOption`. Ta sytuacja nie występuje w środku operacja polecenia kontroli źródła, ale może się zdarzyć, między poleceń.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Jeśli ustawiono nOption `SCC_OPT_SCCCHECKOUTONLY`, IDE wskazująca, że pliki w projekcie aktualnie otwartych powinien nigdy nie można wyewidencjonować ręcznie za pomocą interfejsu użytkownika systemu kontroli źródła. Zamiast tego pliki powinny wyewidencjonowany tylko za pośrednictwem wtyczka do kontroli źródła pod kontrolą środowiska IDE. Jeśli `dwValue` ma ustawioną wartość `SCC_OPT_SCO_NO`, oznacza, że pliki powinny być traktowane zwykle przez wtyczkę i może zostać wyewidencjonowany do kontroli źródła interfejsu użytkownika. Jeśli `dwValue` ma ustawioną wartość `SCC_OPT_SCO_YES`, następnie tylko wtyczki można wyewidencjonować plików i nie można wywołać interfejsu użytkownika systemu kontroli źródła. Jest to odpowiednie do sytuacji, gdy IDE mieć "pseudo-pliki" sensu wyewidencjonować tylko za pośrednictwem IDE.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Jeśli`nOption` ma ustawioną wartość `SCC_OPT_SHARESUBPROJ`, IDE jest sprawdzenie, czy wtyczkę kontroli źródła można użyć określonego folderu lokalnego, podczas dodawania plików z kontroli źródła. Wartość `dwVal` parametru nie ma znaczenia w tym przypadku. Jeśli wtyczka umożliwia IDE określić folder lokalne miejsce docelowe, gdzie ma zostać dodana pliki ze źródła decyduje o [SccAddFromScc](../extensibility/sccaddfromscc-function.md) nosi nazwę, a następnie wtyczki musi zwracać `SCC_I_SHARESUBPROJOK` podczas `SccSetOption` jest — funkcja wywołuje się. IDE, a następnie używa `lplpFileNames` parametr `SccAddFromScc` funkcji do przekazania w folderze docelowym. Wtyczka korzysta z tego folderu docelowego można umieścić pliki dodane z kontroli źródła. Jeśli wtyczka nie zwraca `SCC_I_SHARESUBPROJOK` podczas `SCC_OPT_SHARESUBPROJ` opcja jest ustawiona, IDE zakłada, że wtyczka możliwość dodawania plików tylko w bieżącym folderze lokalnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)