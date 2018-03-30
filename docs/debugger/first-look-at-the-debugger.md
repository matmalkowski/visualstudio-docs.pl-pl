---
title: Wprowadzenie do debugera w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 171b07d453c81883354848f70458bab39daa313e
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2018
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Wprowadzenie do debugera programu Visual Studio
Debuger programu Visual Studio jest łatwy w użyciu w dowolnym języku. W tym miejscu zostanie omówiony sposób debugowania prosty program C#, ale te same kroki można zastosować do kodu w innych językach, takich jak C++ i JavaScript.

Aby obejrzeć film przedstawiający podobne funkcje, zobacz [wprowadzenie do debugera](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Debugowanie projektu podstawowe języka C#  
 Zacznijmy od prostą aplikację konsoli języka C# (**Plik > Nowy > Projekt**, a następnie wybierz pozycję **Visual C#** , a następnie **aplikacji konsoli**). Jeśli nigdy nie pracował z programu Visual Studio przed, zobacz [wskazówki: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). **Main** metody tylko dodaje 1 do zmienna całkowitoliczbowa 10 razy i wynik do konsoli:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Tworzenie ten kod **debugowania** konfiguracji. Ta konfiguracja jest ustawieniem domyślnym. Aby uzyskać więcej informacji o konfiguracji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).  
  
 Uruchom ten kod w debugerze, klikając **Debuguj > Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**). Aplikacji powinny być kończone niemal natychmiast tak faktycznie nie można sprawdzić, czy wszystko zostało drukowany w oknie konsoli.  
  
 Wykonywania można zatrzymać wystarczająco długi, aby wyświetlić okno konsoli przez ustawienie punktu przerwania i krokowe wykonywanie wyprzedzeniem. Aby ustawić punkt przerwania, umieść kursor w `Console.WriteLine` wiersza, a następnie kliknij przycisk **debugowania > nowego punktu przerwania > przerwania funkcji**, lub kliknij na lewym marginesie, w tym samym wierszu. Punkt przerwania powinien wyglądać następująco:  
  
 ![Ustaw punkt przerwania](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Aby uzyskać więcej informacji na temat punktów przerwania, zobacz [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Sprawdź zmienne  
 Debugowanie często pociąga za sobą znajdowanie zmienne, które nie zawierają wartości, których można oczekiwać w określonym punkcie. Pokazano niektóre metody sprawdzić zmiennych.  
  
 Uruchom ponownie debugowanie. Zatrzymuje wykonanie przed `Console.WriteLine` kod jest wykonywany. Może spowodować jej do wykonania podczas przeglądania do przodu (kliknij **Debuguj > Step Over** lub **F10**). W takim przypadku można wybrano **Step Into** (**F11**) i zaakceptujesz takiego samego wyniku; wyjaśniamy różnica później. Wiersz z ostatnich nawias klamrowy metody powinny włączono żółty. Sprawdź okno konsoli. Powinny pojawić się **10**.  
  
 Umieszczeniu na **testInt** zmienną, aby wyświetlić bieżącą wartość w etykietce danych.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 Poniżej oknie Kod powinien zostać wyświetlony **automatycznych**, **zmiennych lokalnych**, i **czujki** systemu windows. Te okna Pokaż bieżące wartości zmiennych w czasie wykonywania. Zarówno **automatycznych** i **zmiennych lokalnych** Pokaż windows **testInt** o wartości **10**.  
  
 ![Okno zmiennych automatycznych podczas debugowania](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Aby uzyskać więcej informacji o tych z systemem windows, temacie [automatycznych i zmiennych lokalnych Windows](../debugger/autos-and-locals-windows.md).  
  
 Zobaczmy, jak wartość zmiennej zmienia jak możemy Przeprowadź przez program. Ustaw punkt przerwania na `testInt += 1;` wiersza i uruchom ponownie debugowanie. Powinny pojawić się który **testInt** w **zmiennych lokalnych** i **automatycznych** systemu windows jest **0**, i **i** jest **1**. Gdy Kontynuuj debugowanie (**Debuguj > Kontynuuj**, lub **Kontynuuj** na pasku narzędzi lub **F5**), można stwierdzić, że wartość **testInt** zmienia się na **1**, następnie **2**i tak dalej. Gdy zostanie wyświetlony gdy spojrzenie na te zmiany, Usuń punkt przerwania (**debugowania > Przełącz punkt przerwania**, lub kliknij ją na marginesie) i Kontynuuj debugowanie. Jeśli chcesz usunąć wszystkie punkty przerwania, kliknij przycisk **debugowania > Usuń wszystkie punkty przerwania**, lub **CTRL + SHIFT + F9**i kliknij przycisk **tak** w oknie dialogowym z pytaniem, **czy chcesz usunąć wszystkie punkty przerwania?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Wykonywanie krok po kroku do, jak i za pośrednictwem wywołania funkcji  
 Można wykonać kod w instrukcji za instrukcja debugera (**Step Into**) lub gdy debuger pomija funkcje można wykonywać kodu (**Step Over**) szybkie uzyskanie kodu czy interesuje Cię więcej () Funkcja wykonywany jest kod nadal). Można przełączać się między obu metod w tej samej sesji debugowania.  
  
 Różnice między **Step Into** i **Step Over**, należy dodać metody, która jest wywoływana przy użyciu innej metody. Dodawanie metody do aplikacji C# i wywołać ją z metody Main. Kod powinien wyglądać następująco:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Ustaw punkt przerwania na `Method1();` wywołania metody Main i Rozpocznij debugowanie. Podczas wykonywania dzieli, kliknij przycisk **debugowania > Wkrocz** (lub **Step Into** na pasku narzędzi lub **F11**). Podziały wykonywania ponownie w pierwszym nawias klamrowy w method1() poprzez odwołanie:  
  
 ![Przechodzenie do kodu](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Zatrzymaj debugowanie i uruchom ponownie, a podczas wykonywania dzieli się na punkt przerwania, kliknij przycisk **Debuguj > Step Over** (lub **Step Over** na pasku narzędzi lub **F10**). Wykonanie ponownie dzieli się na `Console.WriteLine("end");`.  
  
 Jeśli chcesz dowiedzieć się więcej o nawigowanie po kodzie z debugerem, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).