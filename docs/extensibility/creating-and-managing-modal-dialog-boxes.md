---
title: "Tworzenie i zarządzanie nimi modalnych okien dialogowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 466f39ea7ea4b7d5b79901b2503622d2248bb7a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Tworzenie i zarządzanie nimi modalnych okien dialogowych
Po utworzeniu modalne okno dialogowe w programie Visual Studio musi upewnij się, że okno nadrzędne w oknie dialogowym jest wyłączona, gdy zostanie wyświetlone okno dialogowe, a następnie ponownie włącz okno nadrzędne, po zamknięciu okna dialogowego. Jeśli nie zrobisz, zostanie wyświetlony błąd: "programu Microsoft Visual Studio nie może zamknąć, ponieważ modalne okno dialogowe jest aktywne. Zamknij okno dialogowe active i spróbuj ponownie."  
  
 Istnieją dwa sposoby w ten sposób. Zalecaną metodą, jeśli okno dialogowe WPF jest pochodzi z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, a następnie wywołać <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> do wyświetlenia okna dialogowego. Jeśli to zrobisz, nie trzeba zarządzać stanem modalne okno nadrzędne.  
  
 Twoje okno dialogowe nie jest WPF, czy niektóre inne przyczyny nie może pochodzić z okna dialogowego klasy z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, następnie należy uzyskać nadrzędnego okna dialogowego przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> i zarządzanie nimi stan modalny samodzielnie, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metody z Parametr 0 (false), przed wyświetleniem okna dialogowego i wywołanie metody ponownie, podając parametr 1 (PRAWDA), po zamknięciu okna dialogowego.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Okno dialogowe Tworzenie pochodnych DialogWindow  
  
1.  Tworzenie projektu VSIX o nazwie **OpenDialogTest** i Dodawanie polecenia menu o nazwie **OpenDialog**. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aby użyć <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> klasy, należy dodać odwołania do następujących zestawów (na karcie Framework **Dodaj odwołanie** okno dialogowe):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  W OpenDialog.cs, Dodaj następujący `using` instrukcji:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Deklarowanie klasy o nazwie **TestDialogWindow** która pochodzi z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Aby można było zminimalizowanie i Maksymalizuj okno dialogowe, należy ustawić <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> i <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  W **OpenDialog.ShowMessageBox** metody, Zastąp istniejący kod następującym kodem:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Skompiluj i uruchom aplikację. Powinna zostać wyświetlona eksperymentalne wystąpienie programu Visual Studio. Na **narzędzia** menu eksperymentalne wystąpienie powinny pojawić się polecenie o nazwie **OpenDialog wywołania**. Po kliknięciu tego polecenia, powinny pojawić się okno dialogowe. Można zminimalizować i zmaksymalizuj okno.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Tworzenie i zarządzanie nimi nie pochodzi od DialogWindow okno dialogowe  
  
1.  Do wykonania tej procedury, można użyć **OpenDialogTest** rozwiązania utworzony w poprzedniej procedurze, z tego samego odwołania do zestawów.  
  
2.  Dodaj następujące `using` deklaracje:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Utwórz klasę o nazwie **TestDialogWindow2** która pochodzi z <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Dodaj odwołanie prywatnych do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Dodaj Konstruktor, który ustawia odwołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  W **OpenDialog.ShowMessageBox** metody, Zastąp istniejący kod następującym kodem:  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  Skompiluj i uruchom aplikację. Na **narzędzia** menu powinny pojawić się polecenie o nazwie **OpenDialog wywołania**. Po kliknięciu tego polecenia, powinny pojawić się okno dialogowe.