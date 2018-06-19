---
title: Projektant przepływu pracy — okno dialogowe Edytor (starsze) zestawu reguł
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77bb10e5237b33c60b0cd309c2d3c6c634182bc6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977342"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Okno dialogowe Edytor (starsze) zestawu reguł

W tym temacie opisano sposób użycia **Edytor ustawić reguły** okno dialogowe w starszej wersji projektanta przepływów pracy systemu Windows. Starsze projektanta przepływów pracy należy używać wtedy, gdy konieczne objęcie .NET Framework w wersji 3.5 lub WinFX.

**Edytor ustawić reguły** okno dialogowe służy do tworzenia i modyfikowania [działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) zestawy, które są serializowane w pliku Rules reguły.

> [!NOTE]
> Jeśli chcesz otworzyć plik Rules o **Edytor XML z kodowaniem**, należy najpierw zamknąć skojarzone okna Projektanta dla przepływu pracy lub działania.

Informacje na temat dostępu do **Edytor ustawić reguły** okno dialogowe, zobacz [porady: tworzenie działania PolicyActivity zestawu reguł (starsze)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> W edytorze zasad starszych projektanta przepływów pracy służący do docelowego .NET Framework w wersji 3.5 lub WinFX nie obsługuje przeznaczanie dla wielu platform.

W poniższej tabeli opisano elementy interfejsu użytkownika **Edytor ustawić reguły** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Dodaj regułę**|Dodaje nową definicję reguły dla zestawu reguł.|
|**Usuwanie**|Usuwa wybraną regułę z zestawu reguł.|
|**Łączenie w łańcuchy**|Określa typ do przodu łańcuch serwerów do korzystania z zestawu reguł. Dostępne opcje to:<br /><br /> -   **Pełne łańcucha**, określającej używa wszystkich do przodu mechanizmów CBC: pośrednie, przypisywanie — metoda i za pomocą jawnego **aktualizacji** funkcji.<br />-   **Sekwencyjne**, który określa, że nie należy używać do przodu łańcucha.<br />-   **Jawne aktualizacji tylko**, który określa do wykonywania tylko do przodu łańcucha na **aktualizacji** akcje.<br /><br /> Aby uzyskać więcej informacji na temat łańcucha do przodu, zobacz [za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|**Nazwa**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według nazwy.|
|**Priorytet**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według priorytetu.|
|**Ponownej oceny**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według typu ponownej oceny.|
|**Podgląd reguły**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł, w wersji zapoznawczej reguły warunek i akcje.|
|**Nazwa:**|Wprowadź nazwę reguły.|
|**Priorytet:**|Wprowadź priorytet reguły. Domyślnie priorytet wynosi 0.|
|**Ponownej oceny:**|Określa typ ponownej oceny reguły do użycia z regułą. Dostępne opcje to:<br /><br /> -   **Zawsze**, co powoduje, że reguła go obliczyć ponownie zgodnie z potrzebami.<br />-   **Nigdy nie**, co powoduje, że reguła nigdy go obliczyć ponownie. W takim przypadku reguła jest wykonywana tylko raz.|
|**Aktywne**|Sprawdź, aby uaktywnić reguły.|
|**Warunek:**|Wprowadź wyrażenie dla warunku reguły. Informacje o składni wyrażeń zobacz sekcję "Wprowadzania warunku i działania wyrażeń" tej strony.|
|**Następnie akcje:**|Wprowadź wyrażenie Then akcje. Informacje o składni wyrażeń zobacz sekcję "Wprowadzania warunku i działania wyrażeń" tej strony.|
|**Inne akcje:**|Wprowadź wyrażenie akcji Else. Informacje o składni wyrażeń zobacz sekcję "Wprowadzania warunku i działania wyrażeń" tej strony.|
|**OK**|Kliknij, aby zapisać zestawu do pliku Rules reguł.|

 Aby uzyskać więcej informacji na temat zestawów reguł, zobacz [za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Wprowadzanie warunku i wyrażeniami akcji
 Wprowadź wyrażenie dla warunku, a następnie i Else akcje jako tekstu w ich odpowiednich pól **Edytor ustawić reguły** okno dialogowe. Możesz wpisać **to.** w edytorze, aby odwoływać się do pola, właściwości i metody używane w przepływie pracy przy użyciu typu menu IntelliSense. Lub nazwa elementu członkowskiego przepływu pracy można wpisać bezpośrednio. Można wywołać metody statyczne na wskazanych typów, wpisując nazwę klasy, a następnie nazwę metody.

 Operatory logiczne można dodać do warunku, takich jak AND, OR i NOT. Można również dodać predykatów. Predykat jest operator binarny i dwóch argumentów operacji. Operatory binarne obsługiwane są ==, >, \<, > =, i < =. Obsługiwane argumenty operacji są wartości stałej, funkcja arytmetyczne i zakresami publiczne elementy członkowskie.

 Można określić typ do porównania i możesz porównać **null** lub ciąg pusty. Można zagnieździć wywołań elementów członkowskich w zmiennej, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.

 Wyrażenia obsługuje następujące operatory:

-   Operatory relacyjne: ==, =,! =

-   Operatory porównania: <, \<=, >, > =

-   Operatory arytmetyczne: +, -, *, /, MOD

-   Operatory logiczne: I, & &, OR &#124; &#124;, a nie,!

-   Operatory bitowe: &,&#124;

 Kolejność wykonywania wyrażenia następuje reguły pierwszeństwa operatora C#.

 Aby uzyskać więcej informacji o warunkach, zobacz [za pomocą warunków w przepływach pracy](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Zatrzymanie i aktualizacji funkcji
 **Następnie akcji:** i **akcje Else:** wyrażenia obsługują **zatrzymanie** i **aktualizacji** funkcji. Umożliwia **zatrzymanie** , wpisz **zatrzymanie** do **następnie akcji:** lub **Else akcji:** pola tekstowego. **Zatrzymanie** czynność powoduje wykonania zestawu reguł natychmiast zatrzymać i zwraca sterowania do wywołującego kodu. Możesz użyć **aktualizacji** funkcji z przodu łańcucha.

 **Aktualizacji** instrukcji można wyrazić w edytorze w jednym z dwóch formach; oba formularze są wyświetlane w następującym przykładzie:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Aby uzyskać więcej informacji o korzystaniu z **aktualizacji** z łańcucha do przodu, zobacz [za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Zobacz także

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Wybieranie zestawu reguł, okno dialogowe (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)
- [Za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)