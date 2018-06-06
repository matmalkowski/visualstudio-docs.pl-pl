---
title: Mieszanka testów dla scenariusza testu obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cd3511d138fb6416d8309a3e32c1e96c9b70502b
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750938"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Edytowanie mieszanki testów, aby określić, który wydajności sieci Web, jednostki i kodowane testy interfejsu użytkownika do scenariusza testów obciążenia

*Mieszanka testów* scenariusza jest kombinacją wybór testów wydajności i jednostki sieci Web, które są zawarte w tym scenariuszu i dystrybucji tych testów w scenariuszu. Dystrybucja to ustawienie można określić dla prawdopodobieństwo wybrane przez użytkownika wirtualnego podczas uruchomienia testu obciążenia poszczególnego testu.

 Po dodaniu zestawu testów do testu obciążenia, *mieszanka testów* działa jak inny mieszać opcji. Użytkownikiem wirtualnego losowo wybiera badanie, oparte na prawdopodobieństwo, że określone w zestawie. Na przykład jeśli dwóch testów, każdy 50 procent w mieszanym, nowy wirtualny użytkownik wybiera testu pierwszy około połowy czasu. W różnych 50/50 Jeśli jeden test jest długi, a inny jest krótkie, większe obciążenie, pochodzi z długo testu.

 Po dodaniu testy z różnymi, można je usunąć. Możesz również zmienić dystrybucji testu mieszanego przy użyciu formantu mieszanego. Formant mieszanego pozwala łatwo Dopasuj dystrybucji testów w scenariuszu.

> [!NOTE]
> Dystrybucji jest miarą prawdopodobieństwa wybrane przez użytkownika wirtualnego podczas uruchomienia testu obciążenia poszczególnego testu. Dystrybucji jest wyrażona w procentach. W związku z tym sumę liczb dystrybucji dla wszystkich testów, które są zawarte w scenariuszu to 100. Na przykład jeśli scenariusz zawiera tylko jeden test, dystrybucji dla tego testu jest 100 procent.

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Dodaj nowe testy do testu mieszanego w istniejącego scenariusza

Tworząc nowy scenariusz przy użyciu Kreatora nowego testu obciążenia, można określić testy wydajności i jednostki sieci Web, aby dodać do testu mieszanego nowy scenariusz.

Można dodać więcej wydajności sieci Web i testów jednostkowych z różnymi tekst scenariusza za pomocą edytora testu obciążenia.

![Dodawanie testu do istniejącego testu obciążenia](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Aby dodać więcej testów do istniejącego scenariusza

1.  Otwórz testu obciążenia.

2.  W edytorze testu obciążenia, kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz pozycję **Dodaj testy**.

     **Dodaj testy** zostanie wyświetlone okno dialogowe. Wszystkie wydajności sieci Web, jednostkowe i kodowane testy interfejsu użytkownika w rozwiązaniu, które nie są już w danym scenariuszu są dostępne dodać do scenariusza.

3.  W **dostępne testy** okienku wybierz wydajności sieci Web, jednostkowe i kodowane testy interfejsu użytkownika, które chcesz dodać. Wybierz strzałkę w prawo, aby dodać testów do **wybrane testy** okienka.

4.  Po dodaniu testy wybierz **OK**.

     Testy są dodawane do testu mieszanego. Nowe dystrybucji jest automatycznie przypisywana do testów w teście mieszanym.

5.  (Opcjonalnie) Dostosuj kontroli mieszanego do określenia dystrybucji testu. Aby uzyskać więcej informacji, zobacz [o różnych kontroli](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

##  <a name="EditingTestMixRemoveTest"></a> Usuwanie testów ze scenariusza
 ![Usuwanie testu z istniejącego testu obciążenia](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Aby usunąć testy z scenariusza

1.  Otwórz testu obciążenia.

2.  W edytorze testu obciążenia, w drzewie testu obciążenia, kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć testu oraz wybierz **edytowanie mieszanki testów**. **Edytowanie mieszanki testów** zostanie wyświetlone okno dialogowe.

3.  Wybierz wydajności sieci Web, jednostki lub kodowanego testu interfejsu użytkownika w siatce, a następnie wybierz pozycję **Usuń**.

    > [!NOTE]
    > Po usunięciu testu Dostosuj testu mieszanego do preferowanego dystrybucji.

4.  Aby zakończyć usuwanie testów, wybierz **OK**.

##  <a name="EditingTestMixAboutMixControl"></a> Informacje o formancie mieszany
 Formant mieszanego pozwala na dostosowanie procent obciążenia, które jest rozdzielona testy, typy przeglądarek lub typów sieci w scenariuszu testu obciążenia. Wartości procentowe są Dostosuj Przesuń suwaki. Dopasowywanie mieszanki testów określa prawdopodobieństwo wirtualny użytkownik korzystający z określonych testów w scenariuszu testu obciążenia.

 W przypadku przenoszenia suwaka, zmień wartości procentowe wszystkie dostępne elementy. Jeśli masz więcej niż dwa elementy wielkość Dodaj lub usuń jest równomiernie między innymi elementami. Istnieje możliwość zastąpienia tego zachowania. Zaznacz pole wyboru w kolumnie blokady dla danego elementu, należy zablokować określoną wartość procentową wartość dla tego elementu. Następnie gdy suwak wielkość Dodaj lub usuń jest stosowana tylko do wszystkie pozostałe elementy odblokowane.

 **Dystrybucji** przycisk umożliwia przydzielenie wartości procentowe równomiernie wszystkie elementy. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.


 Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny zamiast przy użyciu suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, innych elementów nie zostanie automatycznie dostosowana.

> [!NOTE]
> Suwaki są wyłączone, gdy łączna nie dodaje do 100% lub po wprowadzeniu wartości procentowe w **%** kolumny są miejsc dziesiętnych.


 Po wprowadzeniu wartości procentowe ręcznie, należy upewnić się, że suma wszystkich elementów jest 100%. Po zapisaniu mieszane, jeśli nie jest sumą 100%, pojawi się monit zaakceptować wartości procentowe są one lub do Przejdź wstecz i dostosować je. Jeśli wybierzesz je zaakceptować, ponieważ są one, zostaną obliczone proporcjonalnie do 100%.  Na przykład jeśli dwa elementy i ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawiona do 66,67% (80 podzielona przez 120) i drugiego elementu zostanie ustawiona do 33,33% (40 podzielona przez 120).

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)