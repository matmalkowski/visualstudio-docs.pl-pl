---
title: Funkcja SccHistory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464c71d7caeca1b9b8c4c3455dad1737649f5ea4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138203"
---
# <a name="scchistory-function"></a>Funkcja SccHistory
Ta funkcja wyświetla historię określonych plików.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvContext`  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 `hWnd`  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 `nFiles`  
 [in] Liczba plików określonych w `lpFileName` tablicy.  
  
 `lpFileName`  
 [in] Tablica w pełni kwalifikowane nazwy plików.  
  
 `fOptions`  
 [in] Polecenie flagi (aktualnie nieużywane).  
  
 `pvOptions`  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie uzyskano Historia wersji.|  
|SCC_I_RELOADFILE|System kontroli źródła faktycznie zmodyfikowany plik na dysku podczas pobierania historii (na przykład, pobierając stara wersja), aby załadować ponownie ten plik IDE.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Nie można uzyskać historii plików.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła można wyświetlić okna dialogowego do wyświetlenia historii poszczególnych plików przy użyciu `hWnd` jako okno nadrzędne. Możesz też opcjonalny tekst wyjściowy wywołania zwrotnego funkcja dostarczony do [SccOpenProject](../extensibility/sccopenproject-function.md) mogą być używane, jeśli jest obsługiwana.  
  
 Należy pamiętać, że w pewnych okolicznościach, plik badane mogą ulec zmianie podczas wykonywania tego wywołania. Na przykład [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] polecenie history daje użytkownikowi możliwość pobrania starą wersję pliku. W takim przypadku zwraca wtyczkę kontroli źródła `SCC_I_RELOAD` ostrzec IDE, należy ponownie załadować plik.  
  
> [!NOTE]
>  Jeśli wtyczka do kontroli źródła nie obsługuje tej funkcji dla tablicy plików, można wyświetlić pliku historii pierwszy plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)