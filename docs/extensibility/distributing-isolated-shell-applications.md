---
redirect_url: shell/distributing-isolated-shell-applications
title: Dystrybuowanie aplikacji Isolated Shell | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 250f1d7769f6035e015eeb7247c439b27f913b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="distributing-isolated-shell-applications"></a>Dystrybuowanie aplikacji Isolated Shell
Aby utworzyć aplikację programu isolated shell, należy zainstalować program Visual Studio i programu Visual Studio SDK. Do dystrybucji aplikacji na komputerach innych użytkowników lub klientów, należy uwzględnić specjalne pakietu redystrybucyjnego dla programu isolated shell.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Wymagania wstępne dotyczące dystrybucja aplikacji Isolated Shell  
  
|Nazwa|Opis|  
|----------|-----------------|  
|Visual Studio SDK|Zestaw SDK musi mieć umożliwiające opracowanie i przetestowanie rozszerzenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zestaw SDK umożliwia również utworzenie wystąpienia programu Visual Studio izolowane powłoki.<br /><br /> Program Visual Studio jest wymagane dla tego zestawu SDK.|  
|Microsoft Visual Studio izolowane powłoki pakietu redystrybucyjnego|Pakiet redystrybucyjny programu objąć program Instalatora podczas kompilowania środowisku narzędzi dla programu Visual Studio izolowane powłoki. Pakiet redystrybucyjny programu izolowane powłoki obejmuje .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Tworzenie programu instalacyjnego dla aplikacji  
 Należy utworzyć program specjalnej instalacji aplikacji zintegrowanego lub izolowane powłoki. Aby uzyskać więcej informacji, zobacz [instalowanie aplikacji izolowane powłoki](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Stosowanie aktualizacji do aplikacji  
 Program instalacyjny muszą zezwalać na możliwość, że aplikacja zostanie zaktualizowany, aktualizacje firmy Microsoft lub aktualizacje firmy. Aby uzyskać więcej informacji na temat aktualizacji, zobacz [obsługi wytyczne dotyczące aplikacje izolowane powłoki](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).