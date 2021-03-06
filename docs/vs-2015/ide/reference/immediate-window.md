---
title: Okno bezpośrednie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f3bd020a66b29180bdfb3430d1710e8f3c29a9b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676732"
---
# <a name="immediate-window"></a>Okno bezpośrednie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [bezpośrednim](https://docs.microsoft.com/visualstudio/ide/reference/immediate-window).  
  
  
**Bezpośrednie** okno służy do debugowania i obliczać wyrażeń, wykonywania instrukcji, drukowania wartości zmiennych i tak dalej. Umożliwia wprowadzenie wyrażenia, aby je ocenić lub wykonać przy pomocy języka programowania podczas debugowania. Aby wyświetlić **bezpośrednie** okna, otwórz projekt do edycji, a następnie wybierz **Windows** z **debugowania** menu, a następnie wybierz **bezpośrednie**, lub naciśnij klawisze CTRL + ALT + I.  
  
 Można użyć tego okna, aby wydawać indywidualne [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poleceń. Dostępne polecenia obejmują `EvaluateStatement`, który może służyć do przypisywania wartości do zmiennych. **Bezpośrednie** okna obsługuje również technologię IntelliSense.  
  
## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych  
 Okno to może być szczególnie przydatne podczas debugowania aplikacji. Na przykład, aby sprawdzić wartość zmiennej `varA`, możesz użyć [polecenie Drukuj](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Znak zapytania (?) jest aliasem `Debug.Print`, dlatego to polecenie można również zapisać:  
  
```  
>? varA  
```  
  
 Obie wersje to polecenie zwróci wartość zmiennej `varA`.  
  
> [!NOTE]
>  Problem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenia w pliku **bezpośrednie** okna, należy poprzedzić polecenie a znak większości (>). Aby wprowadzić kilka poleceń, przełącz się do **polecenia** okna.  
  
## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania  
 Możesz użyć **bezpośrednie** okna do wykonania funkcji lub podprocedury w czasie projektowania.  
  
#### <a name="to-execute-a-function-at-design-time"></a>Aby wykonać funkcję w czasie projektowania  
  
1.  Skopiuj następujący kod do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] konsoli aplikacji:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  Na **debugowania** menu, kliknij przycisk **Windows**, a następnie kliknij przycisk **bezpośrednie**.  
  
3.  Typ `?MyFunction(2)` w **bezpośrednie** okna i naciśnij klawisz Enter.  
  
     **Bezpośrednie** uruchomi okna `MyFunction` i wyświetlić `4`.  
  
 Jeśli funkcja lub podprocedura zawiera punkt przerwania, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spowoduje przerwanie wykonywania we właściwym miejscu. Można następnie użyć okien debugera do sprawdzenia stanu programu. Aby uzyskać więcej informacji, zobacz [wskazówki: debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 Nie można użyć obliczenia wyrażenia czasu projektowania w typach projektów, które wymagają uruchamiania środowiska wykonawczego, w tym [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)] projektów, projektów sieci Web, projektów urządzeń inteligentnych i projektów SQL.  
  
### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Obliczanie wyrażenia czasu projektowania w rozwiązaniach dotyczących wielu projektów  
 Podczas ustanawiania kontekstu oceny wyrażenia czasu projektowania, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odwołuje się do aktualnie wybranego projektu w Eksploratorze rozwiązań. Jeśli projekt nie jest zaznaczony w oknie Eksploratora rozwiązań [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] próbuje obliczyć funkcję względu projektu startowego. Jeśli nie można obliczyć funkcji w bieżącym kontekście, otrzymasz komunikat o błędzie. Jeśli próbujesz obliczyć wartości funkcji w projekcie, który nie jest projektem startowym rozwiązania, a otrzymasz komunikat o błędzie, spróbuj wybrać projekt w Eksploratorze rozwiązań i ponownie dokonać obliczenia.  
  
## <a name="entering-commands"></a>Wprowadzenie poleceń  
 Należy wprowadzić znak większości (>) przy wydawaniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenia w **bezpośrednie** okna. Użyj klawiszy Strzałka w górę i Strzałka w dół do przewijania wcześniej wydanych poleceń.  
  
|Zadanie|Rozwiązanie|Przykład|  
|----------|--------------|-------------|  
|Ocena wyrażenia.|Należy poprzedzić wyrażenie znakiem zapytania (?).|`? a+b`|  
|Tymczasowo przejdź do trybu poleceń, będąc w trybie bezpośrednim (Aby wykonać jedno polecenie).|Wprowadź polecenie prefacing go o rozmiarze większym niż znak większości (>).|`>alias`|  
|Przełącz do okna wiersza polecenia.|Wprowadź `cmd` prefacing go w oknie o rozmiarze większym niż znak większości (>).|`>cmd`|  
|Przejdź z powrotem do okna bezpośredniego.|Wprowadź `immed` do okna bez znaku większości (>).|`immed`|  
  
## <a name="mark-mode"></a>Tryb oznaczania  
 Po kliknięciu dowolnego poprzedniego wiersza w **bezpośrednie** okna, nastąpi automatyczne przejście w tryb oznaczania. Dzięki temu można wybrać, edytować i skopiować tekst z poprzedniego polecenia, ponieważ w dowolnym edytorze tekstów i wkleić je do bieżącego wiersza.  
  
## <a name="the-equals--sign"></a>Znak równości (=)  
 Okno służące do wprowadzania `EvaluateStatement` polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.  
  
 W **bezpośrednie** okna, znak równości (=) jest interpretowany jako operator przypisania. Tak na przykład polecenie  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 przypiszą do zmiennej `varA` wartość zmiennej `varB`.  
  
 W **polecenia** okna, z drugiej strony, znak równości (=) jest interpretowany jako operator porównania. Nie można użyć operacji przypisania w **polecenia** okna. Na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, a następnie polecenie  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 Zwraca wartość `False`.  
  
## <a name="first-chance-exception-notifications"></a>Powiadomienia o wyjątkach pierwszej szansy  
 W niektórych konfiguracjach ustawień powiadomienia o wyjątkach pierwszej szansy są wyświetlane w **bezpośrednie** okna.  
  
#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Aby przełączyć powiadomienia wyjątku pierwszej szansy w oknie bezpośrednim  
  
1.  Na **widoku** menu, kliknij przycisk **Windows inne**i kliknij przycisk **dane wyjściowe**.  
  
2.  Kliknij prawym przyciskiem myszy obszar tekstu **dane wyjściowe** okna i zaznacz lub odznacz opcję **komunikaty o wyjątkach**.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie po kodzie za pomocą debugera za](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Debugowanie w programie Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Podstawowe informacje o debugerze](../../debugger/debugger-basics.md)   
 [Wskazówki: Debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)   
 [Używanie wyrażeń regularnych w programie Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)



