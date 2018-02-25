---
title: "Debugowanie w czasie projektowania — Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33e0210023de05047957e7fbf55a8f970fda19d9
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Debugowanie w czasie projektowania w programie Visual Studio

W niektórych scenariuszach może być do debugowania kodu na projekt czasu zamiast, gdy aplikacja jest uruchomiona. Można to zrobić za pomocą **Immediate** okna. Jeśli chcesz debugować kodu XAML, który współdziała z innymi kodu, na przykład kod powiązania danych, możesz użyć **debugowania** > **dołączyć do procesu** w tym celu.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Debugowanie w czasie projektowania, w oknie bezpośrednim  

Można użyć programu Visual Studio **Immediate** okno, aby wykonać funkcji lub procedury, gdy aplikacja nie jest uruchomiona. Jeśli funkcja lub procedura zawiera punkt przerwania, Visual Studio spowoduje przerwanie wykonywania we właściwym momencie. Następnie można okna debugera Sprawdź swój stan programu. Ta funkcja jest nazywana debugowanie w czasie projektowania.  

Poniższy przykład jest w języku Visual Basic, ale **Immediate** okna jest również obsługiwany w aplikacji C# i C++.
  
1.  Wklej następujący kod w aplikacji konsoli języka Visual Basic:  
  
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
  
2.  Ustaw punkt przerwania w wierszu, `s="Add BreakPoint Here"`.  
  
3.  Otwórz **Immediate** okna (**debugowania** > **Windows** > **Immediate**) i wpisz następujące polecenie w okno: `?MyFunction<enter>`  
  
4.  Sprawdź, czy punkt przerwania został trafiony i że stosu wywołań są prawidłowe.  
  
5.  Na **debugowania** menu, kliknij przycisk **Kontynuuj**i upewnij się, że jesteś nadal w trybie projektowania.  
  
6.  Wpisz następujące polecenie w **Immediate** okno: `?MyFunction<enter>`  
  
7.  Wpisz następujące polecenie w **Immediate** okno: `?MySub<enter>`  
  
8.  Sprawdź, czy trafiony punkt przerwania i sprawdź wartość statyczna zmienna `i` w **zmiennych lokalnych** okna. Powinien mieć wartość 3.  
  
9. Sprawdź, czy stos wywołań jest dokładne.  
  
10. Na **debugowania** menu, kliknij przycisk **Kontynuuj**i upewnij się, że jesteś nadal w trybie projektowania.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Debugowanie w czasie projektowania przy użyciu projektanta XAML

Może być przydatne do debugowania kodu za przy użyciu projektanta XAML w niektórych scenariuszach powiązanie dane deklaratywne.

1. W projekcie, Dodaj nową stronę XAML, takich jak *temp.xaml*. Nowa strona XAML może pozostać puste. 

1. Skompiluj rozwiązanie.

1. Otwórz *temp.xaml*, który ładuje projektanta (*UwpSurface.exe* w aplikacji platformy uniwersalnej systemu Windows lub *XDesProc.exe*), możesz dołączyć do niego w kolejnych krokach. 

1. Otwórz nowe wystąpienie programu Visual Studio. Otwórz nowe wystąpienie **dołączyć do procesu** okno dialogowe (**debugowania** > **dołączyć do procesu**) ustaw **dołączyć do** pole typu prawidłowego kodu, takie jak **kodu zarządzanego (środowisko CoreCLR)** lub typ prawidłowego kodu zależnie od wersji platformy .NET. Wybierz z listy poprawny proces projektanta, a **Attach**.

    Dla platformy uniwersalnej systemu Windows projektach przeznaczonych dla kompilacji 16299 lub nowszego, proces projektanta *UwpSurface.exe*. WPF lub wersji platformy uniwersalnej systemu Windows Wstecz, aby 16299 proces projektanta jest *XDesProc.exe*.

1. Dołączony do procesu, przełącz się do projektu, otwórz kod związany z którym chcesz debugować i ustaw punkt przerwania.

1. Na koniec Otwórz stronę, która zawiera kod XAML, który zawiera powiązanie danych.

    Na przykład można ustawić punktu przerwania w kodzie konwerter typu dla następujących XAML, który wiąże blok tekstu w czasie projektowania.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Podczas ładowania strony punkt przerwania zostaje trafiony.
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
