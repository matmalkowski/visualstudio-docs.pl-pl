---
title: "Za pomocą magazynu ustawienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1d62e3ccc47a2b74629cd1468b023c787a1289e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-settings-store"></a>Przy użyciu ustawień magazynu
Istnieją dwa rodzaje ustawień magazynów:  
  
-   Ustawienia konfiguracji, które są tylko do odczytu ustawień programu Visual Studio i pakiet VSPackage. Visual Studio scala ustawienia z wszystkich plików znanych .pkgdef tego magazynu.  
  
-   Ustawienia użytkownika, które są zapisywalne ustawienia, takie jak te, które są wyświetlane na stronach **opcje** — okno dialogowe strony właściwości i niektórych innych oknach dialogowych. Rozszerzenia programu Visual Studio mogą ich używać do lokalnego magazynu małe ilości danych.  
  
 W tym przewodniku pokazano, jak można odczytać danych z magazynu ustawienia konfiguracji. Zobacz [zapisywania w magazynie ustawienia użytkownika](../extensibility/writing-to-the-user-settings-store.md) opis zapisu w magazynie ustawień użytkownika.  
  
## <a name="creating-the-example-project"></a>Tworzenie przykładowy projekt  
 W tej sekcji przedstawiono sposób tworzenia prostego rozszerzenia projektu za pomocą polecenia menu do pokazania.  
  
1.  Każde rozszerzenie programu Visual Studio rozpoczyna się od VSIX Projekt wdrożenia, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projektu o nazwie `SettingsStoreExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Teraz Dodaj szablon elementu polecenia niestandardowych o nazwie **SettingsStoreCommand**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **SettingsStoreCommand.cs**. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Za pomocą magazynu ustawień konfiguracji  
 W tej sekcji przedstawiono sposób wykrywania i wyświetlić ustawienia konfiguracji.  
  
1.  W pliku SettingsStorageCommand.cs, Dodaj następujące instrukcje using:  
  
    ```  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
2.  W `MenuItemCallback`, Usuń treść metody i Dodaj te wiersze pobrać magazynu ustawienia konfiguracji:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
    SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Jest klasa pomocy zarządzane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> usługi.  
  
3.  Teraz Dowiedz się, czy zostały zainstalowane narzędzia Windows Phone. Kod powinien wyglądać następująco:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
        string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Testowanie kodu. Skompiluj projekt i Rozpocznij debugowanie.  
  
5.  W eksperymentalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **SettingsStoreCommand wywołania**.  
  
     Powinien zostać wyświetlony komunikat pole **Microsoft Windows Phone Developer Tools:** następuje **True** lub **False**.  
  
 Visual Studio zachowuje ustawienia magazynu w rejestrze systemu.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Aby sprawdzić ustawienia konfiguracji za pomocą Edytora rejestru  
  
1.  Otwórz Regedit.exe.  
  
2.  Przejdź do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Upewnij się, że są patrzeć klucz, który zawiera \14.0Exp_Config\ i nie \14.0_Config\\. Po uruchomieniu eksperymentalne wystąpienie programu Visual Studio, ustawienia konfiguracyjne znajdują się w gałęzi rejestru "14.0Exp_Config".  
  
3.  Rozwiń węzeł \Installed Products\. Jeśli komunikat w poprzednich krokach jest **Microsoft Windows Phone Developer Tools zainstalowany: True**, a następnie \Installed Products\ powinien zawierać węzeł Microsoft Windows Phone Developer Tools. Jeśli komunikat jest **Microsoft Windows Phone Developer Tools zainstalowany: False**, a następnie \Installed Products\ nie powinna zawierać węzeł Microsoft Windows Phone Developer Tools.