---
title: Debugowanie w czasie projektowania — Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1235e6360ccc5f6c0677f7ec9acb1dd85cad226
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180181"
---
# <a name="debug-at-design-time-in-visual-studio"></a>Debugowanie w czasie projektowania w programie Visual Studio

W niektórych przypadkach warto możliwe jest debugowanie kodu na projekt czasu zamiast, gdy aplikacja jest uruchomiona. Można to zrobić za pomocą **bezpośrednie** okna. Jeśli chcesz debugować kodu XAML, który wchodzi w interakcję z innego kodu, takie jak kod powiązania danych, możesz użyć **debugowania** > **dołączyć do procesu** Aby to zrobić.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Debugowanie w czasie projektowania za pomocą okna bezpośredniego  

Możesz użyć programu Visual Studio **bezpośrednie** okna do wykonania funkcji lub podprocedury, gdy aplikacja nie jest uruchomiona. Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio spowoduje przerwanie wykonywania we właściwym miejscu. Można następnie użyć okien debugera do sprawdzenia stanu programu. Ta funkcja jest wywoływana, debugowanie w czasie projektowania.  

Poniższy przykład jest w języku Visual Basic, ale **bezpośrednie** okno jest również obsługiwane w aplikacjach języka C# i C++.
  
1.  Wklej następujący kod do aplikacji konsoli Visual Basic:  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Ustaw punkt przerwania w wierszu, który odczytuje, `s="Add BreakPoint Here"`.  
  
3.  Otwórz **bezpośrednie** okna (**debugowania** > **Windows** > **bezpośrednie**) i wpisz następujące polecenie w okno: `?MyFunction<enter>`  
  
4.  Sprawdź, czy punkt przerwania został trafiony i że stos wywołań jest prawidłowo wprowadzony.  
  
5.  Na **debugowania** menu, kliknij przycisk **Kontynuuj**i sprawdź, że jesteś nadal w trybie projektowania.  
  
6.  Wpisz następujące polecenie w **bezpośrednie** okna: `?MyFunction<enter>`  
  
7.  Wpisz następujące polecenie w **bezpośrednie** okna: `?MySub<enter>`  
  
8.  Sprawdź, czy trafiony punkt przerwania i sprawdzić wartość zmiennej statycznej `i` w **lokalne** okna. Powinien mieć wartość 3.  
  
9. Sprawdź, czy wywołanie stosu jest prawidłowa.  
  
10. Na **debugowania** menu, kliknij przycisk **Kontynuuj**i sprawdź, że jesteś nadal w trybie projektowania.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Debugowanie w czasie projektowania przy użyciu projektanta XAML

Może być przydatne debugować kod związany z projektanta XAML w niektórych scenariuszach powiązania dane deklaratywne.

1. W projekcie, Dodaj nową stronę XAML, takich jak *temp.xaml*. Nowa strona XAML należy pozostawić pusty. 

1. Skompiluj rozwiązanie.

1. Otwórz *temp.xaml*, który ładuje projektanta (*UwpSurface.exe* w aplikacji platformy uniwersalnej systemu Windows lub *XDesProc.exe*), dzięki czemu możesz dołączyć do niego w kolejnych krokach. 

1. Otwórz nowe wystąpienie programu Visual Studio. Otwórz w nowym wystąpieniu **dołączyć do procesu** okno dialogowe (**debugowania** > **dołączyć do procesu**) ustaw **dołączyć do** pole do typu prawidłowego kodu, takich jak **kodu zarządzanego (CoreCLR)** lub wpisz poprawny kod zależnie od wersji platformy .NET. Z listy wybierz poprawny procesu projektanta i wybierz polecenie **Dołącz**.

    Dla platformy UWP projekty przeznaczone dla kompilacji 16299 lub nowszego, proces projektanta *UwpSurface.exe*. WPF lub wersje platformy uniwersalnej systemu Windows przed 16299 proces projektanta jest *XDesProc.exe*.

1. Gdy dołączony do procesu, przejdź do swojego projektu, otwórz kod związany z którym chcesz debugować i ustaw punkt przerwania.

1. Wreszcie Otwórz stronę, która zawiera kod XAML, który zawiera powiązanie danych.

    Na przykład można ustawić punkt przerwania w kodzie konwerter typu dla następujących XAML, który wiąże TextBlock w czasie projektowania.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Po załadowaniu strony zostanie osiągnięty punkt przerwania.
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/getting-started-with-the-debugger.md)
