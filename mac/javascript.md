---
title: JavaScript
description: Informacje o obsługę języka Javascript w programie Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: b24591053162603ed3089c0868d215a101688f7e
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="javascript-support"></a>Obsługa języka JavaScript

Visual Studio for Mac zapewnia obsługę języka Javascript i Typescript za pośrednictwem wyróżnianie składni, kod formatowanie i IntelliSense. 

![Obsługa edytora typescript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Aby uzyskać więcej informacji na temat pisania kodu JavaScript, zobacz Aby [pisanie kodu Javascript](https://docs.microsoft.com/scripting/javascript/writing-javascript-code) przewodników.

## <a name="adding-a-javascript-file"></a>Dodawanie pliku JavaScript

Pliki JavaScript najczęściej są dodawane do projektów platformy ASP.NET Core za pomocą **nowy plik** okna dialogowego. Aby dodać plik javascript, kliknij prawym przyciskiem myszy projekt i przejdź do **Dodaj > Nowy plik**: 

![Dodawanie nowych plików do projektu](media/javascript-image1.png)

W oknie dialogowym Nowy plik, wybierz **sieci Web > JS pusty plik** lub **sieci Web > plików Typescript**. Nadaj mu nazwę, a następnie wybierz pozycję **nowy**:

![Tworzenie nowego pliku typescript z szablonu](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Programu Visual Studio for Mac używa [usługa języka Javascript](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense) zapewnienie Intellisense, umożliwiając ma uzupełniania kodu inteligentnego, informacje o parametrach i listach elementów członkowskich podczas pisania kodu.

Intellisense dla JavaScript w programie Visual Studio for Mac może bazować na wnioskowanie o typie, JSDoc lub Typescript deklaracji.

- **Wnioskowanie o typie** — typu obiektu jest znalezienia w otaczającym kontekście kodu. Aby uzyskać więcej informacji, zobacz sekcję Visual Studio na [IntelliSense oparte na wnioskowanie o typie](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** — istnieją momenty, gdy wnioskowanie o typie nie udostępnia informacji poprawnego typu. W takich przypadkach informacji o typie można podać jawnie przez [JSDoc](http://usejsdoc.org/about-getting-started.html) adnotacji. Aby uzyskać więcej informacji, zobacz sekcję Visual Studio na [Intellisense oparte na JSDoc](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Pliki deklaracji typeScript** — `.d.ts` o podanie wartości Intellisense dla Javascript używane są pliki. Typy zadeklarowane w tym pliku może służyć jako typy komentarzy JSDoc. Aby uzyskać więcej informacji, zobacz sekcję Visual Studio na [IntelliSense oparte na plikach deklaracji TypeScript](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) ![Dodawanie plików definicji typescript](media/javascript-image3.png)