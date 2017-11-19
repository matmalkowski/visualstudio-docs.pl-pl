---
title: "Przejdź do polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9273cd908a8948b47b818e9c4333cb8bd70fe094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
Przesuwa kursor do określonego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argumenty  
 `linenumber`  
 Opcjonalny. Liczba całkowita reprezentująca numer wiersza, aby przejść do.  
  
## <a name="remarks"></a>Uwagi  
 Rozpoczyna się numerowanie wierszy w jednej. Jeśli wartość `linenumber` jest mniejsza niż jedna, pierwszy wyświetla wiersza. Jeśli wartość `linenumber` jest większy niż numer ostatniego wiersza ostatniego Wyświetla wiersza.  
  
 Jeśli określono wartość `linenumber` nie zostanie określony, **przejdź do wiersza** Wyświetla okno dialogowe.  
  
 Alias dla tego polecenia jest GoToLn.  
  
## <a name="example"></a>Przykład  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)