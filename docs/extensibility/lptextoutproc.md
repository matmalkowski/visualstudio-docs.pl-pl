---
title: LPTEXTOUTPROC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 235d98ba6a5ca665857b8a18db5ca823ecc0c7c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Gdy użytkownik wykonuje operację na kontroli źródła z wewnątrz zintegrowane środowisko programistyczne (IDE), wtyczkę kontroli źródła może być błąd lub komunikatów o stanie dotyczących operacji przekazywania. Wtyczki można wyświetlić jego własnej pola komunikatów w tym celu. Jednak dla więcej bezproblemową integrację, wtyczki można przekazać ciągi do środowiska IDE, następnie wyświetli je w jego natywnej sposób wyświetlania informacji o stanie. Jest to mechanizm `LPTEXTOUTPROC` wskaźnik funkcji. IDE implementuje tej funkcji (opisany bardziej szczegółowo poniżej) do wyświetlania błędów i stanów.  
  
 IDE przekazuje do kontroli źródła wtyczek wskaźnik funkcji do tej funkcji jako `lpTextOutProc` podczas wywoływania parametru [SccOpenProject](../extensibility/sccopenproject-function.md). Podczas operacji SCC, na przykład w trakcie wywołania [SccGet](../extensibility/sccget-function.md) obejmujące wiele plików, wtyczka może wywołać `LPTEXTOUTPROC` funkcja okresowo przekazywanie ciągi do wyświetlenia. IDE te parametry mogą być wyświetlane na pasku stanu, w oknie danych wyjściowych lub w osobnym oknie komunikatu, zależnie od potrzeb. Opcjonalnie, może istnieć możliwość wyświetlania komunikatów z IDE **anulować** przycisku. Dzięki temu użytkownik anuluje operację, i daje możliwość przekazywania tych informacji do wtyczki środowiska IDE.  
  
## <a name="signature"></a>Podpis  
 IDE wyjściowy się, że funkcja ma następującą sygnaturą:  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parametry  
 display_string  
 Ciąg tekstowy do wyświetlenia. Ten ciąg nie powinna kończyć karetki zwracany lub wysuwu wiersza.  
  
 mesg_type  
 Typ komunikatu. W poniższej tabeli wymieniono obsługiwane wartości tego parametru.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Komunikat jest uznawane za informacje, ostrzeżenia lub błędu.|  
|`SCC_MSG_STATUS`|Komunikat wyświetlany stan i mogą być wyświetlane na pasku stanu.|  
|`SCC_MSG_DOCANCEL`|Wysyłane nie ciąg z komunikatem.|  
|`SCC_MSG_STARTCANCEL`|Zaczyna się wyświetlanie **anulować** przycisku.|  
|`SCC_MSG_STOPCANCEL`|Zatrzymuje wyświetlanie **anulować** przycisku.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pyta IDE operacji w tle jest anulowane: zwraca IDE `SCC_MSG_RTN_CANCEL` Jeśli operacja została anulowana; w przeciwnym razie zwraca `SCC_MSG_RTN_OK`. `display_string` Parametru jest rzutowany jako [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) struktury, która jest dostarczana przez wtyczkę kontroli źródła.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informuje o plik IDE, zanim zostaną pobrane z kontroli wersji. `display_string` Parametru jest rzutowany jako [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) struktury, która jest dostarczana przez wtyczkę kontroli źródła.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Określa, że IDE o pliku po pobraniu z kontroli wersji. `display_string` Parametru jest rzutowany jako [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) struktury, która jest dostarczana przez wtyczkę kontroli źródła.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Określa, że IDE bieżącego stanu operacji w tle. `display_string` Parametru jest rzutowany jako [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) struktury, która jest dostarczana przez wtyczkę kontroli źródła.|  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|Ten ciąg został wyświetlony lub operacja została ukończona pomyślnie.|  
|SCC_MSG_RTN_CANCEL|Użytkownik chce anulować operację.|  
  
## <a name="example"></a>Przykład  
 Załóżmy, że wywołania IDE [SccGet](../extensibility/sccget-function.md) o dwadzieścia nazw plików. Wtyczka do kontroli źródła chce, aby uniemożliwić anulowanie operacji w trakcie pobierania pliku. Po otrzymaniu każdego pliku, wywołuje `lpTextOutProc`, przekazanie jej informacje o stanie dla każdego pliku i wysyła `SCC_MSG_DOCANCEL` komunikatów, jeśli ma ona ma stanu do raportowania. Jeśli w dowolnym momencie wtyczki odbiera wartość zwracana `SCC_MSG_RTN_CANCEL` z IDE, anuluje operację pobierania natychmiast, dzięki czemu nie ma więcej plików są pobierane.  
  
## <a name="structures"></a>Struktury  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_IS_CANCELLED` wiadomości. Jest on używany do komunikacji identyfikator operacji w tle, które zostało anulowane.  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` wiadomości. Jest on używany do komunikacji nazwę pliku o mają zostać pobrane i identyfikator operacji w tle zadań pobierania.  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` wiadomości. Jest on używany do komunikacji wynik pobierania określonego pliku, a także identyfikator operacji w tle, który został pobierania. Zobacz wartości zwracanych przez [SccGet](../extensibility/sccget-function.md) dla w wyniku czego można przydzielić.  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Ta struktura jest wysyłany z `SCC_MSG_BACKGROUND_ON_MESSAGE` wiadomości. Jest on używany do komunikacji przy bieżącym stanie operacji w tle. Stan jest wyrażony jako ciąg do wyświetlania IDE, a `bIsError` wskazuje ważność komunikatu (`TRUE` komunikatu o błędzie; `FALSE` ostrzeżenie lub komunikat informacyjny). Znajduje się również identyfikator wysyłania stanu operacji w tle.  
  
## <a name="code-example"></a>Przykład kodu  
 Poniżej przedstawiono prosty przykład wywołania metody `LPTEXTOUTPROC` do wysyłania `SCC_MSG_BACKGROUND_ON_MESSAGE` wiadomości, pokazujący sposób rzutowania struktury wywołanie.  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego zaimplementowana IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)