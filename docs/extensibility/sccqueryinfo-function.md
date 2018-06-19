---
title: Funkcja SccQueryInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e2838709d7c2c2ad6e6b1eeef36c2cc0018a1a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138886"
---
# <a name="sccqueryinfo-function"></a>Funkcja SccQueryInfo
Ta funkcja uzyskuje informacje o stanie dla zestawu wybranych plików pod kontrolą źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 To  
 [in] Liczba plików określonych w `lpFileNames` tablicy i długość `lpStatus` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, które ma zostać zbadany.  
  
 lpStatus  
 [w, out] Tablica, w którym wtyczkę kontroli źródła zwraca flagi stanu dla każdego pliku. Aby uzyskać więcej informacji, zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Zapytanie zakończyło się pomyślnie.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie spowodowany przez problemy z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_PROJNOTOPEN|Projekt nie jest otwarty pod kontrolą źródła.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `lpFileName` jest pustym ciągiem, nie ma żadnych informacji o stanie aktualizacji. W przeciwnym razie jest pełną nazwę ścieżki pliku, dla którego zostały zmienione informacje o stanie.  
  
 Zwracany tablicy mogą być maską bitów z `SCC_STATUS_xxxx` usługi bits. Aby uzyskać więcej informacji, zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md). System kontroli źródła nie może obsługiwać wszystkie typy bitowej. Na przykład jeśli `SCC_STATUS_OUTOFDATE` nie jest oferowany, po prostu nie ustawiono bitu.  
  
 Korzystając z tej funkcji można wyewidencjonować plików, należy pamiętać, że `MSSCCI` stan wymagania:  
  
-   `SCC_STATUS_OUTBYUSER` jest ustawiona, jeśli bieżący użytkownik ma wyewidencjonowania pliku.  
  
-   `SCC_STATUS_CHECKEDOUT` Nie można ustawić, chyba że `SCC_STATUS_OUTBYUSER` jest ustawiona.  
  
-   `SCC_STATUS_CHECKEDOUT` jest ustawiana tylko wtedy gdy plik jest wyewidencjonowany na wybrany katalog roboczy.  
  
-   Jeśli plik jest wyewidencjonowany przez obecnego użytkownika w katalogu innym niż katalog roboczy `SCC_STATUS_OUTBYUSER` jest ustawiona, ale `SCC_STATUS_CHECKEDOUT` nie jest.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)