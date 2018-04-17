---
title: Funkcja SccCheckin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c8d23a89e55b272657dde0c2374c78e63bfaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="scccheckin-function"></a>Funkcja SccCheckin
Ta funkcja sprawdza w uprzednio pobranych plików do systemu kontroli źródła, przechowywania zmiany i utworzenia nowej wersji. Ta funkcja jest wywoływana z liczbą i tablicę nazw plików do wyewidencjonowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka SCC można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 To  
 [in] Liczba plików wybranych do wyewidencjonowania.  
  
 lpFileNames  
 [in] Tablica nazw plików pełni kwalifikowaną ścieżką lokalną.  
  
 lpComment  
 [in] Komentarz ma zostać zastosowany do każdego z wybranych plików, które zostały zaewidencjonowane. Jest to `NULL` Jeśli wtyczka do kontroli źródła należy Monituj o komentarz.  
  
 fOptions  
 [in] Polecenie flagi, albo 0 lub `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] SCC plug-określonych opcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pliki został pomyślnie zaewidencjonowany.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Plik nie został zaewidencjonowany.|  
|SCC_E_NOTCHECKEDOUT|Użytkownik nie został wyewidencjonowany pliku, więc nie można sprawdzić.|  
|SCC_E_CHECKINCONFLICT|Nie można wykonać zaewidencjonowania, ponieważ:<br /><br /> -Innego użytkownika zaewidencjonował wyprzedzeniem i `bAutoReconcile` była wartość false.<br /><br /> —lub—<br /><br /> Nie można wykonać automatyczne scalanie, (na przykład, jeśli pliki są binarne).|  
|SCC_E_VERIFYMERGE|Plik został scalony automatycznie, ale nie została sprawdzona w oczekujących Weryfikacja użytkownika.|  
|SCC_E_FIXMERGE|Plik został scalony automatycznie, ale nie została sprawdzona w z powodu konfliktu scalania, który należy ręcznie rozwiązać.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowana.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Komentarz ma zastosowanie do wszystkich plików, które zostały zaewidencjonowane. Argument komentarz może być `null` ciąg znaków, w którym to przypadku wtyczkę kontroli źródła może monitować użytkownika o ciąg komentarza dla każdego pliku.  
  
 `fOptions` Argument można podać wartości `SCC_KEEP_CHECKEDOUT` flagę wskazującą zamiarem użytkownika zaewidencjonować plik i ponownie wyewidencjonować.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)