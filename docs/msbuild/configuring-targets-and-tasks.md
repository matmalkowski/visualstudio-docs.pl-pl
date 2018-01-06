---
title: "Konfigurowanie obiektów docelowych i zadań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9b0f7676baa604ba301a3b600786d3ce6539f57c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań
Można skonfigurować program MSBuild obiektów docelowych i zadań w celu uruchomienia poza procesem przy użyciu programu MSBuild, dzięki czemu można wskazać kontekstach, które różnią się od pierwszego są uruchomione na. Na przykład możesz zastosować 32-bitowej aplikacji .NET Framework 2.0 jest uruchomiona na komputerze deweloperskim na 64-bitowym systemie operacyjnym program .NET Framework 4.5. Możesz też określić komputerach przy użyciu programu .NET Framework 4 lub starszej. W połączeniu z 32 - lub 64-bitowości określoną wersję systemu .NET Framework jest nazywany *kontekst docelowy*.  
  
## <a name="installation"></a>Instalacja  
 .NET Framework 4.5 i 4.5.1 środowisko uruchomieniowe języka wspólnego (CLR), elementy docelowe, zadania i narzędzia programu .NET Framework 4 należy zastąpić bez zmieniania ich. .NET Framework 4.5.1 jest instalowany jako część [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
 Jeśli chcesz zainstalować program MSBuild niezależnie od programu Visual Studio, możesz pobrać pakiet instalacyjny z [Pobierz MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745). Należy również zainstalować wersje programu .NET Framework, którego chcesz użyć również.  
  
## <a name="targets-and-tasks"></a>Obiektów docelowych i zadań  
 Uruchamia program MSBuild niektórych kompilowanie zadań pozaprocesowa pod kątem większy zestaw kontekstach.  Na przykład MSBuild 32-bitowych może uruchomić zadania kompilacji w procesie 64-bitowych pod kątem 64-bitowym komputerze. Jest to kontrolowane przez `UsingTask` argumentów i `Task` parametrów. Obiekty docelowe, instalowane przez program .NET Framework 4.5 Ustaw tych argumentów i parametrów, a nie są konieczne nie zmiany do tworzenia aplikacji dla różnych kontekstach docelowej.  
  
 Aby utworzyć własny kontekst docelowy, należy odpowiednio ustawione tych argumentów i parametrów. Poszukaj w pliku Microsoft.Common.targets programu .NET Framework 4.5 i pliku Microsoft.Common.Tasks przykłady.  Aby uzyskać informacji na temat sposobu Utwórz niestandardowe zadanie, którego można używać z wielu kontekstów docelowej lub sposobu modyfikowania istniejących zadań, zobacz [porady: Konfigurowanie obiektów docelowych i zadań](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md)