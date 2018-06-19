---
title: 'Porady: Zarządzanie wiele wątków w kodzie zarządzanym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0888a0f65f36d624deffac60ceee032d3f3d13a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139669"
---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Porady: Zarządzanie wiele wątków w kodzie zarządzanym
Jeśli masz rozszerzenie pakiet VSPackage zarządzanych, które wywołuje metody asynchronicznej lub zawiera operacje, które są wykonywane na wątki innego niż wątek interfejsu użytkownika programu Visual Studio, należy stosować się wskazówek podanych poniżej. Wątku interfejsu użytkownika umożliwia zachowanie reakcji, ponieważ nie trzeba czekać do pracy w innym wątku do wykonania. Możesz wprowadzić kod bardziej wydajne, ponieważ nie ma dodatkowych wątków, które zajmują miejsce na stosie, a można tworzyć bardziej niezawodne i łatwiejsze do debugowania, ponieważ uniknąć zakleszczenie i zawiesza się.  
  
 Ogólnie rzecz biorąc, można przełączyć się z wątku interfejsu użytkownika do innego wątku, albo na odwrót. Gdy metoda zwróci wartość, bieżący wątek jest wątku, w którym była pierwotnie używana.  
  
> [!IMPORTANT]
>  Poniższe wskazówki korzystanie z interfejsów API w <xref:Microsoft.VisualStudio.Threading> przestrzeni nazw, w szczególności <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> klasy. Interfejsy API w tej przestrzeni nazw są nowością w programie [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Można pobrać wystąpienia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> właściwości `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Przełączanie z wątku interfejsu użytkownika do wątku w tle  
  
1.  Jeśli chcesz wykonać zadanie asynchroniczne wątku w tle są w wątku interfejsu użytkownika, należy użyć Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Jeśli jesteś w wątku interfejsu użytkownika i chcesz zablokować synchronicznie podczas wykonywania pracy na wątku w tle, użyj <xref:System.Threading.Tasks.TaskScheduler> właściwości `TaskScheduler.Default` wewnątrz <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Przełączanie z wątku w tle do wątku interfejsu użytkownika  
  
1.  Jeśli jesteś w wątku w tle i chcesz zrobić coś w wątku interfejsu użytkownika, użyj <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Można użyć <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metody, aby przełączyć się do wątku interfejsu użytkownika. Ta metoda zapisuje komunikat w wątku interfejsu użytkownika o kontynuację bieżącej metody asynchroniczne, a także komunikuje się z resztą wątkowości platformę, by ustawić priorytet poprawne i uniknąć zakleszczenia.  
  
     Nie można wprowadzić go asynchroniczną metodę wątku tła nie jest asynchroniczne, można nadal używać `await` składni, aby przełączyć się do wątku interfejsu użytkownika, opakowując swoją pracę dzięki <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>w tym przykładzie:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```