---
title: Zapisywanie w magazynie ustawienia użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e205fa8850bdd5ee664f66c6d6bb7bf86195bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawienia użytkownika
Ustawienia użytkownika są zapisywalne ustawienia, takie jak te w **narzędzia / Opcje** okna dialogowego Właściwości systemu windows i niektórych okien dialogowych. Rozszerzenia programu Visual Studio może użyć tych do przechowywania niewielkich ilości danych. W tym przewodniku przedstawiono sposób dodawania Notatnik dla programu Visual Studio jako narzędzie zewnętrzne za odczytywanie z oraz zapisywanie w magazynie ustawień użytkownika.  
  
### <a name="backing-up-your-user-settings"></a>Tworzenie kopii zapasowej ustawień użytkownika  
  
1.  Musi być w stanie zresetowanie ustawień zewnętrznych narzędzi, dzięki czemu można debugować i powtórz procedurę. Aby to zrobić, musisz zapisać oryginalne ustawienia, aby można go przywrócić zgodnie z potrzebami.  
  
2.  Otwórz Regedit.exe.  
  
3.  Przejdź do narzędzia HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Upewnij się, że są patrzeć klucz, który zawiera \14.0Exp\ i nie \14.0\\. Po uruchomieniu eksperymentalne wystąpienie programu Visual Studio, ustawienia użytkownika są w gałęzi rejestru "14.0Exp".  
  
4.  Kliknij prawym przyciskiem myszy podklucz \External Tools\, a następnie kliknij przycisk **wyeksportować**. Upewnij się, że **wybrana gałąź** jest zaznaczone.  
  
5.  Zapisz plik wynikowy Tools.reg zewnętrznych.  
  
6.  Później, gdy chcesz zresetować ustawienia zewnętrznych narzędzi, wybierz HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ klucza rejestru i kliknij przycisk **usunąć** w menu kontekstowym.  
  
7.  Gdy **Potwierdzanie usunięcia klucza** zostanie wyświetlone okno dialogowe, kliknij przycisk **tak**.  
  
8.  Kliknij prawym przyciskiem myszy plik Tools.reg zewnętrznego, który został wcześniej zapisany, kliknij przycisk **Otwórz za pomocą**, a następnie kliknij przycisk **Edytora rejestru**.  
  
## <a name="writing-to-the-user-settings-store"></a>Zapisywanie w magazynie ustawienia użytkownika  
  
1.  Tworzenie projektu VSIX o nazwie UserSettingsStoreExtension, a następnie dodaj niestandardowe polecenia o nazwie UserSettingsStoreCommand. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  W UserSettingsStoreCommand.cs, Dodaj następujące instrukcje using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  W MenuItemCallback Usuń treść metody i pobrać użytkownika, którego ustawienia przechowywania w następujący sposób:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Teraz Dowiedz się, czy Notepad jest już ustawiony jako narzędzie zewnętrzne. Musisz wykonać iterację wszystkich zewnętrznych narzędzi do ustalenia, czy ustawienie ToolCmd jest "Notatnik", w następujący sposób:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  Notatnik nie została ustawiona jako narzędzie zewnętrzne, ustaw go w następujący sposób:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  Testowanie kodu. Należy pamiętać, zostaje włączona Notatnik jako narzędzie zewnętrzne, dlatego należy wycofać rejestru przed jego uruchomieniem po raz drugi.  
  
7.  Skompilować kod i Rozpocznij debugowanie.  
  
8.  Na **narzędzia** menu, kliknij przycisk **UserSettingsStoreCommand wywołania**. Spowoduje to dodanie Notatnik **narzędzia** menu.  
  
9. Teraz powinien zostać wyświetlony Notatnik w menu Narzędzia / Opcje menu, a następnie klikając polecenie **Notatnik** powinna wywołać wystąpienia Notatnika.