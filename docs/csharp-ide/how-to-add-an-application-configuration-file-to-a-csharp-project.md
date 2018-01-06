---
title: 'Porady: Dodawanie pliku konfiguracji aplikacji do projektu C# | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 707100d33e91d1b0920d008140dc2fb6f1e078fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Porady: Dodawanie pliku konfiguracji aplikacji do projektu C#
Dodanie pliku konfiguracji aplikacji (pliku app.config) do projektu C#, można dostosować sposób środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  Aplikacji platformy uniwersalnej systemu Windows nie ma szablonu pliku app.config.
  
 Podczas kompilowania projektu środowisko projektowe automatycznie kopiuje plik app.config, zmienia nazwę pliku kopii do dopasowania pliku wykonywalnego i przenosi ją w katalogu bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
2.  Rozwiń węzeł **zainstalowana**, rozwiń węzeł **Visual C# elementów**, a następnie wybierz pozycję **pliku konfiguracji aplikacji** szablonu.  
  
3.  W **nazwa** polu tekstowym wprowadź nazwę, a następnie wybierz **Dodaj** przycisku.  
  
     Plik o nazwie app.config jest dodany do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schemat pliku konfiguracji](/dotnet/framework/configure-apps/file-schema/index)   
 [Konfigurowanie aplikacji](/dotnet/framework/configure-apps/index)   
 [Porady: Konfigurowanie aplikacji pod kątem wersji programu .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Używanie środowiska programistycznego Visual Studio dla C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)