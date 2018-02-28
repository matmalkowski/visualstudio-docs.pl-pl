---
title: QUERYCHANGESFUNC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 43add362011b31ce695e9a8d9e77d6ca2dedb0e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Jest to funkcja wywołania zwrotnego używane przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operacji wylicza Kolekcja nazw plików i sprawdź stan każdego pliku.  
  
 `SccQueryChanges` Uzyskuje listę plików i wskaźnika do funkcji `QUERYCHANGESFUNC` wywołania zwrotnego. Wtyczka do kontroli źródła wylicza za pośrednictwem danej listy i zawiera stan (za pośrednictwem tego wywołania zwrotnego) dla każdego pliku na liście.  
  
## <a name="signature"></a>Podpis  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] `pvCallerData` Parametr przekazany przez wywołującego (IDE) do [SccQueryChanges](../extensibility/sccquerychanges-function.md). Wtyczka do kontroli źródła należy wykonać żadnych założeń dotyczące zawartości tej wartości.  
  
 pChangesData  
 [in] Wskaźnik do [struktury QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) struktury opisujące zmian w pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 IDE zwraca kod błędu odpowiednie:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Kontynuować przetwarzania.|  
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|  
|SCC_E_xxx|Wszystkie odpowiednie błąd SCC należy zatrzymać przetwarzania.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a>Struktura QUERYCHANGESDATA  
 Struktura przekazana dla każdego pliku wygląda następująco:  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 Rozmiar tej struktury (w bajtach).  
  
 lpFileName  
 Oryginalna nazwa pliku dla tego elementu.  
  
 dwChangeType  
 Kod wskazujący stan pliku:  
  
|Kod|Opis|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Nie można sprawdzić, co się zmieniło.|  
|`SCC_CHANGE_UNCHANGED`|Brak zmian nazwy dla tego pliku.|  
|`SCC_CHANGE_DIFFERENT`|Plik z innej tożsamości, ale takiej samej nazwie istnieje w bazie danych.|  
|`SCC_CHANGE_NONEXISTENT`|Plik nie istnieje w bazie danych lub lokalnie.|  
|`SCC_CHANGE_DATABASE_DELETED`|Plik został usunięty z bazy danych.|  
|`SCC_CHANGE_LOCAL_DELETED`|Plik został usunięty lokalnie, ale plik nadal istnieje w bazie danych. Jeśli nie można ustalić, zwróć `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Plik dodany do bazy danych, ale nie istnieje lokalnie.|  
|`SCC_CHANGE_LOCAL_ADDED`|Plik nie istnieje w bazie danych i jest plikiem lokalnym.|  
|`SCC_CHANGE_RENAMED_TO`|Plik przeniesiony lub w bazie danych jako `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Plik przeniesiony lub w bazie danych z `lpLatestName`; Jeśli jest zbyt drogie śledzić, zwróć flagi, takich jak `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Bieżąca nazwa pliku dla tego elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego zaimplementowana IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Kody błędów](../extensibility/error-codes.md)