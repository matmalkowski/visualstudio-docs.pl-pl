---
title: "Visual Studio Tools for Unity modelu danych Azure wskazówki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: e3b6064a3947f57ffcbe6422162c6c72fca0ab21
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="create-data-model-classes"></a>Tworzenie klasy modelu danych

Projekt Unity musi zawierać klasy modelu danych, które odpowiadają tabele utworzone w zaplecza aplikacji mobilnej Azure.

## <a name="create-the-crashinfo-class"></a>Utwórz klasę CrashInfo

1. W Unity, Dodaj nowy folder w katalogu głównym **zasoby** katalog o nazwie **skryptów**. Wewnątrz nowy folder skryptów, należy utworzyć inny nowy folder o nazwie **modeli danych**. Jest to tylko organizacji.

2. W nowym folderze modeli danych, Utwórz nowy skrypt języka C# o nazwie **CrashInfo**.

3. Otwórz nową `CrashInfo` skryptów, usunięcie wszelkiego kodu szablonu, włącznie z deklaracją klasy przy użyciu instrukcji i Dodaj następujący kod:

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Przewodnik działał prawidłowo Nazwa klasy modelu danych musi odpowiadać nazwie tabeli łatwo utworzyć dla zaplecza aplikacji mobilnej Azure.

## <a name="create-the-highscoreinfo-class"></a>Utwórz klasę HighScoreInfo

1. Znajdujące się w folderze modeli danych, Utwórz nowy skrypt języka C# o nazwie **HighScoreInfo**.

2. Otwórz nową `HighScoreInfo` skryptów, usunięcie wszelkiego kodu szablonu, włącznie z deklaracją klasy przy użyciu instrukcji i Dodaj następujący kod:

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Następny krok

  * [Implementowanie Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
