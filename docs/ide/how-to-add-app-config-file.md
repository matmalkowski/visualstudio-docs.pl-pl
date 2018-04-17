---
title: Jak dodać pliku app.config do projektu programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 22b9ed31621074e27cfa2d51502e44d508d6b424
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Porady: Dodawanie pliku konfiguracji aplikacji do projektu C#

Przez dodanie pliku konfiguracji aplikacji (*app.config* pliku) do projektu C#, można dostosować sposób środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje pliki zestawu. Aby uzyskać więcej informacji o plikach konfiguracji aplikacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Aplikacji platformy uniwersalnej systemu Windows nie mogą zawierać *app.config* pliku.

Podczas tworzenia projektu środowiska programowania automatycznie kopiuje Twojej *app.config* pliku zmienia nazwę pliku kopii do dopasowania pliku wykonywalnego i przenosi kopię **bin** katalog.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Aby dodać plik konfiguracji aplikacji do projektu C#

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

1. Rozwiń węzeł **zainstalowana** > **Visual C# elementów**, a następnie wybierz pozycję **pliku konfiguracji aplikacji** szablonu.

1. W **nazwa** polu tekstowym wprowadź nazwę, a następnie wybierz **Dodaj** przycisku.

     Plik o nazwie *app.config* zostanie dodany do projektu.

## <a name="see-also"></a>Zobacz także

[Zarządzanie ustawieniami aplikacji (.NET)](../ide/managing-application-settings-dotnet.md)  
[Schemat pliku konfiguracji (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Konfigurowanie aplikacji (.NET Framework)](/dotnet/framework/configure-apps/index)