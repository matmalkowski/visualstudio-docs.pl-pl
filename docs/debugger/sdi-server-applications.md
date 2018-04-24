---
title: Aplikacje serwera SDI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9047c9b39bad5f4f790327b5ee65b4de688db9d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="sdi-server-applications"></a>Aplikacje serwera SDI
Jeśli debugujesz aplikację serwera SDI, należy określić `/Embedding` lub `/Automation` w **argumenty wiersza polecenia** właściwości w *projektu* okno dialogowe strony właściwości dla C/C++, C# lub Projekty Visual Basic.  
  
 Argumenty wiersza polecenia debuger można uruchomić aplikacji serwera tak, jakby były go uruchomić z kontenera. Kontener, począwszy od programu menedżera lub pliku spowoduje następnie kontenera do korzystania z wystąpienia serwera usługi uruchomione w debugerze.  
  
## <a name="finding-the-command-line-arguments-property"></a>Wyszukiwanie właściwości argumenty wiersza polecenia  
 Aby uzyskać dostęp do *projektu* strony właściwości — okno dialogowe, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie z menu skrótów wybierz polecenie Właściwości. Aby znaleźć właściwości argumenty wiersza polecenia, rozwiń kategorię właściwości konfiguracji, a następnie kliknij przycisk Strona debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Porady: debugowanie serwerów COM](../debugger/how-to-debug-com-servers.md)