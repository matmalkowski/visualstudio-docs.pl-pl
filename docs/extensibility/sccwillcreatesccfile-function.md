---
title: Funkcja SccWillCreateSccFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccWillCreateSccFile
helpviewer_keywords: SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b6aa6ead6811f50cc186f46561b214ba4cd0905
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sccwillcreatesccfile-function"></a>Funkcja SccWillCreateSccFile
Ta funkcja sprawdza, czy wtyczkę kontroli źródła obsługuje tworzenie MSSCCPRJ. Plik SCC dla każdego danego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekstu wtyczkę kontroli źródła.  
  
 To  
 [in] Liczba nazwy plików zawarte w `lpFileNames` tablicy oraz długość `pbSccFiles` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw FQDN plików do sprawdzenia (tablicy muszą być przydzielone przez obiekt wywołujący).  
  
 pbSccFiles  
 [w, out] Tablica do przechowywania wyników.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_E_INVALIDFILEPATH|Jedna ze ścieżek w tablicy jest nieprawidłowa.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana z listą plików w celu określenia, czy wtyczkę kontroli źródła zapewnia obsługę w MSSCCPRJ. Plik SCC dla każdego z danym plików (Aby uzyskać więcej informacji na temat MSSCCPRJ. Plik SCC, zobacz [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md)). Plug-in kontroli źródła można zadeklarować, czy mają możliwość tworzenia MSSCCPRJ. Pliki SCC przez zadeklarowanie `SCC_CAP_SCCFILE` podczas inicjowania. Zwraca wtyczki `TRUE` lub `FALSE` dla każdego pliku `pbSccFiles` tablicy, aby określić, które pliki danego mieć MSSCCPRJ. Obsługa SCC. Jeśli wtyczka zwróci kod powodzenia z funkcji, wartości w tablicy zwracane są uznawane. W przypadku awarii tablicy jest ignorowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md)