---
title: "Zarządzanie wyjątkami za pomocą debugera programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c04934aed17c6e1b00664d371ff591ebbc3486a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Zarządzanie wyjątkami za pomocą debugera programu Visual Studio

Wyjątkiem jest wskazaniem stanu błędu, który występuje, gdy program jest wykonywana. Debuger można określić, które wyjątków (lub zestawy wyjątków) podziału na i w takim przypadku ma debugera, aby przerwać (gdy debuger dzieli, przedstawia on której wystąpił wyjątek). Można również dodawać lub usuwać wyjątków. Rozwiązania otwarte w programie Visual Studio, za pomocą **debugowania > Windows > Ustawienia wyjątków** otworzyć **ustawienia wyjątków** okna. 

Możesz i powinien zawierać programy obsługi, które odpowiadają na najważniejszych wyjątki, ale ważne jest, aby dowiedzieć się, jak można skonfigurować debugera, aby zawsze przerwać wykonywanie niektóre wyjątki.
  
Gdy wystąpi wyjątek, debuger zapisuje komunikat o wyjątku w oknie danych wyjściowych. Może on przerwać wykonywanie w następujących przypadkach:  
  
-   Wyjątek jest zgłaszany po nie jest obsługiwana.  
  
-   Jest wywoływane, gdy debuger jest skonfigurowany do Przerwij wykonywanie, przed dowolnego programu obsługi.  
  
-   Jeśli ustawiono [tylko mój kod](../debugger/just-my-code.md), i Debuger jest skonfigurowany do dzielenia na żadnym wyjątku, który nie jest obsługiwany w kodzie użytkownika.  
  
> [!NOTE]
>  Program ASP.NET ma obsługi wyjątków najwyższego poziomu, która zawiera błąd strony w przeglądarce. Go nie Przerwij wykonywanie, chyba że **tylko mój kod** jest włączona. Na przykład zobacz [ustawienia debugera, aby kontynuować na wyjątkach nieobsługiwanych przez użytkownika](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) poniżej.  
  
> [!NOTE]
>  W aplikacji Visual Basic debuger zarządza wszystkie błędy jako wyjątki, nawet jeśli używasz na programy obsługi błędów stylu błędu.    
  
## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Poinformuj debugera przerwanie podczas zgłoszenia wyjątku  
Debuger może przerwać wykonywanie w momencie, gdy jest zgłaszany wyjątek, co daje możliwość zbadać wyjątek, zanim program obsługi jest wywoływany.  
  
W **ustawienia wyjątków** okna (**debugowania > Windows > Ustawienia wyjątków**), rozwiń węzeł kategorii wyjątków (na przykład **wspólnego języka środowiska uruchomieniowego wyjątki**, co oznacza wyjątki .NET) i zaznacz pole wyboru dla określonego wyjątku w ramach tej kategorii (na przykład **System.AccessViolationException**). Można również wybrać cały kategorię wyjątków.  
  
![Zaznaczone accessviolationexception —](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  

> [!TIP]
> Określonych wyjątków można znaleźć przy użyciu **wyszukiwania** okna w **ustawienia wyjątków** paska narzędzi lub Użyj wyszukiwania do filtrowania dla określonych przestrzeni nazw (na przykład **System.IO**).
  
W przypadku wybrania wyjątek **ustawienia wyjątków** okna, spowoduje przerwanie wykonywania debugera, wszędzie tam, gdzie wyjątek jest zgłaszany, niezależnie od tego, czy jest obsługiwane i nieobsługiwane. W tym momencie wyjątek nosi nazwę pierwszy wyjątek szansy. Na przykład poniżej przedstawiono kilka scenariuszy:  
  
*  W poniższych aplikacji konsolowej C#, metoda Main zgłasza **accessviolationexception —** wewnątrz `try/catch` bloku:  
  
    ```CSharp  
    static void Main(string[] args)  
    {  
        try  
        {  
            throw new AccessViolationException();  
            Console.WriteLine("here");  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("caught exception");  
        }  
        Console.WriteLine("goodbye");  
    }  
    ```  
  
     Jeśli masz **accessviolationexception —** zaewidencjonowany **ustawienia wyjątków**, po uruchomieniu tego kodu podczas wykonywania debugera spowoduje przerwanie na `throw` wiersza. Następnie można kontynuować wykonywania. Obie linie powinien być wyświetlany w konsoli:  
  
    ```  
    caught exception  
    goodbye  
    ```  
  
     ale nie są wyświetlane `here` wiersza.  
  
*  Biblioteki klas z klasy, która ma dwie metody, metoda zgłasza wyjątek, który go obsługuje oraz drugiej metody, w tym samym wyjątek, który nie obsługuje on odwołuje się do aplikacji konsolowej C#:  
  
    ```csharp 
    public class Class1  
    {  
        public void ThrowHandledException()  
        {  
            try  
            {  
                throw new AccessViolationException();  
            }  
            catch (AccessViolationException ave)  
            {  
                Console.WriteLine("caught exception" + ave.Message);  
            }  
        }  
  
        public void ThrowUnhandledException()  
        {  
            throw new AccessViolationException();  
        }  
    }  
    ```  
  
     Poniżej przedstawiono metody Main() aplikacji konsoli:  
  
    ```CSharp  
    static void Main(string[] args)  
    {  
        Class1 class1 = new Class1();  
        class1.ThrowHandledException();  
        class1.ThrowUnhandledException();  
    }  
    ```  
  
     Jeśli masz **accessviolationexception —** zaewidencjonowany **ustawienia wyjątków**, po uruchomieniu tego kodu podczas wykonywania debugera spowoduje przerwanie na `throw` wiersza w obu  **ThrowHandledException()** i **ThrowUnhandledException()**.  
  
 Jeśli chcesz przywrócić wartości domyślne ustawienia wyjątków, możesz kliknąć **przywrócić** przycisk na pasku narzędzi:  
  
 ![Przywróć ustawienia domyślne w ustawieniach wyjątek](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
##  <a name="BKMK_UserUnhandled"></a>Poinformuj debugera, aby kontynuować na wyjątkach nieobsługiwanych przez użytkownika  
 Jeśli debugowania kodu .NET lub JavaScript z [tylko mój kod](../debugger/just-my-code.md), można ustalić debugera nie, aby przerwać na wyjątki, które nie są obsługiwane w kodzie użytkownika, ale są obsługiwane w innym miejscu.  
  
1.  W **ustawienia wyjątków** okna, otwórz menu kontekstowe okna prawym przyciskiem myszy, a następnie wybierając **Pokaż kolumny**. (Jeśli wyłączysz **tylko mój kod**, nie zobaczysz tego polecenia.)  
  
2.  Powinny pojawić się druga kolumna o nazwie **dodatkowe akcje**. Ta kolumna zawiera **Kontynuuj w przypadku braku przez kod użytkownika** na określonych wyjątków, co oznacza, że debuger nie podział wtedy, gdy ten wyjątek nie jest obsługiwane w kodzie użytkownika, ale jest obsługiwane w kodzie zewnętrznych.  
  
3.  Możesz zmienić to ustawienie, albo dla określonego wyjątku (wybierz wyjątek, kliknij prawym przyciskiem myszy i wybierz/usunięcie zaznaczenia **Kontynuuj w przypadku braku kodu użytkownika**) lub dla całego kategorii wyjątków (na przykład wszystkie typowe Wyjątki czasu wykonywania języka).  
  
 Na przykład aplikacji sieci web ASP.NET obsługi wyjątków, konwertując je na kod stanu HTTP 500 ([obsługi wyjątków w interfejsu API platformy ASP.NET](http://www.asp.net/web-api/overview/error-handling/exception-handling)), które mogą nie pomóc określić źródło wyjątku. W poniższym przykładzie kod użytkownika wywołuje `String.Format()` który zgłasza <xref:System.FormatException>. Wykonanie dzieli w następujący sposób:  
  
 ![podziały na użytkownika &#45; wyjątek unhanlded](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
## <a name="add-and-delete-exceptions"></a>Dodawanie i usuwanie wyjątków  
 Można dodawać i usuwać wyjątków. Dowolnego typu wyjątku można usunąć z każdej kategorii, wybierając wyjątek i klikając **usunąć** przycisk (znak minus) na **ustawienia wyjątków** paska narzędzi lub klikając prawym przyciskiem myszy wyjątek i Wybieranie **usunąć** z menu kontekstowego. Usuwanie wyjątek ma ten sam efekt jako mający wyjątku nie jest zaznaczona, czyli, że debuger nie będę powodować utraty, gdy jest on generowany.  
  
 Aby dodać wyjątek: w **ustawienia wyjątków** okna, wybierz jedną z kategorii wyjątku (na przykład **środowisko uruchomieniowe języka wspólnego**) i kliknij przycisk **Dodaj** przycisku. Wpisz nazwę wyjątku (np. **System.UriTemplateMatchException**). Wyjątek został dodany do listy (w kolejności alfabetycznej) i automatycznie jest zaznaczone.  
  
 Jeśli chcesz dodać wyjątek wyjątki dostępu do pamięci procesora GPU, wyjątki środowiska wykonawczego języka JavaScript lub kategorie wyjątki Win32 konieczne podanie kodu błędu, a także opis.  
  
> [!TIP]
>  Sprawdź pisownię! **Ustawienia wyjątków** okna nie sprawdza istnienie dodano wyjątek. Dlatego w przypadku wpisania **Sytem.UriTemplateMatchException**, otrzymasz wpis dla tego wyjątku (a nie **System.UriTemplateMatchException**).  
  
 Ustawienia wyjątków są zachowywane w plik .suo rozwiązania, więc odnoszą się do danego rozwiązania. Nie można ponownie użyć ustawień określonych wyjątków w rozwiązań. W tym momencie są trwałe tylko wyjątki dodane; Usunięto wyjątków nie są. Innymi słowy możesz dodać wyjątek, zamknij i ponownie otwórz rozwiązanie, a wyjątek będą nadal dostępne. Jednak po usunięciu wyjątek i zamknij i otwórz ponownie rozwiązanie, pojawi się wyjątek.  
  
 **Ustawienia wyjątków** okna obsługuje typów wyjątków ogólnych w języku C#, ale nie w języku Visual Basic. Przerwanie na wyjątki, takich jak `MyNamespace.GenericException<T>`, należy dodać wyjątek jako **MyNamespace.GenericException'1**. Oznacza to jeśli został utworzony wyjątek następująco:  
  
```CSharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Można dodać wyjątku, aby **ustawienia wyjątków** podobnie do następującej:  
  
 ![Dodawanie wyjątków ogólnych](../debugger/media/addgenericexception.png "AddGenericException")  

## <a name="add-conditions-to-an-exception"></a>Dodawanie warunków do Wystąpił wyjątek

Można ustawić warunki na wyjątki w **ustawienia wyjątków** okno dialogowe. Obecnie obsługiwane warunki obejmować nazwy modułu do dołączania lub wykluczania dla wyjątku. Przez ustawienie nazwy modułu warunków, użytkownik może przerwać wyjątek tylko w określonym kodem modułów, lub można uniknąć dzielenia na konkretnym modułów.

> [!NOTE]
> Dodawanie warunków do wyjątku jest nowa w programie[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Aby dodać warunkowego wyjątki, wybierz **Edytuj warunek** ikonę w oknie dialogowym Ustawienia wyjątków polu lub kliknij prawym przyciskiem myszy wyjątek i wybierz polecenie **edytowanie warunków**.

![Warunki po wystąpieniu wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")
  
## <a name="see-also"></a>Zobacz też  
 [Kontynuowanie wykonania po wyjątkach](../debugger/continuing-execution-after-an-exception.md)   
 [Porady: Badanie kodu systemu po wystąpieniu wyjątku](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Porady: Użyj macierzystego sprawdzania w trakcie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [Sprawdza przy użyciu czasu wykonywania bez biblioteki wykonawczej języka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)