---
title: Funkcja SccCheckout | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 671e4ecebb44f0910eba3bb835a6da6f9a7f3903
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="scccheckout-function"></a>Funkcja SccCheckout
Podana lista nazw plików w pełni kwalifikowana, tej funkcji wyewidencjonuje je na dysku lokalnym. Komentarz ma zastosowanie do wszystkich plików wyewidencjonowany. Argument komentarz może być `null` ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 [in] Liczba plików wybranych do wyewidencjonowania.  
  
 lpFileNames  
 [in] Tablica nazw plików do wyewidencjonowania kwalifikowaną ścieżką lokalną.  
  
 lpComment  
 [in] Komentarz ma zostać zastosowany do każdego z wybranych plików jest wyewidencjonowany.  
  
 fOptions  
 [in] Polecenie flagi (zobacz [flag bitowych używane przez określonego polecenia](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Wyewidencjonowanie zostało pomyślnie zakończone.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Plik nie został wyewidencjonowany.|  
|SCC_E_ALREADYCHECKEDOUT|Użytkownik ma już ten plik wyewidencjonowany.|  
|SCC_E_FILEISLOCKED|Plik jest zablokowany, zabronienia tworzenie nowych wersji.|  
|SCC_E_FILEOUTEXCLUSIVE|Inny użytkownik przeprowadził wyewidencjonowania na wyłączność w odniesieniu do tego pliku.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)