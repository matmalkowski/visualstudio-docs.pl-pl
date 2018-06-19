---
title: Wdrożenie ClickOnce w systemie Windows Vista | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c546d7e4287fc47a3770baa306a43a1631be2f06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558935"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Wdrożenie ClickOnce w systemie Windows Vista
Tworzenie aplikacji w programie Visual Studio Kontrola konta użytkownika (UAC) w systemie Windows Vista zazwyczaj generuje manifest osadzonych zakodowane jako dane binarne dane XML w pliku wykonywalnego aplikacji. Ponieważ aplikacji ClickOnce i COM bez rejestrowania wymaga manifest zewnętrznych, Visual Studio generuje plik dla tych typów projektów zawierających dane funkcji Kontrola konta użytkownika zamiast osadzonych manifestu. Domyślnie program Visual Studio używa informacji z pliku o nazwie app.manifest do generowania informacji manifestu kontroli konta użytkownika zewnętrznego (w przypadku wdrażania ClickOnce i COM bez rejestrowania) lub aby osadzić go w pliku wykonywalnego aplikacji (dla wszystkich innych przypadkach). Program Visual Studio udostępnia następujące opcje do generowania manifestu:  
  
-   Używać osadzonych manifestu. Osadzone dane funkcji Kontrola konta użytkownika plik wykonywalny aplikacji i Uruchom jako zwykłego użytkownika.  
  
     To ustawienie domyślne (chyba że używasz ClickOnce). To ustawienie będzie obsługiwać zwykły sposób, w którym działa program Visual Studio w systemie Windows Vista; oznacza to, że Generowanie manifestu wewnętrznych i zewnętrznych, zarówno przy użyciu `AsInvoker`.  
  
-   Użyj zewnętrznego manifestu. Generuj manifest zewnętrznych za pomocą app.manifest.  
  
     Spowoduje to wygenerowanie zewnętrznych manifestu, korzystając z informacji w app.manifest. Podczas publikowania aplikacji za pomocą ClickOnce lub COM bez rejestrowania, Visual Studio dodaje app.manifest do projektu i dodaje tej opcji.  
  
-   Używać nie manifestu. Utwórz aplikację bez manifestu.  
  
     Takie podejście jest również nazywany *wirtualizacji*. Użyj tej opcji, aby zapewnić zgodność z istniejącymi aplikacjami z wcześniejszych wersji programu Visual Studio.  
  
 Nowe właściwości są dostępne na **aplikacji** strony projektanta projektu (dla programu Visual C# tylko dla projektów) i format pliku projektu MSBuild.  
  
 Należy pamiętać, że metoda konfigurowania Generowanie manifestu UAC w programie Visual Studio IDE różni się w zależności od typu projektu (Visual C# i Visual Basic).  
  
 Aby uzyskać informacje o konfigurowaniu projekty Visual C# do generowania manifestu, zobacz [strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Aby uzyskać informacje o konfigurowaniu projekty Visual Basic do generowania manifestu, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Uprawnienia użytkownika i programu Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)