---
title: 'Porady: Określanie poleceń Pre-i POST-instrumentalnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8ce82bea823307e02b719fbfae43fe0697aca65
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844641"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Porady: Określanie poleceń pre-i POST-instrumentalnych

Możesz określić polecenia uruchamiane przed lub po są instrumentowane pliki binarne w sesji wydajności. Dowolne polecenie, które mogą być wystawiane z wiersza polecenia można określić jako wstępne dokumentu lub zdarzenia po instrumentacji. Na przykład można określić polecenia, które automatyzują ponownego podpisywania zestawu za pomocą klucza silnej nazwy w pliku wsadowym, która jest wykonywana po są instrumentowane pliki binarne.

Możesz określić polecenia dla instrumentowanych danych binarnych w przebiegu profilowania lub pojedynczych plików binarnych. Jednak można określić tylko jedno polecenie wstępne dokumentu do uruchomienia przed i tylko jedno polecenie po Instrumentacji do uruchomienia po instrumentacji. Nie można określić poleceń dla obu wszystkie pliki binarne i pojedynczych plików binarnych. Po określeniu polecenia dla wszystkich plików binarnych polecenia są uruchamiane przed lub po Instrumentacji danych binarnych każdego w sesji.

Katalog roboczy, w którym są wykonywane polecenia zależy od systen działania, na którym jest uruchamiana [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] i na platformie docelowej PROFILOWANEGO aplikacji.

 **32-bitowych komputerów**

Na komputerach z 32-bitowy, domyślny katalog narzędzia profiler jest *: dysk rozruchowy\Program 10.0\Team Files\Microsoft Visual Studio Tools narzędzia*.

**komputery 64-bitowe**

Na komputerach 64-bitowych należy określić ścieżkę zgodnie z platformą docelową PROFILOWANEGO aplikacji:

- Dla 32-bitowych aplikacji domyślny katalog narzędzia profiler jest:

     *: dysk rozruchowy\Program pliki (x86) \Microsoft Visual Studio 10.0\Team narzędzia narzędzia*

- Dla 64-bitowych aplikacji domyślny katalog narzędzia profiler jest:

     *: dysk rozruchowy\Program pliki (x86) \Microsoft Visual Studio 10.0\Team Tools\x64 narzędzia*

## <a name="to-specify-pre-instrument-commands"></a>Aby określić polecenia przed dokumentu

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenie wstępne dokumentu dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.

    - Aby określić polecenie wstępne dokumentu dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego w **celów** lista sesji wydajności, a następnie wybierz **właściwości**.

2. W **strony właściwości**, kliknij przycisk **Instrumentacji**.

3. Wpisz polecenie w **wiersza polecenia** pole tekstowe w obszarze **wstępne agregowania zdarzeń**.

    > [!NOTE]
    > Po kliknięciu przycisku wielokropka **(...)**  jest sąsiadujące **wiersza polecenia** pola Wyszukaj i wybierz odpowiedniego pliku .exe, cmd i bat.

4. Kliknij przycisk **OK**.

     Aby wyłączyć uruchamianie polecenia bez jego usuwania, wybierz pozycję **wykluczone z Instrumentacji** pole wyboru. Aby zmodyfikować kompilatora lub konsolidatora ustawienia, należy użyć strony właściwości projektu.

## <a name="to-specify-post-instrument-commands"></a>Aby określić polecenia POST-instrumentalnych

1. Wykonaj jedną z następujących czynności:

    - Aby określić polecenia po instrumentacji dla wszystkich plików binarnych w sesji wydajności, wybierz węzeł sesji wydajności w **Eksplorator wydajności**, a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.

    - Aby określić polecenia po instrumentacji dla określonego pliku binarnego, kliknij prawym przyciskiem myszy nazwę pliku binarnego w **celów** lista sesji wydajności, a następnie wybierz **właściwości**.

2. W **strony właściwości**, kliknij przycisk **Instrumentacji**.

3. Wpisz polecenie w **wiersza polecenia** pole tekstowe w obszarze **zdarzenia po Instrumentacji**.

    > [!NOTE]
    > Po kliknięciu przycisku wielokropka **(...)**  jest sąsiadujące **wiersza polecenia** pola Wyszukaj i wybierz odpowiedniego pliku .exe, cmd i bat.

4. Kliknij przycisk **OK**.

     Aby wyłączyć uruchamianie polecenia bez jego usuwania, wybierz pozycję **wykluczone z Instrumentacji** pole wyboru. Aby zmodyfikować kompilatora lub konsolidatora ustawienia, należy użyć strony właściwości projektu.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)