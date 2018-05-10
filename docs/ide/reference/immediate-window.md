---
title: Okno bezpośrednie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4789bc8ca7359af2df6cf2ff9fbcdd8ba7d6b9
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="immediate-window"></a>Okno bezpośrednie
**Immediate** okna jest używana do debugowania i obliczać wyrażeń, wykonać instrukcje wartości zmiennych i tak dalej. Umożliwia ona wprowadź wyrażenia, które mają być obliczane lub wykonywane przez język programowania podczas debugowania. Aby wyświetlić **Immediate** okna, otwórz projekt do edycji, a następnie wybierz **Windows** z **debugowania** menu i wybierz **Immediate**, lub naciśnij klawisze CTRL + ALT + I.

 Można użyć tego okna, aby osoba problem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poleceń. Dostępne polecenia to `EvaluateStatement`, które mogą służyć do przypisywania wartości do zmiennych. **Immediate** okna obsługuje również funkcję IntelliSense.

## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych
 To okno może być szczególnie przydatne podczas debugowania aplikacji. Na przykład, aby sprawdzić wartość zmiennej `varA`, można użyć [polecenia Drukuj](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

 Znak zapytania (?) jest aliasem `Debug.Print`, dlatego to polecenie może być także zapisane:

```cmd
>? varA
```

 Obie wersje to polecenie zwróci wartość zmiennej `varA`.

> [!NOTE]
> Do wystawienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w **Immediate** okna, należy poprzedzić polecenie z a znak większości (>). Aby wprowadzić wiele poleceń, przełącz się do **polecenia** okna.


## <a name="design-time-expression-evaluation"></a>Obliczenie wyrażenia czasu projektowania
 Można użyć **Immediate** okna do wykonywania funkcji lub procedury w czasie projektowania.

#### <a name="to-execute-a-function-at-design-time"></a>Aby wykonać funkcję w czasie projektowania

1.  Skopiuj następujący kod do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] konsoli aplikacji:

    ```vb
    Module Module1

        Sub Main()
            MyFunction(5)
        End Sub

        Function MyFunction(ByVal input as Integer) As Integer
            Return input * 2
        End Function

    End Module
    ```

2.  Na **debugowania** menu, kliknij przycisk **Windows**, a następnie kliknij przycisk **Immediate**.

3.  Typ `?MyFunction(2)` w **Immediate** okna i naciśnij klawisz Enter.

     **Immediate** uruchomi okna `MyFunction` i wyświetlić `4`.

Jeśli funkcja lub procedura zawiera punkt przerwania, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spowoduje przerwanie wykonywania we właściwym momencie. Następnie można okna debugera Sprawdź swój stan programu. Aby uzyskać więcej informacji, zobacz [wskazówki: debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md).

Nie można użyć obliczenie wyrażenia czasu projektowania w typów projektów, które wymagają uruchamiania środowiska wykonawczego w tym [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] projektów, projekty sieci Web, projekty urządzeń inteligentnych i projekty SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Obliczenie wyrażenia czasu projektowania w rozwiązań dotyczących wielu projektów
 Kontekst dla obliczenie wyrażenia czasu projektowania, ustanawiając [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odwołuje się do aktualnie wybrany projekt w Eksploratorze rozwiązań. Jeśli nie wybrano projektu w Eksploratorze rozwiązań [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje ocenić funkcji przed projekt startowy. Nie można obliczyć funkcji w bieżącym kontekście, otrzymasz komunikat o błędzie. Jeśli chcesz ocenić funkcji w projekcie, który nie jest do rozwiązania projekt startowy i wystąpi błąd, spróbuj wybrać projekt w Eksploratorze rozwiązań i spróbuj ponownie oceny.

## <a name="entering-commands"></a>Wprowadzanie polecenia
 Należy wprowadzić większą niż podpisania (>), wydając [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] polecenia w **Immediate** okna. Użyj klawiszy Strzałka w górę i Strzałka w dół, aby przewijać wcześniej wydanych poleceń.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Obliczyć wyrażenia.|Należy poprzedzić wyrażenia znakiem zapytania (?).|`? a+b`|
|Tymczasowo tryb polecenia w trybie natychmiastowym (do wykonywania pojedynczych poleceń).|Wprowadź polecenie prefacing go z większości znak większości (>).|`>alias`|
|Przełącz do okna poleceń.|Wprowadź `cmd` do okna, prefacing go z większości znak większości (>).|`>cmd`|
|Przejdź do okna bezpośredniego.|Wprowadź `immed` do okna bez oznacza większe znak większości (>).|`immed`|

## <a name="mark-mode"></a>Tryb oznaczania
 Po kliknięciu dowolnej poprzedniego wiersza w **Immediate** okna, następuje przejście automatycznie w trybie znaku. Dzięki temu można wybrać, edytowania i skopiować tekst powyższych poleceń w edytorze tekstu i wklej je do bieżącego wiersza.

## <a name="the-equals--sign"></a>Znak równości (=)
 Okno służy do wprowadzania `EvaluateStatement` polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.

 W **Immediate** okna, znak równości (=) jest interpretowana jako operatora przypisania. Tak na przykład, polecenie

```cmd
>Debug.EvaluateStatement(varA=varB)
```

 zostanie przypisana do zmiennej `varA` wartość zmiennej `varB`.

 W **polecenia** okna, natomiast znak równości (=) jest interpretowana jako operator porównania. Nie można użyć przypisania operacje w **polecenia** okna. Na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, a następnie polecenie

```cmd
>Debug.EvaluateStatement(varA=varB)
```

 Zwraca wartość `False`.

## <a name="first-chance-exception-notifications"></a>Powiadomienia o wyjątkach pierwszej szansy
 W niektórych konfiguracjach ustawienia powiadomienia o wyjątkach pierwszej szansy są wyświetlane w **Immediate** okna.

#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Aby włączyć powiadomienia o wyjątkach pierwszej szansy w oknie bezpośrednim

1.  Na **widoku** menu, kliknij przycisk **inne okna**i kliknij przycisk **dane wyjściowe**.

2.  Kliknij prawym przyciskiem myszy w obszarze tekst **dane wyjściowe** okna i zaznacz lub odznacz **komunikaty o wyjątkach**.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie za pomocą debugera](../../debugger/navigating-through-code-with-the-debugger.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Debugowanie w programie Visual Studio](../../debugger/debugging-in-visual-studio.md)
- [Podstawowe informacje o debugerze](../../debugger/debugger-basics.md)
- [Wskazówki: Debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Używanie wyrażeń regularnych w programie Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)