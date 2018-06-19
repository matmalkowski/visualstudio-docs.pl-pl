---
title: Problemy z zabezpieczeniami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d45ebd8c4d80b84749838c2034d72159c9e39627
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126900"
---
# <a name="security-issues"></a>Problemy z zabezpieczeniami
Tylko uprawnienia potrzebne do debugowania programu przy użyciu programu Visual Studio, są takie same, jak deweloper musi on zostać uruchomiony program. W tym zdalnego debugowania w większości sytuacji (niektórych sytuacjach dotyczących innych usług, takich jak Internet Information Services mogą wymagać wyższego poziomu uprawnień).  
  
 Po uruchomieniu programu Visual Studio (PDM) Menedżera debugowania procesu śledzi debugowania procesów na komputerze lokalnym. Zdalnie program o nazwie msvsmon.exe jest uruchomiona przez dewelopera, aby obsługiwać zdalne debugowanie i udostępnić PDM. (Należy pamiętać, że msvsmon.exe nie jest usługą i musi zostać uruchomione ręcznie, aby włączyć debugowanie zdalne na tej maszynie.) Gdy program Visual Studio (lub msvsmon.exe) nie jest uruchomiona, żadne procesy nie są śledzone do debugowania.  
  
 Oznacza to, że deweloper może debugować programy, które użytkownik wprowadzenie żadne specjalne uprawnienia. Deweloper może nawet debugować procesy uruchomione przez innego użytkownika, że inna osoba jest członkiem grupy zabezpieczeń. I włączyć debugowanie zdalnego, konieczne jest tylko do kopiowania niezbędnych plików do zdalnego komputera i uruchomić msvsmon.exe (zobacz [zdalnego debugowania](../../debugger/remote-debugging.md) więcej szczegółów).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)   
 [Menedżer debugowania procesu](../../extensibility/debugger/process-debug-manager.md)   
 [Debugowanie zdalne](../../debugger/remote-debugging.md)