---
title: Problemy z zabezpieczeniami | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 753f916d148675afd7313afc8673232f22280b7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-issues"></a>Problemy z zabezpieczeniami
Tylko uprawnienia potrzebne do debugowania programu przy użyciu programu Visual Studio, są takie same, jak deweloper musi on zostać uruchomiony program. W tym zdalnego debugowania w większości sytuacji (niektórych sytuacjach dotyczących innych usług, takich jak Internet Information Services mogą wymagać wyższego poziomu uprawnień).  
  
 Po uruchomieniu programu Visual Studio (PDM) Menedżera debugowania procesu śledzi debugowania procesów na komputerze lokalnym. Zdalnie program o nazwie msvsmon.exe jest uruchomiona przez dewelopera, aby obsługiwać zdalne debugowanie i udostępnić PDM. (Należy pamiętać, że msvsmon.exe nie jest usługą i musi zostać uruchomione ręcznie, aby włączyć debugowanie zdalne na tej maszynie.) Gdy program Visual Studio (lub msvsmon.exe) nie jest uruchomiona, żadne procesy nie są śledzone do debugowania.  
  
 Oznacza to, że deweloper może debugować programy, które użytkownik wprowadzenie żadne specjalne uprawnienia. Deweloper może nawet debugować procesy uruchomione przez innego użytkownika, że inna osoba jest członkiem grupy zabezpieczeń. I włączyć debugowanie zdalnego, konieczne jest tylko do kopiowania niezbędnych plików do zdalnego komputera i uruchomić msvsmon.exe (zobacz [zdalnego debugowania](../../debugger/remote-debugging.md) więcej szczegółów).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)   
 [Menedżer debugowania procesu](../../extensibility/debugger/process-debug-manager.md)   
 [Debugowanie zdalne](../../debugger/remote-debugging.md)