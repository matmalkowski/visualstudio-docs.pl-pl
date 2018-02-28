---
title: "Jak dodać pliku app.config do projektu programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Porady: Dodawanie pliku konfiguracji aplikacji do projektu C#

Dodanie pliku konfiguracji aplikacji (pliku app.config) do projektu C#, można dostosować sposób środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [jak środowiska uruchomieniowego lokalizuje zestawy (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikacji platformy uniwersalnej systemu Windows nie zawiera pliku app.config.

Podczas tworzenia projektu środowiska programowania automatycznie kopiuje plik app.config, zmienia nazwę pliku kopii do dopasowania pliku wykonywalnego i przenosi Kopiuj do **bin** katalogu.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

1. Rozwiń węzeł **zainstalowana** > **Visual C# elementów**, a następnie wybierz pozycję **pliku konfiguracji aplikacji** szablonu.

3. w **nazwa** polu tekstowym wprowadź nazwę, a następnie wybierz **Dodaj** przycisku.

     A file named app.config is added to your project.

## <a name="see-also"></a>Zobacz także

[Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)  
[Schemat pliku konfiguracji (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)