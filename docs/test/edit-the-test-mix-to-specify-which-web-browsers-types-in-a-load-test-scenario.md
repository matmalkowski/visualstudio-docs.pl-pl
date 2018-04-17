---
title: Przeglądarka testu mieszanego dla obciążenia testowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: be0bd036c907f852028f6a9cccc798742e624184
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Edytowanie mieszanki testów, aby określić, które Web typów przeglądarek w obciążeniu scenariusza testu

*Rozkład przeglądarek* umożliwia Symulacja obciążenia bardziej realistycznie w scenariuszu testu obciążenia. Obciążenia jest generowany przy użyciu heterogenicznych różnych przeglądarek sieci Web, a jeden pojedynczy przeglądarki sieci Web. Możesz utworzyć bliżej zbliżenia przeglądarki sieci Web, które będą używane z aplikacjami.

 Rozkład przeglądarek określa prawdopodobieństwo wirtualny użytkownik korzystający z określonego typu przeglądarki sieci Web w scenariuszu testu obciążenia. Podczas tworzenia testu obciążenia można symulować, czy obciążenie jest generowany przez więcej niż jednej przeglądarki sieci Web. Po dodaniu typ przeglądarki sieci Web z różnymi z zestawu przeglądarki sieci Web, które są dostarczane, zbiór skojarzone nagłówki dla wybranej przeglądarki sieci Web jest dodawany na każde żądanie HTTP, który jest przesyłany w teście wydajności sieci Web.

 Rozkład przeglądarek działa jak inne opcje mieszanego. Typ przeglądarki sieci Web jest losowo skojarzony z użytkownikiem wirtualnego oparte na rozkład przeglądarek. Testy tego użytkownika są uruchamiane w szczególności przeglądarki sieci Web, oparte na prawdopodobieństwo, że określone w zestawie.

 Po określeniu rozkład przeglądarek, można później Dodawanie i usuwanie typów przeglądarek sieci Web z różnymi. Możesz również zmienić dystrybucji mieszanego przeglądarki za pomocą formantu mieszanego. Formant mieszanego pozwala łatwo Dopasuj rozkład przeglądarek w scenariuszu.

## <a name="adding-new-browsers-to-a-scenario"></a>Dodawanie nowych przeglądarek do scenariusza

### <a name="to-add-new-browsers-to-a-scenario"></a>Aby dodać nowy przeglądarek do scenariusza

1.  Gdy w trakcie określania wybierz rozkład przeglądarek do scenariusza **Dodaj**.

     Nowy wpis przeglądarki jest dodawany do siatki.

    > [!NOTE]
    > Do wyświetlenia **Edytuj rozkład przeglądarek** okno dialogowe, kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz pozycję **Edytuj rozkład przeglądarek**.

2.  W **typ przeglądarki** kolumny, wybierz strzałkę nowego wpisu i wybierz typ żądanego przeglądarki.

3.  (Opcjonalnie) Dostosuj kontroli mieszanego do określenia dystrybucji testu.

4.  Po zakończeniu dodawania przeglądarki wybierz **OK**.

##  <a name="EditingTestMixSpecifyBrowserRemovingBrowserTypes"></a> Usuwanie przeglądarek ze scenariusza

### <a name="to-remove-browsers-from-a-scenario"></a>Aby usunąć przeglądarki z scenariusza

1.  Otwórz testu obciążenia.

2.  Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć przeglądarki, a następnie wybierz pozycję **Edytuj rozkład przeglądarek**.

     **Edytuj rozkład przeglądarek** zostanie wyświetlone okno dialogowe.

3.  Wybierz przeglądarkę w siatce, a następnie wybierz pozycję **Usuń**.

4.  (Opcjonalnie) Dostosuj kontroli mieszanego do określenia dystrybucji testu.

5.  Po zakończeniu usuwanie przeglądarek wybierz **OK**.

## <a name="about-the-mix-control"></a>Informacje o formancie mieszany

 Formant mieszanego pozwala na dostosowanie procent obciążenia, które jest rozdzielona testy, typy przeglądarek lub typów sieci w scenariuszu testu obciążenia. Wartości procentowe są Dostosuj Przesuń suwaki. Dopasowywanie różnych typów przeglądarki określa prawdopodobieństwo wirtualny użytkownik, który uruchomił typ przeglądarki określonych w scenariuszu testu obciążenia.

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