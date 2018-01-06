---
title: StartTrackingContextWithRoot | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContextWithRoot
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66065fe94b41c06082e878329a03de3851ee844d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Rozpoczyna kontekst śledzenia przy użyciu pliku odpowiedzi, określając znacznika głównego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp 
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`intermediateDirectory`  
 Katalog, w którym będą przechowywane w dzienniku śledzenia.  
  
 [in]`taskName`  
 Identyfikuje kontekst śledzenia. Ta nazwa jest używana do tworzenia nazwy pliku dziennika.  
  
 [in]`rootMarkerResponseFile`  
 Nazwa ścieżki pliku odpowiedzi, który zawiera znacznik główny. Nazwa głównego służy do grupy wszystkich śledzenia dla kontekstu razem.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **zakończyło się pomyślnie** ustawiony bit, jeśli kontekst śledzenia został utworzony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker.h  
  
## <a name="see-also"></a>Zobacz też  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)