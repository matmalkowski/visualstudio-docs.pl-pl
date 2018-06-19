---
title: 'Projektant przepływu pracy — porady: tworzenie aplikacji usługi przepływu pracy WCF'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974672"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Porady: tworzenie aplikacji usługi przepływu pracy WCF

Aplikacje usług Windows Communication Foundation (WCF) przepływu pracy są rozproszonej komunikacji usługi, które przekazywania wiadomości między klientami a się w granicach procesu. Implementacja kontraktu usługi na stronie usługi odbywa się deklaratywnie działań przepływu pracy w programie .NET Framework 4 w sposób analogiczny do usług starszych przepływu pracy w programie .NET Framework 3.5.

## <a name="to-create-a-wcf-workflow-service-application"></a>Aby utworzyć aplikację usługi przepływu pracy WCF

1.  Uruchom program Visual Studio 2010.

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **zainstalowane szablony** okienku wybierz **WCF** lub **przepływu pracy** z jednej **Visual C#** lub **Visual Basic** grupowania w zależności od języka wyboru.

4.  W środkowym okienku wybierz **aplikacji usługi przepływu pracy WCF**.

5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

7.  W **rozwiązania** wybierz albo utworzyć nowe rozwiązanie, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w programie Visual Studio 2010, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie  **Nowy projekt** otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.

8.  Szablon projektu tworzy definicji usługi jako XAML. Projektant przepływu pracy systemu Windows zostanie otwarty do widoku projektu z <xref:System.Activities.Statements.Sequence> działanie, które zawiera zestaw <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie działania](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)