---
title: Funkcja SccQueryChanges | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryChanges
helpviewer_keywords: SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 589013b996f9ed018e28292a27c6a760eef1dae7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sccquerychanges-function"></a>Funkcja SccQueryChanges
Ta funkcja wylicza danej listy plików dostarczanie informacji na temat zmiany nazwy dla każdego pliku za pomocą funkcji wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekstu wtyczkę kontroli źródła.  
  
 To  
 [in] Liczba plików w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, aby uzyskać informacje na.  
  
 pfnCallback  
 [in] Funkcja wywołania zwrotnego do wywołania dla każdej nazwy pliku na liście (patrz [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) szczegółowe informacje).  
  
 pvCallerData  
 [in] Wartość, które zostaną przekazane bez zmian funkcji wywołania zwrotnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Proces wykonywania zapytania została ukończona pomyślnie.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty w kontroli źródła.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji.|  
|SCC_E_NONSPECIFICERROR|Wystąpił błąd nieokreślonej lub ogólne.|  
  
## <a name="remarks"></a>Uwagi  
 Są zmiany, którego dotyczy zapytanie do przestrzeni nazw: w szczególności, zmiana nazwy, dodawanie i usuwanie pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Kody błędów](../extensibility/error-codes.md)