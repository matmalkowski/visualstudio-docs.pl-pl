---
title: Polecenia ścieżki symboli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21a745177722160b100d0bbad770c3a74c40ca3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631798"
---
# <a name="symbol-path-command"></a>Ścieżka symboli — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ścieżka symboli — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/symbol-path-command).  
  
  
Określa listę katalogów do wyszukiwania symboli w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argumenty  
 `pathname`  
 Opcjonalna. Rozdzielana średnikami lista ścieżek dla debugera do wyszukiwania symboli.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie `pathname` jest określony, polecenie wyświetla listę bieżących ścieżek symboli.  
  
## <a name="example"></a>Przykład  
 Ten przykład dodaje dwie ścieżki do listy katalogów symboli.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład wyświetla listą rozdzielaną średnikami dla bieżących ścieżek symboli.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)



