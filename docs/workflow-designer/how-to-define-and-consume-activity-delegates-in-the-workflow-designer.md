---
title: 'Projektant przepływu pracy — porady: Definiowanie oraz stosowanie delegatów działania'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2039c1792a5e42c3181a01b10ff5bf271ea3bf2f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755759"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Porady: Definiowanie oraz stosowanie delegatów działania w Projektancie przepływów pracy

.NET framework 4.5 obejmuje Projektant out-of-box <xref:System.Activities.Statements.InvokeDelegate> działania. Tego projektanta pozwala przypisać delegatów do działania, która pochodzi z <xref:System.Activities.ActivityDelegate>, takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Zdefiniuj do delegata działania

1.  W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu**.

1. W **nowy projekt** okno dialogowe, wybierz opcję **przepływu pracy** kategorii po lewej stronie, a następnie wybierz **Aplikacja konsoli przepływu pracy** szablonu projektu. Nazwij projekt (Jeśli to konieczne), a następnie kliknij przycisk **Ok**.

   > [!NOTE]
   > Jeśli nie widzisz **przepływu pracy** kategorii, wcześniejszej instalacji **Windows Workflow Foundation** składnika programu Visual Studio 2017 r. Aby uzyskać szczegółowe instrukcje, zobacz [zainstalować program Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

2.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**. Wybierz **przepływu pracy** kategorii, a następnie wybierz **działania** szablon elementu. Nazwa nowego działania **MyForEach.xaml** , a następnie wybierz **OK**.

   Działanie zostanie otwarty w Projektancie przepływów pracy.

3.  W Projektancie przepływów pracy, kliknij przycisk **argumenty** kartę.

4.  Kliknij przycisk **utworzenia argumentu**. Nazwa nowej argument **elementów**.

5.  W **typ argumentu** kolumny wybierz **tablicy [T]**.

6.  W przeglądarce typu wybierz **obiektu** , a następnie wybierz **OK**.

7.  Kliknij przycisk **utworzyć Argument** ponownie. Nazwa nowej argument **treści**. W **kierunek** kolumny dla argumentu nowy, wybierz opcję **właściwości**.

8.  W kolumnie Typ argumentu wybierz **Przeglądaj w poszukiwaniu typów**

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

19. Przeciągnij <xref:System.Activities.Statements.Assign> działania na poziomie wiersz poniżej <xref:System.Activities.Statements.InvokeDelegate> działania. <xref:System.Activities.Statements.Assign> Utworzeniu działania i <xref:System.Activities.Statements.Sequence> działanie jest tworzone automatycznie zawiera dwa działania w **treści** sekcji **MyForEach** działania. Sekwencja jest wymagana od momentu **treści** sekcja może zawierać tylko pojedyncze działanie. Automatyczne tworzenie nowego <xref:System.Activities.Statements.Sequence> działanie to nowa funkcja programu .NET Framework 4.5.

20. Ustaw **do** właściwość <xref:System.Activities.Statements.Assign> działanie **indeksu**. Ustaw **wartość** właściwość **przypisać** działanie **indeksu + 1**.

   Niestandardowa **MyForEach** działania wywołuje dowolne działanie raz dla każdej wartości przekazywane do niego za pośrednictwem **elementów** kolekcji z wartościami w kolekcji jako dane wejściowe dla działania.

## <a name="use-the-custom-activity-in-a-workflow"></a>Użyj niestandardowego działania w przepływie pracy

1.  Tworzenie projektu przez naciśnięcie przycisku **Ctrl**+**Shift**+**B**.

2.  W **Eksploratora rozwiązań**, otwórz **Workflow1.xaml** w projektancie.

3.  Przeciągnij **MyForEach** przybornika działań na powierzchnię projektanta. Działanie jest w sekcji przybornika z taką samą nazwę jak projektu.

4.  Ustaw **elementów** właściwość **MyForEach** działanie **nowy obiekt [] {1, "abc"}**.

5.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działania z **podstawowych** sekcji przybornika do **delegata: Body** sekcji **MyForEach** działania.

6.  Ustaw **tekst** właściwość <xref:System.Activities.Statements.WriteLine> działanie **Argument.ToString()**.

Podczas wykonywania przepływu pracy w konsoli programu zawiera następujące dane wyjściowe:

**1**
**abc**