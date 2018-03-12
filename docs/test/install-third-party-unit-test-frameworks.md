---
title: "Instalowanie platform testów jednostkowych innych firm | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c0cd7853c65d5501213076cb7ccb533c5134c9f4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="install-third-party-unit-test-frameworks"></a>Instalowanie platform testów jednostkowych innych firm
Visual Studio Test Explorer można uruchomić wszystkie jednostki struktury testowej, która opracowała karta Interfejs Eksploratora. Program instalacyjny platformy instalację plików binarnych i dodaje szablony projektu Visual Studio dla obsługiwanych języków. Podczas tworzenia projektu z szablonem narzędzia Eksplorator testów jest zarejestrowany platformę. Rozwiązanie programu Visual Studio może zawierać projektów testów jednostkowych używający różnych platform i które są przeznaczone dla różnych języków. Eksplorator testów uruchamia je wszystkie.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise, Visual Studio Professional  
  
## <a name="acquiring-third-party-frameworks"></a>Uzyskiwanie struktur innych firm  
 Można pobrać i zainstalować wiele platform testów jednostkowych innych firm, za pomocą Menedżera rozszerzenia programu Visual Studio lub Visual Studio Marketplace. Można również pobrać struktur w innych witrynach, takich jak witryny sieci Web platformy.  
  
### <a name="installing-from-visual-studio"></a>Instalowanie w programie Visual Studio  
  
1.  Wybierz **narzędzia** standardowe menu, a następnie wybierz pozycję **rozszerzenia i aktualizacje**.  
  
2.  Rozwiń węzeł **Online**, **programu Visual Studio Marketplace**, **narzędzia**. Wybierz **testowania**.  
  
3.  Przeszukaj listę, aby znaleźć platformę.  
  
4.  Wybierz platformę, a **Pobierz**.  
  
 Aby uzyskać więcej informacji, zobacz [Znajdowanie i rozszerzenia przy użyciu programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
### <a name="installing-from-the-web"></a>Instalowanie z sieci web  
 Jeśli znasz platformę myślisz:  
  
1.  Otwórz [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).  
  
2.  Wpisz nazwę w ramach **znaleźć** pole.  
  
3.  Wybierz platformę na liście wyników, aby przejść do strony programu Visual Studio Marketplace narzędzia.  
  
 Aby przeglądać listę struktury oraz inne narzędzia do testowania:  
  
1.  Otwórz [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).  
  
2.  W **Filtruj według kategorii / kolekcji**, wybierz **zobaczyć wszystkie**.  
  
3.  W **kategorii** listy (oznaczone jako **przedstawiający**), rozwiń węzeł **narzędzia** węzeł, a następnie wybierz **testowanie**.  
  
4.  Wybieranie platformy na liście wyników, aby przejść do strony narzędzia Visual Studio Marketplace. 

## <a name="update-to-the-latest-test-adapters"></a>Aktualizowanie do najnowszej adapterów testowych

Aktualizację do najnowszej adapter testowy stabilna występować lepsze testowania odnajdywania i wykonywania. Aby uzyskać więcej informacji o aktualizacjach MSTest NUnit i xUnit adapterów testowych, zobacz [blogu Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aby zaktualizować test najnowsza stabilna wersja karty

1. Otwórz Menedżera pakietów Nuget dla rozwiązania, przechodząc do **Narzędzia > Menedżera pakietów NuGet > Zarządzaj pakietami NuGet rozwiązania...**

2. Polecenie **aktualizacje** kartę i wyszukać NUnit lub xUnit test kart, które są zainstalowane.

3. Wybierz kartę każdego testu, a następnie wybierz najnowsza stabilna wersja w menu rozwijanego.

4. Wybierz **zainstalować** przycisku.

![Adapter testowy uaktualnienia](media/installadapter-upgrade.png)

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
