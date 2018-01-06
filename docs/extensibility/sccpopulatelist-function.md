---
title: Funkcja SccPopulateList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateList
helpviewer_keywords: SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 474bb834d36661c7cd85b98db78c13f619d7cba6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccpopulatelist-function"></a>Funkcja SccPopulateList
Ta funkcja aktualizuje listę pliki dla polecenia kontroli konkretnego źródła i dostarcza stan kontroli źródła na wszystkie pliki danego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Nwykonywane  
 [in] Polecenie kontroli źródła, które zostaną zastosowane do wszystkich plików w `lpFileNames` tablicy (zobacz [kod polecenia](../extensibility/command-code-enumerator.md) listę poleceń możliwe).  
  
 To  
 [in] Liczba plików w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, znane IDE.  
  
 pfnPopulate  
 [in] Funkcja wywołania zwrotnego IDE do wywołania do dodawania i usuwania plików (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) szczegółowe informacje).  
  
 pvCallerData  
 [in] Wartość, która ma zostać przekazane bez zmian funkcji wywołania zwrotnego.  
  
 lpStatus  
 [w, out] Tablica wtyczka do kontroli źródła do zwrócenia flagi stanu dla każdego pliku.  
  
 fOptions  
 [in] Polecenie flagi (zobacz sekcję "PopulateList flagi" [flag bitowych używane przez określonego polecenia](../extensibility/bitflags-used-by-specific-commands.md) szczegółowe informacje).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja sprawdza, czy lista plików dla jego bieżący stan. Używa `pfnPopulate` funkcja wywołania zwrotnego, aby powiadomić wywołującego, jeśli plik nie pasuje do kryteriów dla `nCommand`. Na przykład, jeśli polecenie jest `SCC_COMMAND_CHECKIN` i nie został wyewidencjonowany pliku na liście, a następnie wywołania zwrotnego służy do informowania wywołującego. Czasami wtyczkę kontroli źródła może się okazać innych plików, które może być częścią polecenie i dodaj je. Umożliwia to na przykład Visual Basic użytkownika wyewidencjonować plik bmp, który jest używany przez jego projekt, ale nie ma w pliku projektu Visual Basic. Użytkownik wybierze **uzyskać** w IDE. IDE spowoduje wyświetlenie listy wszystkich plików, które uważa, że użytkownik może uzyskać, ale przed listy jest wyświetlany, `SccPopulateList` funkcja jest wywoływana, aby upewnić się, listy, który będzie wyświetlany jest aktualny.  
  
## <a name="example"></a>Przykład  
 IDE tworzy listę plików, które uważa, że użytkownik może uzyskać. Przed wyświetleniem tej listy, wywołuje `SccPopulateList` działać, zapewniając możliwość wtyczkę kontroli źródła dodawania i usuwania plików z listy. Wtyczka modyfikuje listę przez wywołanie funkcji wywołania zwrotnego danego (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) więcej szczegółów).  
  
 Wtyczka kontynuuje wywoływanie `pfnPopulate` funkcji, która dodaje i usuwa pliki, dopóki nie zostało zakończone, a następnie zwraca `SccPopulateList` funkcji. IDE można następnie wyświetlić listę jej. `lpStatus` Tablicy reprezentuje wszystkie pliki w oryginalnej listy przekazano IDE. Wtyczka wypełnienia w stanie we wszystkich tych plików dodatkowo wprowadzania użycie funkcji wywołania zwrotnego.  
  
> [!NOTE]
>  Wtyczka do kontroli źródła zawsze może po prostu zwracać bezpośrednio z tej funkcji, pozostawiając na liście, ponieważ jest on. Jeśli wtyczka implementuje tę funkcję, może on wskazywać na to, ustawiając `SCC_CAP_POPULATELIST` flag bitowych możliwości w pierwszym wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md). Domyślnie wtyczka powinien zawsze założono, że wszystkie elementy przekazywany są plikami. Jednak jeśli ustawia IDE `SCC_PL_DIR` oflagowane w `fOptions` parametru, wszystkie elementy przekazywany mają być traktowane jako katalogów. Wtyczkę należy dodać wszystkie pliki, które należy w katalogach. Nigdy nie przejdzie IDE w kombinację plików i katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Używane przez określonego polecenia flag bitowych](../extensibility/bitflags-used-by-specific-commands.md)   
 [Polecenie kodu](../extensibility/command-code-enumerator.md)