---
title: 'Wskazówki: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 585a33a8a3c49792be0cc986b36636e7107290ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Wskazówki: tworzenie niestandardowego Instalatora dla aplikacji ClickOnce
Dyskretnie zainstalować żadnych aplikacji ClickOnce, na podstawie pliku .exe i aktualizowane przez instalatora niestandardowego. Niestandardowy Instalator można zaimplementować środowisko użytkownika podczas instalacji, w tym niestandardowych okien dialogowych dla operacji zabezpieczeń i konserwacji. Aby wykonać operacje instalacji, używa niestandardowego Instalatora <xref:System.Deployment.Application.InPlaceHostingManager> klasy. Ten przewodnik przedstawia sposób tworzenia niestandardowego instalatora instalacji dyskretnej aplikacji ClickOnce.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Aby utworzyć niestandardowy Instalator aplikacji ClickOnce  
  
1.  W aplikacji ClickOnce Dodaj odwołania do System.Deployment i System.Windows.Forms.  
  
2.  Dodaj nową klasę do aplikacji i określić dowolną nazwę. W tym przewodniku zastosowano nazwę `MyInstaller`.  
  
3.  Dodaj następujące `Imports` lub `using` instrukcje na początku nowej klasy.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Dodaj następujące metody do klasy.  
  
     Te metody mogą wywoływać <xref:System.Deployment.Application.InPlaceHostingManager> metody pobierania manifest rozmieszczenia assert odpowiednie uprawnienia, monitowanie użytkownika o zezwolenie na zainstalować, a następnie Pobierz i zainstaluj aplikację do pamięci podręcznej ClickOnce. Niestandardowy Instalator można określić, że aplikacji ClickOnce jest wstępnie zaufany lub może odroczyć decyzja dotycząca zaufania do <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> wywołania metody. Ten kod ufa wstępnie aplikacji.  
  
    > [!NOTE]
    >  Uprawnienia przypisane przez wstępnie ufające nie może przekraczać uprawnień kodu niestandardowego Instalatora.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Próba instalacji w kodzie, wywołaj `InstallApplication` metody. Na przykład, jeśli nazwę klasy `MyInstaller`, może wywołać `InstallApplication` w następujący sposób.  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>Następne kroki  
 Aplikacji ClickOnce, można również dodać logikę aktualizacji niestandardowych, łącznie z niestandardowego interfejsu użytkownika do wyświetlenia podczas procesu aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikacji ClickOnce można również pominąć standardową pozycję menu Start, skrótów i wpis Dodaj lub usuń programy, za pomocą `<customUX>` elementu. Aby uzyskać więcej informacji, zobacz [ \<Punkt_wejścia > Element](../deployment/entrypoint-element-clickonce-application.md) i <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > — Element](../deployment/entrypoint-element-clickonce-application.md)