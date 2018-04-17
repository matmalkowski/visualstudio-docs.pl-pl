---
title: 'Porady: tworzenie aplikacji usługi przepływu pracy WCF | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d901354b4a6a5f90ef75567131540405af7c9690
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Porady: tworzenie aplikacji usługi przepływu pracy WCF

[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] aplikacje usług przepływu pracy są rozproszone komunikacji usługi, które przekazywania wiadomości między klientami a się w granicach procesu. Implementacja kontraktu usługi na stronie usługi odbywa się deklaratywnie działań przepływu pracy w [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] w sposób analogiczny do usług starszych przepływu pracy w programie .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Aby utworzyć aplikację usługi przepływu pracy WCF

1.  Uruchom [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu...** .

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **zainstalowane szablony** okienku wybierz **WCF** lub **przepływu pracy** z jednej **Visual C#** lub **Visual Basic** grupowania w zależności od języka wyboru.

4.  W środkowym okienku wybierz **aplikacji usługi przepływu pracy WCF**.

5.  W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

7.  W **rozwiązania** wybierz albo utworzyć nowe rozwiązanie, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać Aplikacja konsoli przepływu pracy do istniejącego rozwiązania, otworzyć tego rozwiązania w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie **Nowy projekt...** otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.

8.  Szablon projektu tworzy definicji usługi jako XAML. Projektant przepływu pracy systemu Windows zostanie otwarty do widoku projektu z <xref:System.Activities.Statements.Sequence> działanie, które zawiera zestaw <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie działania](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)