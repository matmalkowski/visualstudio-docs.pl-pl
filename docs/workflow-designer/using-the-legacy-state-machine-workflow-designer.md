---
title: Projektant przepływu pracy — za pomocą projektanta przepływów pracy maszyny stanu starszych
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6ad09c2e999d9432b3c4e1062cb3031eb20ff56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979152"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Za pomocą projektanta przepływów pracy maszyny stanu starszych

Podczas tworzenia nowego projektu przepływu pracy stan komputera w programie Visual Studio 2010, przeznaczonego dla programu .NET Framework w wersji 3.5 lub WinFX, możesz użyć **Aplikacja konsoli przepływu pracy maszyny stanu** lub  **Stan: Biblioteka przepływu pracy automatu** szablonu projektu starszej wersji. Jeśli zostanie wybrana jedna z tych szablonów projektu maszyny stanu, Projektant maszyny stanu jest przedstawiany jako przepływem pracy starszego interfejsu użytkownika projektanta. Uzyskać informacji o szablonach projektu maszyny stanu starszej wersji, zobacz [jak: utworzyć stanu komputera przepływu pracy aplikacji konsoli (starsze)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) i [porady: Tworzenie biblioteki przepływu pracy (starsze)maszynystanu](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

Przepływ pracy automatu stanów składa się z zestawem stanów. Jednego stanu jest oznaczona jako stanu początkowego. Każdy stan może odbierać zdarzenia w określonym zestawie. Na podstawie zdarzenia, przejście może się do innego stanu. Przepływ pracy automatu stanów może mieć stan końcowy. Po nawiązaniu przejście do stanu końcowego zakończeniu przepływu pracy.

## <a name="state-machine-designer-views"></a>Widoki projektanta automatu stanów
 Projektant maszyny stanu jest dowolne projektanta, co oznacza, że działania mogą być przenoszone między za darmo na powierzchni projektu. Projektant maszyny stanu ma dwa widoki: *stanu* widoku i *sterowane zdarzeniami* widoku.

 Widok stanu przedstawia stan działania i sterowane zdarzeniami działań, które mogą być zawarte w ramach działania stanu. W tym widoku przejść z jednego stanu do innego są reprezentowane przez liniami z działania sterowane zdarzeniami w jednego stanu do innego stanu. Można również utworzyć przejścia, przez siebie Rysowanie linii. Aby narysować przejścia, wybierz działanie sterowane zdarzeniami, a następnie wybierz jedną z dojścia na działania i przeciągnij go. Rysuje tej akcji. Ten wiersz następnie jest dołączony do stanu docelowego, wskazując przejścia między stanami.

 Aby uzyskać dostęp do widoku zdarzeniami, kliknij dwukrotnie działanie sterowane zdarzeniami. Projektanta, który pojawi się są podobne jak w Projektancie sekwencyjnego przepływu pracy. W górnej części projektanta pasek nawigacyjny Wyświetla hierarchię działań do sterowane zdarzeniami działania, która jest wyświetlana. Klikając dowolny element w hierarchii wyświetlanych, można przejść do widoku stanu. Jeśli użytkownik narysuje przejście z jednego stanu do innego w widoku stanu, a w przypadku wyświetlania widoku tego działania zdarzeniami, działania stanu zestawu są dodawane do działania sterowane zdarzeniami dla Ciebie. Jeśli zmienisz właściwości zestawu stanu działania, znajduje odzwierciedlenie w widoku stanu.

## <a name="state-machine-workflow-activities"></a>Działania przepływu pracy automatu stanów
 W poniższej tabeli opisano klucza działań, które są używane w Projektancie przepływów pracy stan maszyny.

|Nazwa przybornika|Działanie|Opis|
|------------------|--------------|-----------------|
|**Stan**|[Działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan w automacie stanów; może zawierać dodatkowe **działanie StateActivity** działań. Aby uzyskać więcej informacji, zobacz [za pomocą działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|**Metoda SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Określa przejście do nowego stanu. Aby uzyskać więcej informacji, zobacz [za pomocą działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|**Działanie StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wykonuje po wprowadzeniu stanie; może zawierać innych działań. Aby uzyskać więcej informacji, zobacz [za pomocą działania działanie StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|
|**Działanie StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Wykonuje zawarte działania podczas opuszczania [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działania. Aby uzyskać więcej informacji, zobacz [za pomocą działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Używany do stanów, które opierają się na zdarzenie zewnętrzne, aby rozpocząć wykonywania. **EventDrivenActivity** działania musi mieć działanie implementujące [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) interfejs jako pierwsze działanie podrzędne. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|

 Głównym składnikiem przepływ pracy automatu stanów jest [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działania. Zdarzenia są przechwytywane w różnych miejscach przepływ pracy automatu stanów, innych stanów są wprowadzane do obsługi zadań, które są skojarzone z zdarzenia. Okres istnienia przepływu pracy przepływ pracy może pozostaw, a następnie wprowadź kilka innych stanów. Te stany połączyć ze sobą za pomocą [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) działania.

 Przeciągnięcie nowy **działanie StateActivity** na powierzchnię projektu przepływu pracy, możesz dodać [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), lub dodatkowych **działanie StateActivity** działania jako działania podrzędnego.

> [!CAUTION]
> Podczas tworzenia przepływów pracy za pomocą projektanta przepływów pracy maszyny stanu, należy monitorować strukturę przepływu pracy w przypadku projektowania **konspekt dokumentu** okno widoku. Wyświetlanie struktury przepływ pracy automatu stanów w **konspekt dokumentu** widok okna odzwierciedla logicznego układu działań w pliku znaczników przepływu pracy. Fizyczny układ działań przepływu pracy na powierzchnię projektu może nie duplikatów logicznego układu działań w pliku znaczników przepływu pracy.
>
> Aby otworzyć **konspekt dokumentu** okna na **widoku** menu wskaż **inne okna**, a następnie wybierz **konspekt dokumentu**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie aplikacji konsoli przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)
- [Instrukcje: Tworzenie biblioteki przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)
- [Przepływy pracy automatu stanów](http://go.microsoft.com/fwlink?LinkID=65016)
- [Za pomocą działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)
- [Za pomocą działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)
- [Za pomocą działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)
- [Za pomocą działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)
- [Przy użyciu działanie EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)