---
title: 'Porady: Dodawanie pliku konfiguracji aplikacji do projektu C# | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 29386381679c02d3f4c7772e79f1da4a64705e3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682573"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Porady: Dodawanie pliku konfiguracji aplikacji do projektu C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przez dodawanie pliku konfiguracji aplikacji (plik app.config) do projektu C#, można dostosować, jak środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  Nie obsługuje Store Windows <xref:System.Configuration>. Z tego powodu Store apps nie zawierają szablonu pliku app.config.  
  
 Podczas tworzenia projektu środowiska programistycznego automatycznie kopiuje plik app.config, zmienia nazwę pliku kopiowania, aby dopasować plik wykonywalny i przenosi kopii w katalogu bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** pojawi się okno dialogowe.  
  
2.  Rozwiń **zainstalowane**, rozwiń węzeł **elementy Visual C#**, a następnie wybierz **pliku konfiguracji aplikacji** szablonu.  
  
3.  W **nazwa** polu tekstowym wprowadź nazwę, a następnie wybierz **Dodaj** przycisku.  
  
     Plik, który nosi nazwę pliku app.config zostanie dodany do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schemat pliku konfiguracji](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Konfigurowanie aplikacji](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Porady: Konfigurowanie aplikacji pod kątem określonej wersji oprogramowania .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Używanie środowiska programistycznego Visual Studio dla C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)