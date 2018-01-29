---
title: Ustaw czujki na zmiennych w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 04/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0f5c518becd09f6b94fb598975caa913d150ac2a
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Ustaw czujki na zmiennych czujki i QuickWatch Windows w programie Visual Studio
Podczas debugowania, można użyć **czujki** i **QuickWatch** systemu windows, aby obejrzeć zmiennych i wyrażeń.  Różnica jest to, że **czujki** można wyświetlić w oknie kilku zmiennych podczas **QuickWatch** okno wyświetla pojedynczą zmienną w czasie. 

Systemu windows są dostępne tylko podczas sesji debugowania. Aby otworzyć **czujki** okna, wybierz **debugowania > Windows > Obejrzyj > Obejrzyj (1, 2, 3, 4)**). Aby otworzyć **QuickWatch** okna, albo kliknij prawym przyciskiem myszy w zmiennej i wybierz **QuickWatch** lub wybierz **Debuguj > QuickWatch**.
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Obserwowania pojedynczą zmienną z QuickWatch  
 Można użyć **QuickWatch** okna, aby przyjrzeć się pojedynczą zmienną. Na przykład, jeśli masz następujący kod:  
  
```CSharp
static void Main(string[] args)  
{  
    int a, b;  
    a = 1;  
    b = 2;  
    for (int i = 0; i < 10; i++)  
    {  
        a = a + b;  
    }   
}  
```  
  
 Można obserwować zmiennej w oknie QuickWatch w następujący sposób:  
  
1.  Ustaw punkt przerwania na `a = a + b;` wiersza.  
  
2.  Rozpocznij debugowanie. Wykonanie zatrzymuje się na punkt przerwania.  
  
3.  Otwórz **QuickWatch** okna (kliknij prawym przyciskiem myszy `a`, a następnie wybierz **QuickWatch**, lub wybierz `a` i naciśnij klawisz **SHIFT + F9**).

    Powinny pojawić się zmienną w **wartości** okna o wartości 1.

    ![QuickWatch Expression](../debugger/media/watchexpression.png "QuickWatchExpression")  

    Jeśli chcesz ocenić wyrażenia przy użyciu zmiennej, dodać wyrażenie, takie jak `a + b` do **wyrażenie** i kliknij **obliczyć ponownie**. 
  
4.  Dodaj zmienną **czujki** w oknie **QuickWatch** klikając **Dodaj wyrażenie kontrolne**. 

    > [!NOTE]
    > **QuickWatch** okno jest oknem modalnego okna dialogowego, więc nie można kontynuować debugowanie tak długo, jak jest otwarty.  
  
5.  Zamknij **QuickWatch** okna. Teraz można kontynuować debugowania gdy Sprawdź wartość w **czujki** okna.  
  
## <a name="observing-variables-with-the-watch-window"></a>Obserwowania zmiennych z okna czujki  
 Można obserwować wiele zmiennych o **czujki** okna. Na przykład, jeśli masz następujący kod:  
  
```C++  
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}
  
```  
  
 Dodaj wartości trzech zmiennych do okna czujki w następujący sposób:  
  
1.  Ustaw punkt przerwania na `c = a + b;` wiersza.  
  
2.  Rozpocznij debugowanie (**F5**). Wykonanie zatrzymuje się na punkt przerwania.  
  
3.  Otwórz okno czujki (**debugowania > Windows > Obejrzyj > Obejrzyj 1**, lub **CTRL + ALT + W 1**).  
  
4.  Dodaj `a` zmiennej w pierwszym wierszu `b` zmienną do drugiego wiersza i `c` zmienną do trzeciego wiersza.

    Zmienne można dodawać, klikając pusty wiersz i wpisując nazwę zmiennej.
  
5.  Kontynuuj debugowanie (naciśnij klawisz **F11** można poprawić debuger).  
  
 Powinny pojawić się zmiana jako Iterowanie za pomocą wartości zmiennych `for` pętli.  
  
 Jeśli Programowanie w kodzie natywnym czasami może być konieczne zakwalifikować kontekście nazwę zmiennej lub wyrażeniu zawierającym nazwę zmiennej. Kontekst jest funkcja, plik źródłowy i modułu, w którym znajduje się zmienną. Jeśli masz na kwalifikować się kontekstu za pomocą składni operatora kontekstu. Aby uzyskać więcej informacji, zobacz [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md).  
  
## <a name="observing-expressions-with-the-watch-window"></a>Obserwowania wyrażenia z okna czujki  
 Teraz spróbujmy użycie zamiast tego wyrażenia. Możesz dodać dowolne prawidłowe wyrażenie rozpoznany przez debuger.  
  
 Na przykład jeśli masz kod przedstawiony w poprzedniej sekcji, można uzyskać średnią z trzech wartości następująco:  
  
 ![Watch Expression](../debugger/media/watchexpression.png "WatchExpression")  
  
 W ogólności, zasady obliczania wyrażeń w **czujki** okna są takie same jak zasady obliczania wyrażeń języka programowania. Jeśli wyrażenie zawiera błąd składniowy, można oczekiwać, że ten sam błąd kompilatora, które są widoczne w edytorze kodu. Oto przykład:  
  
 ![Obejrzyj błąd wyrażenia](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a>Odświeżanie wartości czujki, które są nieaktualne  
 W pewnych okolicznościach, można napotkać ikony odświeżania (strzałka cykliczne) gdy wyrażenie jest obliczane w **czujki** okna.  Na przykład, jeśli masz obliczania właściwości wyłączone (**Narzędzia > Opcje > debugowanie > Włącz obliczanie właściwości i inne niejawne wywołania funkcji**), i mieć następujący kod:  
  
```CSharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Jeśli ustawisz czujki na `Count` właściwości listy, powinny zostać wyświetlone informacje takie jak następujące:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Na powyższej ilustracji przedstawiono błąd lub wartość, która jest nieaktualny. Wartość można odświeżyć ogólnie rzecz biorąc, klikając ikonę, ale w niektórych przypadkach może nie chcesz go odświeżyć. Najpierw musisz wiedzieć, dlaczego nie zostało obliczone wartości.  
  
 Po wskazaniu ikony etykietka narzędzia informacje na temat przyczyny nie zostało obliczone wyrażenie.  Jeśli pojawi się circling strzałki, wyrażenie nie zostało obliczone dla jednego z następujących powodów:  
  
-   Wystąpił błąd, ponieważ obliczeniem wyrażenie. Na przykład limit czasu może wystąpić lub zmienną mogły zostać poza zakresem.  
  
-   Wyrażenie zawiera wywołanie funkcji, które może wywołać efekt uboczny w aplikacji (zobacz [efekty uboczne i wyrażenia](#bkmk_sideEffects)).  
  
-   Automatyczne obliczanie właściwości i wywołania funkcji niejawna przez debuger jest wyłączone (**Narzędzia > Opcje > debugowanie > Włącz obliczanie właściwości i inne niejawne wywołania funkcji**), a następnie wyrażenie nie może być obliczane automatycznie.  
  
 Aby odświeżyć wartość, kliknij ikonę odświeżania lub naciśnij klawisz spacji. Debuger próbuje obliczyć ponownie wyrażenie. Jeśli ikona odświeżania pojawił się, ponieważ automatyczne obliczanie właściwości i inne niejawne wywołania funkcji zostało wyłączone, można obliczyć wyrażenia.  
  
 Jeśli widzisz ikonę, która jest koło dwa faliste wiersze, które przypominają wątków wyrażenie nie zostało obliczone z powodu potencjalnego zależności między wątkami. Innymi słowy oceny kodu wymaga inne wątki w tymczasowego uruchomienia aplikacji. Podczas pracy w trybie przerwania, zwykle zostały zatrzymane wszystkie wątki w aplikacji. Stosowanie innych wątków, aby uruchomić tymczasowo może mieć nieoczekiwane wpływ na stan programu i powoduje, że debuger do ignorowania zdarzenia, takie jak punkty przerwania i wyjątków zgłaszanych na tych wątków.  
  
##  <a name="bkmk_sideEffects"></a>Efekty uboczne i wyrażenia  
 Niektóre wyrażenia obliczenia można zmienić wartość zmiennej lub inaczej nie wpływa na stan programu. Na przykład obliczenie wyrażenia następujące zmienia wartość `var1`:  
  
```  
var1 = var2  
```  
  
 Ten kod może spowodować [ubocznym](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne mogą utrudnić debugowania przez zmianę sposobu działania programu.  
  
 Wyrażenie ma efekty uboczne jest oceniane tylko raz, po przejściu go. Kolejne oceny są wyłączone. Możesz ręcznie zmienić to zachowanie, klikając ikonę aktualizacji, która jest wyświetlana obok wartość.  
  
 Jest jednym ze sposobów uniknąć wszystkie efekty uboczne wyłączyć Obliczanie funkcji automatycznego (**Narzędzia > Opcje > debugowanie > Włącz obliczanie właściwości i inne niejawne wywołania funkcji**).  
  
 Podczas obliczania właściwości lub niejawne wywołania funkcji jest wyłączone, możesz wymusić oceny przy użyciu **ac** format modyfikator (C# tylko). Zobacz [sformatować Specyfikatory w języku C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="bkmk_objectIds"></a>Za pomocą identyfikatorów obiektów w oknie wyrażeń kontrolnych (C# i Visual Basic)  

 Brak razy, aby przyjrzeć się zachowaniu określonego obiektu. Na przykład można śledzić obiekt odwołuje się do zmiennej lokalnej po tej zmiennej wykroczyła poza zakres. W języku C# i Visual Basic można utworzyć obiektu identyfikatory dla określonych wystąpień typów referencyjnych i używać ich w oknie wyrażeń kontrolnych i warunków punktu przerwania. Identyfikator obiektu jest generowany przez środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług i skojarzone z obiektem.  
  
> [!NOTE]
>  Identyfikatory obiektów Utwórz słabe odwołania, a nie uniemożliwiają obiektu bezużytecznych. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
 Poniższy kod tworzy jedną metodę `Person` przy użyciu zmiennej lokalnej, ale chcesz poznać `Person`jego nazwa jest w innej metody:  
  
```CSharp  
class Person  
{  
    public Person(string name)  
    {  
        Name = name;  
    }  
    public string Name { get; set; }  
}  
  
public class Program  
{  
    List<Person> _people = new List<Person>();  
    public static void Main(string[] args)  
    {  
        MakePerson();  
        DoSomething();  
    }  
  
    private static void MakePerson()  
    {  
        var p = new Person("Bob");  
        _people.Add(p);  
    }  
  
    private static void DoSomething()  
    {  
        // more processing  
         Console.WriteLine("done");  
    }  
}  
  
```  
  
 Można dodać odwołanie do tego `Person` obiektu w **czujki** okna w następujący sposób:  
  
1.  Ustaw punkt przerwania w kodzie pewien czas, po utworzeniu obiektu.  
  
2.  Rozpocznij debugowanie, a podczas wykonywania zatrzyma się punkt przerwania, odnaleźć zmiennej w **zmiennych lokalnych** okna, kliknij go prawym przyciskiem myszy i wybierz **wprowadzić identyfikator obiektu**.  
  
3.  Powinny pojawić się  **$**  plus liczbą **zmiennych lokalnych** okna, które reprezentuje identyfikator obiektu.  
  
4.  Dodaj identyfikator obiektu do okna czujki.  
  
5.  Ustaw punkt przerwania, w którym chcesz obserwować zachowanie obiektu.  W powyższym kodzie wyniesie w `DoSomething()` metody.  
  
6.  Kontynuuj debugowanie i gdy zatrzyma wykonywanie `DoSomething()` metody **czujki** Wyświetla okna `Person` obiektu.  
  
> [!NOTE]
>  Jeśli chcesz wyświetlić właściwości obiektu, takie jak `Person.Name` w powyższym przykładzie, musisz włączyć obliczania wartości właściwości.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Korzystanie z rejestrów w oknie wyrażeń kontrolnych (tylko C++)  
 Jeśli są debugowanie kodu natywnego, możesz dodać nazwy rejestru, a także za pomocą nazwy zmiennych  **$ \<zarejestrować nazwę >** lub  **@ \<zarejestrować nazwę >**.  Aby uzyskać więcej informacji, zobacz [Pseudovariables](../debugger/pseudovariables.md).  
  
## <a name="dynamic-view-and-the-watch-window"></a>Widok dynamiczny i okno czujki  
 Niektóre języki skryptów (na przykład JavaScript lub Python) Użyj dynamicznych lub [kaczka wpisując](https://en.wikipedia.org/wiki/Duck_typing), i języków .NET (w wersji 4.0 lub nowszy) obsługuje obiekty, które są trudne do obserwować przy użyciu normalnego debugowania systemu windows, ponieważ ich może być czasu wykonywania właściwości i metody, których nie można wyświetlić.  
  
 Gdy okno czujki wyświetla obiektu utworzone na podstawie typu, który implementuje [interfejsu interfejs IDynamicMetaObjectProvider](/dotnet/api/system.dynamic.idynamicmetaobjectprovider?view=netframework-4.7), debuger dodaje specjalnego **widoku dynamicznego** węzeł **automatycznych**  wyświetlania. Ten węzeł zawiera dynamicznych elementów członkowskich obiektu dynamicznego, ale nie zezwala na edytowanie wartości elementów członkowskich.  
  
 Kliknięcie prawym przyciskiem myszy w dowolnym podrzędnym **widoku dynamicznego** i wybierz polecenie **Dodaj wyrażenie kontrolne**, debuger Wstawia nową zmienną czujki, który rzutuje obiekt na obiekt dynamiczny. Innymi słowy **nazwa obiektu** staje się (**obiektu (dynamiczny)). Nazwa**.  
  
 Ocena członków **widoku dynamicznego** może mieć efekty uboczne. Aby uzyskać informacje o skutki uboczne są zobacz [efekty uboczne i wyrażenia](#bkmk_sideEffects). Język C#, debuger nie automatycznie obliczyć ponownie wartości widoczne w **widoku dynamicznego** po kroku do nowego wiersza kodu. W języku Visual Basic wyrażenia dodane za pośrednictwem **widoku dynamicznego** są automatycznie odświeżane.  
  
 Aby uzyskać instrukcje dotyczące sposobu odświeżania wartości widoku dynamicznego, zobacz [wartości czujki odświeżanie, które są nieaktualne](#bkmk_refreshWatch).  
  
 Jeśli chcesz wyświetlić tylko **widoku dynamicznego** dla obiekt, można użyć **dynamiczne** specyfikatorze formatu:  
  
-   C#: **ObjectName dynamiczne**  
  
-   Visual Basic:: **$dynamic, nazwa obiektu**  
  
 **Widoku dynamicznego** zwiększa również działanie debugowania dla obiektów COM. Gdy debuger napotkał obiektów COM w **System.__ComObject**, dodaje **widoku dynamicznego** węzła dla obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuger systemu Windows](../debugger/debugger-windows.md)
