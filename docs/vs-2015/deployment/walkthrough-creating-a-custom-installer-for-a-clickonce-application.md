---
title: 'Wskazówki: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2e544bf49437ce6e3c1e8de1b7c792c63a32700a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679984"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Wskazówki: tworzenie niestandardowego Instalatora dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wskazówki: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](https://docs.microsoft.com/visualstudio/deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application).  
  
Dyskretnie zainstalować żadnych aplikacji ClickOnce, na podstawie pliku .exe i zaktualizowane przez instalatora niestandardowego. Niestandardowego Instalatora można zaimplementować niestandardowy komfortu podczas instalacji, w tym niestandardowych okien dialogowych dla operacji zabezpieczeń i konserwacji. Aby wykonać operacje instalacji, używa niestandardowego Instalatora <xref:System.Deployment.Application.InPlaceHostingManager> klasy. W tym instruktażu pokazano, jak utworzyć niestandardowego instalatora dyskretnej instalacji aplikacji ClickOnce.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Aby utworzyć niestandardowego Instalatora aplikacji ClickOnce  
  
1.  W aplikacji ClickOnce należy dodać odwołania do System.Deployment i pozycję System.Windows.Forms.  
  
2.  Dodaj nową klasę do aplikacji i określić dowolną nazwę. W tym przewodniku używa nazwy `MyInstaller`.  
  
3.  Dodaj następujący kod `Imports` lub `using` instrukcji na górze nowej klasie.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Dodaj następujące metody do klasy.  
  
     Wywoływanie tych metod <xref:System.Deployment.Application.InPlaceHostingManager> metody pobierania pliku manifestu wdrożenia assert odpowiednie uprawnienia, poproś użytkownika o zgodę, aby zainstalować, a następnie należy pobrać i zainstalować ją w pamięci podręcznej funkcji ClickOnce. Określić niestandardowego Instalatora aplikacji ClickOnce jest wstępnie zaufany lub może odroczyć zaufania decyzja o <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> wywołania metody. Ten kod wstępnie ufa aplikacji.  
  
    > [!NOTE]
    >  Uprawnienia przypisane przez wstępnie ufające nie może przekraczać uprawnień kodu niestandardowego Instalatora.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5.  Próby instalacji w kodzie, wywołania `InstallApplication` metody. Na przykład, jeśli nazwę klasy `MyInstaller`, może wywołać `InstallApplication` w następujący sposób.  
  
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
 Aplikacja ClickOnce, można również dodać logikę aktualizacji niestandardowych, łącznie z niestandardowego interfejsu użytkownika wyświetlany podczas procesu aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikacja ClickOnce można również pominąć standardowy wpis menu Start, skrótów i wpisu Dodaj lub usuń programy, za pomocą `<customUX>` elementu. Aby uzyskać więcej informacji, zobacz [ \<Punkt_wejścia > Element](../deployment/entrypoint-element-clickonce-application.md) i <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > Element](../deployment/entrypoint-element-clickonce-application.md)



