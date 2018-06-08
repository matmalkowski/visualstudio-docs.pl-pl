---
title: Okno wyniku
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e9af45262649473f9676bff80b4a238fdd642ac
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844215"
---
# <a name="output-window"></a>Okno wyniku

**Dane wyjściowe** wyświetlane komunikaty o stanie dla różnych funkcji w zintegrowane środowisko programistyczne (IDE). Aby otworzyć **dane wyjściowe** okna, na pasku menu wybierz **widoku** > **dane wyjściowe**, lub naciśnij klawisz **Ctrl** +  **ALT**+**O**.

## <a name="toolbar"></a>Pasek narzędzi

Następujące sterowniki są wyświetlane na pasku narzędzi **dane wyjściowe** okna.

### <a name="show-output-from"></a>Pokaż dane wyjściowe

Zawiera co najmniej jednego okienka danych wyjściowych, aby wyświetlić. Kilku okienek informacje mogą być dostępne, w zależności od używanych narzędzi, które w IDE **dane wyjściowe** okna na dostarczenie wiadomości do użytkownika.

### <a name="find-message-in-code"></a>Wyszukaj komunikat w kodzie

Przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd kompilacji wybranych.

### <a name="go-to-previous-message"></a>Przejdź do poprzedniej wiadomości

Zmiany fokusu w **dane wyjściowe** okno do poprzedniego błąd kompilacji i przenosi punkt wstawiania w edytorze kodu na wiersz, który zawiera zawierający błąd kompilacji.

### <a name="go-to-next-message"></a>Przejdź do następnej wiadomości

Zmiany fokusu w **dane wyjściowe** okna do następnego błąd kompilacji i przenosi punkt wstawiania w edytorze kodu na wiersz, który zawiera zawierający błąd kompilacji.

### <a name="clear-all"></a>Wyczyść wszystko

Usuwa cały tekst z **dane wyjściowe** okienka.

### <a name="toggle-word-wrap"></a>Przełącz zawijanie tekstu

Włącza lub wyłącza funkcję zawijanie **dane wyjściowe** okienka. Jeśli zawijanie jest włączona, tekst w dłuższych pozycji wykracza poza obszar wyświetlania jest wyświetlany w następującym wierszu.

## <a name="output-pane"></a>W okienku danych wyjściowych

**Dane wyjściowe** wybranego w okienku **Pokaż dane wyjściowe z** liście zostaną wyświetlone dane wyjściowe ze wskazanego źródła.

## <a name="route-messages-to-the-output-window"></a>Rozsyłanie wiadomości w oknie danych wyjściowych

Aby wyświetlić **dane wyjściowe** okna zawsze, gdy w przypadku kompilowania projektu, **opcje** okna dialogowego, na **projekty i rozwiązania** > **ogólne**  wybierz pozycję **okna Pokaż dane wyjściowe kiedy rozpoczyna się kompilacja**. Następnie kod plik otwarty do edycji, wybierz **przejdź do następnej wiadomości** i **przejdź do poprzedniej wiadomości** na **dane wyjściowe** pasek narzędzi okna, aby wybrać wpisów w  **Dane wyjściowe** okienka. Jak to punkt wstawiania w przechodzi edytora kodu do wiersza kodu, gdzie występuje wybranego problemu.

Niektóre funkcje IDE i poleceń wywoływana w [okno polecenia](../../ide/reference/command-window.md) dostarczania ich dane wyjściowe do **dane wyjściowe** okna. Dane wyjściowe z zewnętrznych narzędzi, takich jak *bat* i *.com* pliki, które jest zwykle wyświetlany w oknie wiersza polecenia, jest kierowany do **dane wyjściowe** okienko po wybraniu  **Okno danych wyjściowych** opcji [Zarządzanie narzędziami zewnętrznymi](../../ide/managing-external-tools.md). Wiele innych rodzajów wiadomości mogą być wyświetlane w **dane wyjściowe** również okienka. Na przykład podczas sprawdzania składni języka Transact-SQL w procedurze składowanej w docelowej bazie danych wyniki są wyświetlane w **dane wyjściowe** okna.

Można także program aplikacji do zapisania komunikaty diagnostyczne w czasie wykonywania, aby **dane wyjściowe** okienka. Aby to zrobić, użyj elementów członkowskich <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy w <xref:System.Diagnostics> przestrzeń nazw w bibliotece klas programu .NET Framework. Elementy członkowskie <xref:System.Diagnostics.Debug> klasy dane wyjściowe podczas kompilowania konfiguracji debugowania rozwiązania lub projektu; członkami <xref:System.Diagnostics.Trace> klasy, dane wyjściowe podczas budowania konfiguracji Debug i Release. Aby uzyskać więcej informacji, zobacz [komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md).

W języku C++, możesz tworzyć niestandardowe kroki procesu kompilacji i zdarzenia kompilacji, których ostrzeżenia i błędy są wyświetlane i uwzględniane **dane wyjściowe** okienka. Naciskając **F1** w wierszu danych wyjściowych, można wyświetlić odpowiedniego tematu Pomocy. Aby uzyskać więcej informacji, zobacz [Format danych wyjściowych niestandardowego kroku kompilacji](/cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Zachowanie przewijania

Jeśli używasz autoscrolling w **dane wyjściowe** okna, a następnie przejść za pomocą myszy lub klawiszy strzałek, zatrzymuje autoscrolling. Aby wznowić autoscrolling, naciśnij klawisz **Ctrl**+**zakończenia**.

## <a name="see-also"></a>Zobacz także

- [Komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Porady: kontrolowanie w oknie danych wyjściowych](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)
- [Zrozumienie konfiguracje kompilacji](../../ide/understanding-build-configurations.md)
- [Przegląd biblioteki klas](/dotnet/standard/class-library-overview)