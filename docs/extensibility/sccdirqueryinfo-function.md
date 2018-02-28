---
title: Funkcja SccDirQueryInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c7a930c0fcdffbc76bba431012d76dd6d13686d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccdirqueryinfo-function"></a>Funkcja SccDirQueryInfo
Ta funkcja sprawdza listę katalogów ich bieżący stan w pełni kwalifikowana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 nDirs  
 [in] Liczba katalogów wybranych do można wykonać zapytania.  
  
 lpDirNames  
 [in] Tablica pełni kwalifikowane ścieżki katalogów można wykonać zapytania.  
  
 lpStatus  
 [w, out] Strukturę tablicy dla wtyczki do zwrócenia flagi stanu kontroli źródła (zobacz [kod stanu katalogu](../extensibility/directory-status-code-enumerator.md) szczegółowe informacje).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Zapytanie powiodło się.|  
|SCC_E_OPNOTSUPPORTED|System kontroli kodu źródłowego nie obsługuje tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja wypełnia zwracany tablicy o maski bitów z `SCC_DIRSTATUS` rodziny (zobacz [kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)), jeden wpis dla każdego katalogu podane. Tablica stanu jest przydzielany przez obiekt wywołujący.  
  
 IDE tej funkcji używa się przed katalogiem jest zmieniana na Sprawdź, czy katalog jest pod kontrolą źródła, badając, czy ma ona odpowiedni projekt. Katalog nie jest pod kontrolą źródła, IDE zapewniają odpowiednie ostrzeżenia dla użytkownika.  
  
> [!NOTE]
>  Jeśli wtyczka do kontroli źródła nie implementuje jednej lub więcej wartości stanu, niezaimplementowana bitów powinna być równa zero.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)