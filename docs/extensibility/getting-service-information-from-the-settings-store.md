---
title: Pobieranie informacji o usłudze z magazynu ustawienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11731e36517ae6245dddd1ebdd3b002fb3c37391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127506"
---
# <a name="getting-service-information-from-the-settings-store"></a>Pobieranie informacji o usłudze z ustawień magazynu
Aby odnaleźć wszystkie dostępne usługi lub w celu ustalenia, czy określona usługa jest zainstalowana, można użyć magazyn ustawień. Należy znać typu klasy usługi.  
  
### <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług  
  
1.  Tworzenie projektu VSIX o nazwie FindServicesExtension, a następnie dodaj niestandardowe polecenia o nazwie FindServicesCommand. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  W FindServicesCommand.cs, Dodaj następujące instrukcje using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Pobierz magazynu ustawienia konfiguracji, a następnie znajdź podkolekcję o nazwie usługi. Ta kolekcja zawiera wszystkie dostępne usługi. W metodzie MenuItemCommand Usuń istniejący kod i zastąp go następujące czynności:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string message = "Available services:\n";  
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");  
        int n = 0;  
        foreach (string service in collection)  
        {  
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";  
        }  
  
        MessageBox.Show(message);  
    }  
    ```  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
5.  W eksperymentalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **FindServicesCommand wywołania**.  
  
     Powinna zostać wyświetlona lista wszystkich usług okno komunikatu.  
  
     Aby sprawdzić te ustawienia, można użyć Edytora rejestru.  
  
## <a name="finding-a-specific-service"></a>Znajdowanie określonej usługi  
 Można również użyć <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodę, aby ustalić, czy określona usługa jest zainstalowana. Należy znać typu klasy usługi.  
  
1.  W MenuItemCallback projektu został utworzony w poprzedniej procedurze, Wyszukaj w sklepie ustawienia konfiguracji `Services` kolekcji, która ma podkolekcję o nazwie przez identyfikator GUID usługi. W takim przypadku firma Microsoft będzie szukać usługi pomocy.  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();  
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);  
        string message = "Help Service Available: " + hasHelpService;  
  
        MessageBox.Show(message);  
    }  
    ```  
  
2.  Skompiluj projekt i Rozpocznij debugowanie.  
  
3.  W eksperymentalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **FindServicesCommand wywołania**.  
  
     Powinien zostać wyświetlony komunikat z tekstem **pomocy usługi dostępne:** następuje **True** lub **False**. Aby sprawdzić to ustawienie, służy Edytora rejestru, jak pokazano w poprzednich krokach.