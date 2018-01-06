---
title: "Visual Studio Tools for Unity Azure wskazówki Instalatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: ba9de2e6af5c066e83b75576f9b104f20908aec6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="create-easy-tables"></a>Tworzenie tabel łatwe

Teraz, gdy masz aplikacji mobilnej na platformie Azure z tabelami łatwe zainicjować nadszedł czas na tworzenie tabel, które będą przechowywać informacje o danych wysyłanych z gier środowiska Unity.

## <a name="setup-the-crash-heatmap-table"></a>Instalator tabeli heatmap awarii

1. W portalu Azure kliknij opcję Wszystkie zasoby, a następnie wybierz aplikację mobilną, skonfigurowanego dla tabel łatwy w poprzednich krokach.

  ![Wybierz aplikację mobilną](media/vstu_azure-setup-table-schema-image1.png)

2. Przewiń w dół do **MOBILE** nagłówek i wybierz **łatwe tabel**. Nie powinna być wszelkie zawiadomienia o Inicjowanie aplikacji w przypadku tabel łatwe.  

  ![Wybierz tabele łatwe](media/vstu_azure-setup-table-schema-image2.png)

3. Kliknij przycisk **Dodaj** przycisku.

  ![Kliknij przycisk Dodaj](media/vstu_azure-setup-table-schema-image3.png)

4. Nazwa tabeli "**CrashInfo**" i kliknij przycisk **OK**. Pozostaw pozostałe opcje z ustawień domyślnych.

  > [!WARNING]
  > Ta nazwa musi odpowiadać nazwie klasy modelu danych utworzone później w tym przewodnikiem.

  ![Nazwy i kliknij przycisk OK](media/vstu_azure-setup-table-schema-image4.png)

5. Powiadomienie będzie ogłaszamy po utworzeniu nowej tabeli.

> [!NOTE]
> Łatwe tabel schemat tabeli faktycznie dynamicznie jest tworzony w miarę dodawania danych. Oznacza to, że odpowiednie dane kolumny nie mają być ręcznie skonfigurowane w tym kroku.

## <a name="setup-the-leaderboard-table"></a>Instalator tabeli Liderzy

1. Wróć do bloku łatwe tabel, a następnie kliknij przycisk **Dodaj** do dodania drugiej tabeli.

  ![Dodaj drugą tabelę](media/vstu_azure-setup-table-schema-image10.png)

2. Nazwa nowej tabeli "**HighScoreInfo**" i kliknij przycisk **OK**. Pozostaw pozostałe opcje ustawień domyślnych.

  > [!WARNING]
  > Ta nazwa musi odpowiadać nazwie klasy modelu danych utworzone później w tym przewodnikiem.

  ![Nazwy i kliknij przycisk OK](media/vstu_azure-setup-table-schema-image11.png)

3. Powiadomienie będzie ogłaszamy po utworzeniu nowej tabeli.


## <a name="next-step"></a>Następny krok

* [Przygotowanie środowiska programistycznego](visual-studio-tools-for-unity-azure-prepare.md)
