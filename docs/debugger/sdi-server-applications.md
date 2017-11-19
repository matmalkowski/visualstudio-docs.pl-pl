---
title: Aplikacje serwera SDI | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 089eeada5f3d9d392aff7768ed3f5b813ef8f772
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sdi-server-applications"></a>Aplikacje serwera SDI
Jeśli debugujesz aplikację serwera SDI, należy określić `/Embedding` lub `/Automation` w **argumenty wiersza polecenia** właściwości w *projektu* okno dialogowe strony właściwości dla C/C++, C# lub Projekty Visual Basic.  
  
 Argumenty wiersza polecenia debuger można uruchomić aplikacji serwera tak, jakby były go uruchomić z kontenera. Kontener, począwszy od programu menedżera lub pliku spowoduje następnie kontenera do korzystania z wystąpienia serwera usługi uruchomione w debugerze.  
  
## <a name="finding-the-command-line-arguments-property"></a>Wyszukiwanie właściwości argumenty wiersza polecenia  
 Aby uzyskać dostęp do *projektu* strony właściwości — okno dialogowe, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie z menu skrótów wybierz polecenie Właściwości. Aby znaleźć właściwości argumenty wiersza polecenia, rozwiń kategorię właściwości konfiguracji, a następnie kliknij przycisk Strona debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Porady: debugowanie serwerów COM](../debugger/how-to-debug-com-servers.md)