---
title: Funkcja SccUncheckout | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c363da795e588963c234af05a856f3352a7b2815
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccuncheckout-function"></a>Funkcja SccUncheckout
Ta funkcja spowoduje cofnięcie poprzedniej operacji wyewidencjonowania, a tym samym Przywracanie zawartość wybranego pliku lub plików do stanu przed wyewidencjonowanie. Wszystkie zmiany wprowadzone w pliku, ponieważ wyewidencjonowanie zostaną utracone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 To  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, do których chcesz cofnąć wyewidencjonowanie kwalifikowaną ścieżką lokalną.  
  
 fOptions  
 [in] Polecenie flag (nie).  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Cofnięcie wyewidencjonowania powiodło się.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Cofnij wyewidencjonowanie nie powiodło się.|  
|SCC_E_NOTCHECKEDOUT|Użytkownik nie ma ten plik wyewidencjonowany.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty z kontroli źródła.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
  
## <a name="remarks"></a>Uwagi  
 Po wykonaniu tej czynności `SCC_STATUS_CHECKEDOUT` i `SCC_STATUS_MODIFIED` flagi zostanie zarówno wyczyszczone dla plików, na których wykonano cofnięcie wyewidencjonowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)