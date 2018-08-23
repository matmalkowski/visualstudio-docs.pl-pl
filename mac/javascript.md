---
title: JavaScript
description: Informacje na temat obsługi języka JavaScript w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 21ff2211632cba63dafe2a7abf1964e7a89e87c3
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42624360"
---
# <a name="javascript-support"></a>Obsługa języka JavaScript

Program Visual Studio for Mac zapewnia obsługę dla języków Javascript i Typescript za pośrednictwem wyróżniania składni, formatowanie kodu i technologii IntelliSense. 

![Pomoc techniczna do edytora języka typescript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Aby uzyskać więcej informacji na temat pisania kodu JavaScript, zobacz Aby [pisanie kodu Javascript](https://docs.microsoft.com/scripting/javascript/writing-javascript-code) przewodników.

## <a name="adding-a-javascript-file"></a>Dodawanie pliku JavaScript

Pliki JavaScript w większości przypadków są dodawane do projektów ASP.NET Core za pomocą **nowy plik** okna dialogowego. Aby dodać plik języka javascript, kliknij prawym przyciskiem myszy nad projektem i przejdź do **Dodaj > Nowy plik**: 

![dodanie nowych plików do projektu](media/javascript-image1.png)

W oknie dialogowym Nowy plik, wybierz **Web > plik JS pusty** lub **sieci Web > plik Typescript**. Nadaj jej nazwę, a następnie wybierz **New**:

![utworzenie nowego pliku typescript na podstawie szablonu](media/javascript-image2.png)

## <a name="intellisense"></a>funkcja IntelliSense

Program Visual Studio for Mac używa [usługę językową Javascript](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense) dostarczyć Intellisense, co pozwala mieć inteligentnego uzupełniania kodu, informacje o parametrach i listy elementów członkowskich, podczas pisania kodu.

Funkcja intellisense języka JavaScript w programie Visual Studio dla komputerów Mac może bazować na wnioskowanie o typie, JSDoc lub Typescript deklaracji.

- **Wnioskowanie o typie** — typ obiektu jest wybierana przez otaczającego kontekst kodu. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [IntelliSense oparte na wnioskowanie o typie](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **Element JSDoc** — istnieją momenty, gdy wnioskowanie o typie nie udostępnia informacji poprawnego typu. W takich przypadkach informacje o typie można podać jawnie przez [JSDoc](http://usejsdoc.org/about-getting-started.html) adnotacji. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [Intellisense oparte na danych JSDoc](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Pliki deklaracji TypeScript** — `.d.ts` pliki są używane do przekazania wartości do Javascript Intellisense. Typy zadeklarowane w tym pliku może służyć jako typy na komentarzy JSDoc. Aby uzyskać więcej informacji, zobacz sekcję programu Visual Studio na [funkcji IntelliSense na podstawie TypeScript deklaracji plików](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) ![dodanie plików definicji typescript](media/javascript-image3.png)