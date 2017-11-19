---
title: "Przełącznik&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73d9838b5908b059aa229b5e979d635088d31de0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="switchlttgt-activity-designer"></a>Przełącznik&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.Switch%601> Działania oblicza określone wyrażenie i wykonuje działania z działań, których skojarzony klucz jest zgodna z wartością uzyskane z oceny kolekcji.  
  
 **Przełącznika < T\>**  Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Switch%601> działania w [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="the-switchtactivity"></a>Przełącznik\<T > działania  
 A <xref:System.Activities.Statements.Switch%601> zawiera działanie <xref:System.Activities.Statements.Switch%601.Expression%2A> i słownika <xref:System.Activities.Statements.Switch%601.Cases%2A>. Każdorazowo w słowniku składa się z pary, który zawiera *klucza* i działania, która służy jako odpowiednie *wartość*. <xref:System.Activities.Statements.Switch%601> Ocenia działania <xref:System.Activities.Statements.Switch%601.Expression%2A> i porównuje ją z kluczy. W przypadku odnalezienia pasującego odpowiadające mu działanie jest wykonywana. Tylko jedno dopasowanie jest możliwa, ponieważ klucze słownika musi być unikatowa zgodnie z typem równości zdefiniowane przez porównania równości słownika. Jeśli nie znaleziono, <xref:System.Activities.Statements.Switch%601.Default%2A> wykonaniu działania.  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>Jak użyć przełącznika\<T > Projektant działań  
 **Przełącznika\<T >** Projektant działań można znaleźć w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu **Przybornika** karcie na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.) Po usunięcie go do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wyświetla **wybierz typy** okna dialogowego, aby umożliwić użytkownikowi, określ typ ogólny *T* używane w <xref:System.Activities.Statements.Switch%601> działania. Wartość domyślna to **Int32**. Raz typu ogólnego *T* został wybrany, **przełącznika < T\>**  projektanta została dodana do projektanta przepływów pracy.  
  
 Poniżej przedstawiono właściwości **przełącznika < T\>**  projektanta. Wszystkie te właściwości można edytować w siatce właściwości. Niektóre z nich można również edytować na powierzchnię projektanta.  
  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.Switch%601> właściwości oraz opis korzystania z nich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Switch%601> Projektant działań. Wartość domyślna to przełącznika < Int32\>. Wartość można edytować w **właściwości** okna lub bezpośrednio w nagłówku projektanta.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Wartość true|Określa wyrażenie użyty do porównania z kluczami w kolekcji przypadków, aby określić w takim przypadku można wykonać.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Określa działanie wykonywane, jeśli nie znaleziono. Kliknij przycisk **dodać działanie** przycisk w projektancie, aby otworzyć **domyślne** pola, których można było porzucić działania.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Określa przypadków ma zostać obliczone. Aby dodać przypadek, kliknij przycisk **Dodawanie nowych przypadku** przycisk w dolnej części **przełącznika\<T >** projektanta. Przycisk zmiany pola tekstowego (pola kombi zaznaczenie typu ogólnego, dodając przełącznik\<T > jest ciągiem lub wyliczenia). Po dodaniu klucza w **przypadek wartość** obszar wielkość rozszerza i działania można porzucić gdzie tekst wskazówki "Upuść działanie tutaj", aby zdefiniować logiki wykonywania w przypadku.|  
  
 Można dodać wiele przypadków tak długo, jak klucze case nie są duplikowane. W przeciwnym razie okna dialogowego błędu wyświetla raportowania się, że określony klucz case już istnieje i że należy wybrać inny klucz. W **przełącznika\<T >** projektanta, tylko jeden obszar wielkość może znajdować się w widoku rozwiniętego naraz. Jeśli w widoku zwiniętym wielkość obszaru, klikając wielkość obszaru powiększa go. Zwróć uwagę, że w przypadku zwinięte projektanta pokazuje nazwę wyświetlaną działania w przypadku po prawej stronie Jeśli istnieje dowolne. W przeciwnym razie pokazuje **dodać działanie** przycisku, który umożliwia dodawanie działania i rozwija wielkość liter, jeśli klikniesz przycisk.  
  
 Kliknięcie przycisku klucz istniejącego przypadku zmienia klucz z etykiety w pole tekstowe tak, aby można było edytować klucza przypadków.  
  
 Istnieją 2 sposobów usuwania przypadku:  
  
1.  Wybierz wielkość liter i usuń go.  
  
2.  Wybierz kliknij prawym przyciskiem myszy case, aby wyświetlić menu kontekstowe i wybrać **usunąć**.  
  
 Należy pamiętać, że należy wybrać case, aby go usunąć. Wybierając i usuwając działanie w przypadku usuwa tylko działania inaczej.  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)