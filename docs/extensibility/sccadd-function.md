---
title: Funkcja SccAdd | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 52137da9d14920a2fd5213f1110a74d895e51c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccadd-function"></a>Funkcja SccAdd
Ta funkcja dodaje nowe pliki do systemu kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 To  
 [in] Liczba plików wybranych do dodania do bieżącego projektu, jak podano w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica w pełni kwalifikowane nazwy lokalnych plików do dodania.  
  
 lpComment  
 [in] Komentarz, który ma zostać zastosowany do wszystkich plików dodawany.  
  
 pfOptions  
 [in] Tablica flag poleceń na poziomie każdego pliku.  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja Dodaj zakończyła się pomyślnie.|  
|SCC_E_FILEALREADYEXISTS|Wybrany plik jest już pod kontrolą źródła.|  
|SCC_E_TYPENOTSUPPORTED|Typ pliku (na przykład "binary") nie jest obsługiwana przez system kontroli źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; Dodaj nie wykonać.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowana.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle `fOptions` tutaj zastępuje tablicy `pfOptions`, z jedną `LONG` opcję specyfikacji na plik. Jest to typ pliku mogą się różnić od pliku.  
  
> [!NOTE]
>  Nie można określić zarówno `SCC_FILETYPE_TEXT` i `SCC_FILETYPE_BINARY` opcje dla tego samego pliku, ale jest prawidłowa, aby określić ani. Ustawienie nie jest taka sama jak ustawienie `SCC_FILETYPE_AUTO`, w którym to przypadku źródło kontrolować wtyczki automatycznie wykrywa typ pliku.  
  
 Poniżej znajduje się lista flagi używane w `pfOptions` tablicy:  
  
|Opcja|Wartość|Znaczenie|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Wtyczka do kontroli źródła powinna wykryć typ pliku.|  
|SCC_FILETYPE_TEXT|0x01|Wskazuje plik tekstowy ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Wskazuje typ pliku innego niż tekst w formacie ASCII.|  
|SCC_ADD_STORELATEST|0x04|Przechowuje najnowszą kopię pliku nie może.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Traktuje plik jako tekst ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Traktuje plik jako Unicode tekst w formacie UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Traktuje plik jako tekst Unicode w UTF16 format Little Endian.|  
|SCC_FILETYPE_UTF16BE|0x40|Traktuje formatu pliku jako tekst Unicode w UTF16 Big Endian.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)