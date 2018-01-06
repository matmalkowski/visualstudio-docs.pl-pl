---
title: Funkcja SccRemove | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRemove
helpviewer_keywords: SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f4d7d76e80fa165206a3faa53835b74c2716d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccremove-function"></a>Funkcja SccRemove
Ta funkcja usuwa pliki z systemu kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccRemove(  
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
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw w pełni kwalifikowaną ścieżką lokalną plików do usunięcia.  
  
 lpComment  
 [in] Komentarz, który ma zostać zastosowany do każdego pliku, zostaną usunięte.  
  
 fOptions  
 [in] Flagi polecenie (i nieużywanych).  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Usunięcie zakończyło się pomyślnie.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ISCHECKEDOUT|Nie można usunąć pliku, ponieważ użytkownik został on wyewidencjonowany.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; plik nie został usunięty.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja usuwa pliki z systemu kontroli źródła, ale nie powoduje usunięcia ich z lokalnego dysku twardego użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)