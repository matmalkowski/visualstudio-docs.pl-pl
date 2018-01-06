---
title: "Porady: Definiowanie oraz stosowanie delegatów działania w Projektancie przepływów pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 47bca660b28c82b870946fb436b92c13a5aab485
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Porady: Definiowanie oraz stosowanie delegatów działania w Projektancie przepływów pracy
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)]zawiera nowe projektanta out-of-box dla <xref:System.Activities.Statements.InvokeDelegate> działania. Tego projektanta pozwala przypisać delegatów do działania, która pochodzi z <xref:System.Activities.ActivityDelegate>, takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Zdefiniuj do delegata działania  
  
1.  W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], wybierz pozycję **pliku**, **nowy**, **projektu**. Wybierz **przepływu pracy** węźle po lewej stronie oraz **Aplikacja konsoli przepływu pracy** szablonu po prawej stronie. Nazwij projekt (Jeśli to konieczne), a następnie kliknij przycisk **Ok**.  
  
2.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** . Wybierz **przepływu pracy** węźle po lewej stronie oraz **działania** szablonu po prawej stronie. Nazwa nowego działania **MyForEach.xaml** i kliknij przycisk **Ok**. Działanie zostanie otwarty w Projektancie przepływów pracy.  
  
3.  W Projektancie przepływów pracy, kliknij przycisk **argumenty** kartę.  
  
4.  Kliknij przycisk **utworzenia argumentu**. Nazwa nowej argument **elementów**.  
  
5.  W **typ argumentu** kolumny wybierz **tablicy [T]**.  
  
6.  W przeglądarce typu wybierz **obiektu**. Click **Ok**.  
  
7.  Kliknij przycisk **utworzyć Argument** ponownie. Nazwa nowej argument **treści**. W **kierunek** kolumny dla argumentu nowy, wybierz opcję **właściwości**.  
  
8.  W kolumnie Typ argumentu wybierz **Przeglądaj w poszukiwaniu typów...**  
  
9. W przeglądarce typu wprowadź **ActivityAction** w **nazwy typu** pola. Wybierz **ActivityAction\<T >** w widoku drzewa. Wybierz **obiektu** na liście rozwijanej, który wygląda jak przypisać typ **ActivityAction\<obiektu >** do argumentu.  
  
10. Przeciągnij <xref:System.Activities.Statements.While> działania z **przepływ sterowania** sekcji przybornika powierzchnię projektanta.  
  
11. Wybierz <xref:System.Activities.Statements.While> działania, a następnie wybierz **zmienne** kartę.  
  
12. Wybierz **utworzyć zmienną**. Nazwa nowej zmiennej **indeksu**.  
  
13. W **typ zmiennej** kolumny wybierz **Int32**. Pozostaw **zakres** jako **podczas**i **domyślne** puste kolumny.  
  
14. Ustaw **warunku** właściwość <xref:System.Activities.Statements.While> działanie **indeksu < Items.Length;**.  
  
15. Przeciągnij <xref:System.Activities.Statements.InvokeDelegate> działania z **podstawowych** sekcji przybornika do **treści** z <xref:System.Activities.Statements.While> działania.  
  
16. Wybierz **treści** w listy rozwijanej delegata.  
  
17. W **właściwości** siatki dla <xref:System.Activities.Statements.InvokeDelegate> działania, kliknij przycisk **...**  przycisk **argumenty delegata** właściwości.  
  
18. W **wartość** kolumny argument o nazwie **Argument**, wprowadź **elementy [Indeks]**. Kliknij przycisk **Ok** zamknąć **DelegateArguments** okna dialogowego.  
  
19. Przeciągnij <xref:System.Activities.Statements.Assign> działania na poziomie wiersz poniżej <xref:System.Activities.Statements.InvokeDelegate> działania. <xref:System.Activities.Statements.Assign> Działania zostanie utworzony, a <xref:System.Activities.Statements.Sequence> działania zostanie utworzony automatycznie zawierają dwa działania w **treści** sekcji **MyForEach** działania. Sekwencja jest wymagana od momentu **treści** sekcja może zawierać tylko pojedyncze działanie. Automatyczne tworzenie nowego <xref:System.Activities.Statements.Sequence> działanie jest nowa funkcja [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Ustaw **do** właściwość <xref:System.Activities.Statements.Assign> działanie **indeksu**. Ustaw **wartość** właściwość **przypisać** działanie **indeksu + 1**.  
  
 Niestandardowa **MyForEach** działania wywoła teraz dowolne działanie raz dla każdej wartości przekazywane do niego za pośrednictwem **elementów** kolekcji z wartościami w kolekcji jako dane wejściowe dla działania.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Użyj niestandardowego działania w przepływie pracy  
  
1.  Tworzenie projektu przez naciśnięcie przycisku **Ctrl + Shift + B**.  
  
2.  W **Eksploratora rozwiązań**, otwórz **Workflow1.xaml** w projektancie.  
  
3.  Przeciągnij **MyForEach** przybornika działań na powierzchnię projektanta. W sekcji przybornika z taką samą nazwę jak projekt będzie działania.  
  
4.  Ustaw **elementów** właściwość **MyForEach** działanie **nowy obiekt [] {1, "abc"}**.  
  
5.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działania z **podstawowych** sekcji przybornika do **delegata: Body** sekcji **MyForEach** działania.  
  
6.  Ustaw **tekst** właściwość <xref:System.Activities.Statements.WriteLine> działanie **Argument.ToString()**.  
  
 Podczas wykonywania przepływu pracy konsoli będzie zawierać następujące informacje:  
  
 **1**   
**ABC**