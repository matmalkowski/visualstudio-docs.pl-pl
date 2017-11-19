---
title: "Sprawdź zmienne w automatycznych i zmiennych lokalnych w systemie Windows | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 04/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2504807bd4717ec7f42ed059e7ef4d962c7441e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="inspect-variables-in-the-autos-and-locals-windows-in-visual-studio"></a>Sprawdź zmienne w automatycznych i zmiennych lokalnych Windows w programie Visual Studio
**Automatycznych** okna (podczas debugowania, **CTRL + ALT + V, A**, lub **debugowania > Windows > automatycznych**) i **zmiennych lokalnych** okna (podczas debugowania **CTRL + ALT + V, L**, lub **Debuguj > Windows > Zmienne lokalne**) są bardzo przydatne, gdy chcesz sprawdzić wartości zmiennych podczas debugowania. **Zmiennych lokalnych** wyświetlane zmienne zdefiniowane w zakresie lokalnego jest zazwyczaj funkcji lub metody, który jest aktualnie wykonywany. **Automatycznych** okna są wyświetlane zmienne używane wokół bieżącego wiersza (miejsce, w której debuger został zatrzymany). Dokładnie zmienne, które są wyświetlane w tym oknie różni się w różnych językach. Zobacz [co zmienne są wyświetlane w oknie automatycznych?](#bkmk_whatvariables) poniżej.  
  
Aby uzyskać więcej informacji o debugowaniu podstawowe zobacz [wprowadzenie do debugera](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Spojrzenie na obiektach w oknach zmiennych automatycznych i zmiennych lokalnych  
Tablice i obiekty są wyświetlane w oknach zmiennych automatycznych i zmiennych lokalnych jako drzewa formantów. Kliknij strzałkę w lewo nazwę zmiennej, aby rozwinąć widok, aby wyświetlić pola i właściwości. Oto przykład [FileStream](http://msdn.microsoft.com/Library/a8737776-e545-4867-91ed-51c7f031fa19) obiektu w **zmiennych lokalnych** okno:  
  
![Zmienne lokalne &#45; FileStream](../debugger/media/locals-filestream.png "FileStream zmiennych lokalnych")  
  
## <a name="bkmk_whatvariables"></a>Jakie zmienne są wyświetlane w oknie automatycznych?  
 Można użyć **automatycznych** okna w kodzie C#, Visual Basic i C++. **Automatycznych** okna nie obsługuje języka JavaScript lub F #.  
  
 W języku C# i Visual Basic **automatycznych** okno wyświetla dowolnej zmiennej używany w bieżącym lub poprzedniego wiersza. Jeśli na przykład deklarować zmiennych i ustaw je w następujący sposób:

```CSharp
    public static void Main()
    {
       int a, b, c, d;
       a = 1;
       b = 2;
       c = 3;
       d = 4;
    }
```

 Jeśli ustawisz punkt przerwania w wierszu `c = 3`; i uruchom debuger, po przerwaniu wykonywania **automatycznych** okno będzie wyglądać następująco:  

 ![Automatyczne &#45; CSharp](../debugger/media/autos-csharp.png "CSharp automatycznych")  

 Należy pamiętać, że wartość `c` ma wartość 0, ponieważ wiersz `c = 3` jeszcze nie zostało wykonane.  

 W języku C++ **automatycznych** okno wyświetla zmienne używane co najmniej trzy wiersze przed bieżącym wierszem (wiersza, w którym wykonywanie zostało zatrzymane). Deklarowanie zmiennych sześć:

```C++
    void main() {
        int a, b, c, d, e, f;
        a = 1;
        b = 2;
        c = 3;
        d = 4;
        e = 5;
        f = 6;
    }
```

 Jeśli ustawisz punkt przerwania w wierszu `e = 5;` i uruchom debuger, po przerwaniu wykonywania **automatycznych** okno będzie wyglądać następująco:  
  
 ![Automatyczne &#45; Cplus](../debugger/media/autos-cplus.png "Cplus automatycznych")  
  
 Należy pamiętać, że zmienna e została zainicjowana, ponieważ kod w wierszu `e = 5;` jeszcze nie zostało wykonane.  
  
 Można również sprawdzić wartości zwracanych funkcje i metody w pewnych okolicznościach. Zobacz [widoku wartości zwracanych z wywołań metody](#bkmk_returnValue) poniżej.  
  
##  <a name="bkmk_returnValue"></a>Widok wartości zwracanych z wywołań metody.  
 Kod .NET i C++ należy zbadać wartości zwracanych podczas kroku za pośrednictwem lub poza wywołania metody. Ta funkcja jest przydatna, gdy wynikiem wywołania metody nie jest przechowywana w zmiennej lokalnej, na przykład, gdy metoda jest używany jako parametr lub jako do wartości zwracanej innej metody.  
  
 Poniższy kod C# dodaje zwracane wartości dwie funkcje:  

```CSharp
static void Main(string[] args)  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    int x = sumVars(a, b) + subtractVars(c, d);  
}  
  
private static int sumVars(int i, int j)  
{  
    return i + j;  
}  
  
private static int subtractVars(int i, int j)  
{  
    return j - i;  
}  
```

 Ustaw punkt przerwania na `int x = sumVars(a, b) + subtractVars(c, d);` wiersza.  
  
 Rozpocznij debugowanie, a podczas wykonywania dzieli na pierwszy punkt przerwania, naciśnij klawisz **F10 (Step Over)**. Powinny pojawić się następujące opcje w **automatycznych** okno:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Dlaczego są wartości zmiennych czasami czerwono zmiennych lokalnych i automatycznych systemu windows?  
Można zauważyć, że wartość zmiennej czasami jest w **zmiennych lokalnych** i **automatycznych** systemu windows. Są to wartości zmiennych, które zostały zmienione od czasu ostatniego obliczania. Zmiana może być z poprzedniej sesji debugowania, lub wartość została zmieniona w oknie.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Zmiana formatu numerycznego okna zmiennej  
Domyślny format liczbowy jest dziesiętną, ale można go zmienić na szesnastkowe. Kliknij prawym przyciskiem myszy wewnątrz **zmiennych lokalnych** lub **automatycznych** i zaznacz **wyświetlacz**. Dotyczy wszystkich oknach debugera.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Edytowanie wartości w zmiennych systemu Windows  
Można edytować wartości większości zmiennych, które są widoczne w **automatycznych**, **zmiennych lokalnych**, **czujki**, i **QuickWatch** systemu windows. Informacje o **czujki** i **QuickWatch** systemu windows, zobacz [czujki i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Wystarczy kliknąć dwukrotnie wartość, którą chcesz zmienić, a następnie dodaj nową wartość.  
  
Można wprowadzić wyrażenie wartości, na przykład `a + b`. Debuger akceptuje najbardziej prawidłowe wyrażenia języka.  
  
W kodzie natywnym języku C++ może być konieczne zakwalifikować kontekście nazwę zmiennej. Aby uzyskać więcej informacji, zobacz [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md).  
 
Jednak należy zachować ostrożność podczas zmiany wartości. Oto niektóre potencjalne problemy:  
  
-   Niektóre wyrażenia obliczenia można zmienić wartość zmiennej lub inaczej nie wpływa na stan programu. Na przykład oceny `var1 = ++var2` zmienia wartość `var1` i `var2`.  
  
     Wyrażeń, które zmiany danych są określane jako ma [efekty uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), które dają nieoczekiwane wyniki, jeśli nie masz pewności z nich. Upewnij się, że rozumiesz konsekwencji tej zmiany przed wprowadzeniem go.  
  
-   Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza nieścisłości z powodu konwersji decimal-binary ułamkowych składników. Nawet pozornie nieszkodliwe edycji może spowodować zmianę niektórych najmniej znaczących bitów w zmiennej zmiennoprzecinkowych.  
  
## <a name="changing-the-window-context"></a>Zmiana kontekstu okna  
Można użyć **debugowania lokalizacji** narzędzi, aby wybrać odpowiednią funkcję, wątku lub procesu, który zmienia kontekst dla zmiennych systemu windows. Ustaw punkt przerwania i Rozpocznij debugowanie. (Jeśli ten pasek narzędzi nie jest widoczny, możesz je włączyć, klikając w pustą część obszar paska narzędzi. Możesz wyświetlić listę pasków narzędzi; Wybierz **debugowania lokalizacji**). Gdy punkt przerwania zostaje trafiony, zatrzymuje wykonywanie, aby sprawdzić narzędzi debugowania lokalizacji, który jest ostatnim wierszu poniższej ilustracji.
  
![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")   
  
## <a name="see-also"></a>Zobacz też  
 [Debuger systemu Windows](../debugger/debugger-windows.md)
