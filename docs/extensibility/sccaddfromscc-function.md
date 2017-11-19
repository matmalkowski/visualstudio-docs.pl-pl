---
title: Funkcja SccAddFromScc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFromScc
helpviewer_keywords: SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5027e765e12ff483a9a27795990f0ddfbb479a5c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfromscc-function"></a>Funkcja SccAddFromScc
Ta funkcja umożliwia użytkownikowi przeglądanie w poszukiwaniu plików, które znajdują się już w systemie kontroli źródła i następnie wprowadzić te pliki częścią bieżącego projektu. Na przykład tej funkcji można uzyskać typowe pliku nagłówka w bieżącym projekcie bez kopiowania pliku. Zwracany tablica plików, `lplpFileNames`, zawiera listę plików, które użytkownik chce dodać do projektu IDE.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpnFiles  
 [w, out] Bufor liczbę plików, które są dodawane w. (Jest to `NULL` Jeśli pamięć wskazywana przez `lplpFileNames` jest do zwolnienia. Zobacz uwagi szczegółowe informacje).  
  
 lplpFileNames  
 [w, out] Tablicy wskaźników do nazwy pliku bez ścieżki katalogu. Ta tablica jest przydzielona i zwolniony przez wtyczkę kontroli źródła. Jeśli `lpnFiles` = 1 i `lplpFileNames` nie jest `NULL`, imię w tablicy wskazywana przez `lplpFileNames` zawiera folder docelowy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pliki zostały pomyślnie się i dodane do projektu.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana z żadnego skutku.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowana.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołanie tej funkcji. Jeśli wtyczka do kontroli źródła obsługuje określenia folderu lokalne miejsce docelowe, przekazuje IDE `lpnFiles` = 1 i przekazuje nazwę folderu lokalnego na `lplpFileNames`.  
  
 Po wywołaniu `SccAddFromScc` funkcja zwraca, wtyczkę przypisał wartości do `lpnFiles` i `lplpFileNames`, przydziału pamięci dla tablicy nazwy pliku, w razie potrzeby (należy pamiętać, że ten przydział zastępuje wskaźnika w `lplpFileNames`). Wtyczka do kontroli źródła jest odpowiedzialny za umieszczenie wszystkich plików w katalogu użytkownika lub w folderze określonej nazwy. Następnie IDE dodaje pliki do projektu IDE.  
  
 Na koniec IDE wywołania tej funkcji po raz drugi, przekazując `NULL` dla `lpnFiles`. To jest interpretowana jako specjalne sygnału przez wtyczkę, aby zwolnić pamięć przydzielona dla tablicy nazwy pliku w kontroli źródła`lplpFileNames``.`  
  
 `lplpFileNames`jest `char ***` wskaźnika. Wtyczka do kontroli źródła umieszczenie wskaźnika do tablicy wskaźników do nazwy pliku, w związku z tym przekazywania na liście w standardowy sposób dla tego interfejsu API.  
  
> [!NOTE]
>  Początkowej wersji interfejsu API VSSCI nie dostarczył sposób wskazywania projektem docelowym dla dodanymi plikami. Aby uwzględnić to semantykę `lplpFIleNames` parametru zostały rozszerzone, aby stał się parametr/out, a nie parametru wyjściowego. Jeśli tylko jeden plik jest określony, oznacza to, że wartość wskazywana przez `lpnFiles` = 1, a następnie pierwszy element `lplpFileNames` zawiera folder docelowy. Do używania tych nowych semantykę wywołań IDE `SccSetOption` działać z `nOption`ustawiono parametr `SCC_OPT_SHARESUBPROJ`. Jeśli wtyczka do kontroli źródła nie obsługuje semantykę, zwraca `SCC_E_OPTNOTSUPPORTED`. Podczas stosowania tak wyłącza **Dodaj z kontroli źródła** funkcji. Jeśli wtyczka obsługuje **Dodaj z kontroli źródła** funkcji (`SCC_CAP_ADDFROMSCC`), a następnie obsługuje nowe semantyki i musi zwracać `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)