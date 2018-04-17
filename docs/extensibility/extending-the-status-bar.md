---
title: Rozszerzanie pasek stanu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a766e0c607d4d669fada794e1cf0779559f2346b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-status-bar"></a>Rozszerzanie paska stanu
Pasek stanu programu Visual Studio w dolnej części IDE służy do wyświetlania informacji.  
  
 Podczas rozszerzania paska stanu w regionach cztery można wyświetlić interfejsu użytkownika i informacji: region opinii, pasek postępu, region animacji i region projektanta. Region opinii służy do wyświetlania tekstu i wyróżnianie tekstu wyświetlanego. Pasek postępu pokazuje przyrostowego postępu dla operacji wykonywania short, takie jak zapisywanie pliku. Region animacji Wyświetla animację stale zwracane dla długotrwałe operacje lub operacji nieokreślonej długości, takich jak tworzenie wielu projektów w rozwiązaniu. I projektanta regionu pokazuje liczbę wierszy i kolumn lokalizacji kursora.  
  
 Pasek stanu można uzyskać za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfejsu (z <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> usługi). Ponadto każdy obiekt ulokowany na ramkę okna można zarejestrować stanu paska obiektu klienta zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfejsu. Zawsze, gdy okno jest aktywna, Visual Studio wysyła zapytanie ulokowany w tym oknie dla obiekt `IVsStatusbarUser` interfejsu. Jeśli znaleziono, wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metoda w interfejsie zwrócony i obiektu można zaktualizować na pasku stanu w ramach tej metody. Dokumentu systemu windows, na przykład, można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodę, aby zaktualizować informacje w regionie projektanta, gdy stanie się aktywne.  
  
 W poniższych procedurach założono, że rozumiesz sposób tworzenia projektu VSIX i Dodawanie polecenia niestandardowego menu. Aby uzyskać informacje, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modyfikowanie paska stanu  
 W tej procedurze przedstawiono sposób ustawić tekstu, wyświetlić tekst statyczny i zaznacz wyświetlanego tekstu w regionie opinii na pasku stanu.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Odczytywanie i zapisywanie do paska stanu  
  
1.  Tworzenie projektu VSIX o nazwie **TestStatusBarExtension** i Dodawanie polecenia menu o nazwie **TestStatusBarCommand**.  
  
2.  W TestStatusBarCommand.cs Zastąp kod metody obsługi polecenia (MenuItemCallback) z następujących czynności:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  Należy skompilować kod i Rozpocznij debugowanie.  
  
4.  Otwórz **narzędzia** menu w eksperymentalne wystąpienie programu Visual Studio. Kliknij przycisk **wywołania TestStatusBarCommand** przycisku.  
  
     Powinny pojawić się który tekst w pasku odczyty teraz stanu **"Tylko napisaliśmy na pasku stanu."** i w wyświetlonym oknie komunikatu ma tego samego tekstu.  
  
#### <a name="updating-the-progress-bar"></a>Aktualizowanie pasek postępu  
  
1.  W tej procedurze firma Microsoft będzie pokazują, jak zainicjować i zaktualizuj pasek postępu.  
  
2.  Otwórz plik TestStatusBarCommand.cs i Zastąp metodę MenuItemCallback następującym kodem:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  Należy skompilować kod i Rozpocznij debugowanie.  
  
4.  Otwórz **narzędzia** menu w eksperymentalne wystąpienie programu Visual Studio. Kliknij przycisk **wywołania TestStatusBarCommand** przycisku.  
  
     Powinny pojawić się który tekst w pasku odczyty teraz stanu **"Zapisywanie paska postępu".** Również powinien być widoczny pasek postępu pobierania aktualizacji w ciągu sekundy przez 20 sekund. Następnie na pasku stanu i pasek postępu zostały wyczyszczone.  
  
#### <a name="displaying-an-animation"></a>Wyświetlanie animacji  
  
1.  Pasek stanu wyświetla pętli animacji, która wskazuje albo długotrwałej operacji (na przykład tworzenie wielu projektów w rozwiązaniu). Jeśli nie ma tego animacji, upewnij się, masz właściwą **narzędzia / Opcje** ustawienia:  
  
     Przejdź do **narzędzia/Opcje / ogólne** karcie i usuń zaznaczenie pola wyboru **automatycznie Dostosuj wyglądu oparte na wydajność klienta**. Następnie zaznacz opcję podrzędne **Włącz bogate doświadczenia wizualne**. Teraz można wyświetlać animacji, podczas kompilowania projektu w eksperymentalnym wystąpieniu programu Visual Studio.  
  
     W tej procedurze wyświetli standardowe animacji programu Visual Studio, reprezentujący tworzenia projektu lub rozwiązania.  
  
2.  Otwórz plik TestStatusBarCommand.cs i Zastąp metodę MenuItemCallback następującym kodem:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  Należy skompilować kod i Rozpocznij debugowanie.  
  
4.  Otwórz **narzędzia** w eksperymentalne wystąpienie programu Visual Studio i kliknij przycisk menu **TestStatusBarCommand wywołania**.  
  
     Po wyświetleniu okna komunikatu powinno również zostać wyświetlone animacji na pasku stanu po prawej. Gdy zamknąć okno komunikatu, zniknie animacji.