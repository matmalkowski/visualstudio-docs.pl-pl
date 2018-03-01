---
title: "Polecenie ścieżki symboli | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6eb125c691cb9e6f8642093612aca142172e76d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
Ustawia listę katalogów dla debugera do wyszukiwania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argumenty  
 `pathname`  
 Opcjonalny. Rozdzielany średnikami lista ścieżek debugera do wyszukiwania symboli.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie `pathname` jest określony, polecenie wyświetla listę bieżącej ścieżki symboli.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dodaje dwie ścieżki do listy katalogów symbolu.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia rozdzielaną średnikami listę bieżącej ścieżki symboli.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)