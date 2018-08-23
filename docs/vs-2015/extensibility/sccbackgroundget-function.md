---
title: Funkcja SccBackgroundGet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 162bbc427b48ee10ea3a0b88837cf012f1c3fd07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629360"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja SccBackgroundGet](https://docs.microsoft.com/visualstudio/extensibility/sccbackgroundget-function).  
  
Ta funkcja pobiera z kontroli źródła każdego określonych plików bez interakcji użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 Niepowodzeń  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [out w] Tablica nazwy plików do pobrania.  
  
> [!NOTE]
>  Nazwy muszą być w pełni kwalifikowanej nazwy lokalnego.  
  
 Flagidw  
 [in] Polecenie flagi (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Unikatowa wartość skojarzonego z tą operacją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja została ukończona pomyślnie.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Pobieranie w tle jest już w toku (wtyczka do kontroli źródła powinna zwrócić to tylko wtedy, gdy nie obsługuje operacji wsadowych jednocześnie).|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończenie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja zawsze jest wywoływana w wątku, inny niż ten, który załadowany wtyczka do kontroli źródła. Ta funkcja nie powinien zwrócić, dopóki zakończy działania; jednak może ona zostać wywołana wiele razy przy użyciu wielu list plików, wszystko w tym samym czasie.  
  
 Korzystanie z `dwFlags` argument jest taka sama jak [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)

