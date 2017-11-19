---
title: Funkcja SccDirDiff | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirDiff
helpviewer_keywords: SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea335ef6bcb2a27b4312c613062be0d365711cbc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sccdirdiff-function"></a>Funkcja SccDirDiff
Ta funkcja przedstawia różnice między bieżącym katalogu lokalnego na dysku klienta i odpowiedniego projektu pod kontrolą źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 Właściwość hWnd  
 [in] Dojście do okna IDE, które wtyczka do kontroli źródła można używać jako elementu nadrzędnego wszystkie okna dialogowe, które zawiera.  
  
 lpDirName  
 [in] Pełna ścieżka do katalogu lokalnego, dla których chcesz wyświetlić różnica visual.  
  
 wartość elementu dwFlags  
 [in] Polecenie flagi (zobacz uwagi sekcji).  
  
 pvOptions  
 [in] Opcje plug-dotyczące kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|W katalogu na dysku jest taka sama jak projektu w kontroli kodu źródłowego.|  
|SCC_I_FILESDIFFER|W katalogu na dysku jest inna niż projektu w kontroli kodu źródłowego.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowana.|  
|SCC_E_FILENOTCONTROLLED|Katalog nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji. Ponowna próba jest zalecane.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć katalogu lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana w celu poinstruowania wtyczka do kontroli źródła do wyświetlania użytkownikowi listę zmian w określonym katalogu. Wtyczka otwiera osobnym oknie, w formacie swojego wyboru, aby wyświetlić różnice między katalogu użytkownika na dysku i odpowiedniego projektu pod kontrolą wersji.  
  
 Jeśli porównanie obsługuje wtyczki katalogów gwarancja, nawet jeśli opcji "szybkie różnicowego" nie są obsługiwane musi obsługiwać porównania katalogów na podstawie nazwy pliku.  
  
|`dwFlags`|Interpretacja|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Porównania bez uwzględniania wielkości liter (może służyć do szybkiego różnicowego lub visual).|  
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (może służyć do szybkiego różnicowego lub visual).|  
|SCC_DIFF_QD_CONTENTS|Jeśli jest to obsługiwane przez wtyczkę kontroli źródła, dyskretnie porównuje katalogu po bicie.|  
|SCC_DIFF_QD_CHECKSUM|Jeśli obsługiwane przez dodatek typu plug-in, dyskretnie porównuje katalogu za pomocą sumy kontrolnej lub, jeśli nie jest obsługiwana, powraca do SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Jeśli obsługiwane przez dodatek typu plug-in, dyskretnie porównuje katalogu za pomocą jego sygnatury czasowej lub, jeśli nie jest obsługiwana, nastąpi powrót na SCC_DIFF_QD_CHECKSUM lub SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Ta funkcja korzysta z tej samej flagi polecenie jako [SccDiff](../extensibility/sccdiff-function.md). Jednak nie obsługuje operacji "szybkie różnicowego" dla katalogów wybrać wtyczka do kontroli źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)