---
title: Opcje, edytor tekstu, C/C++, formatowanie
ms.date: 04/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ee7fab1564b39b29ae288e96c7aa77e0da21e88c
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235144"
---
# <a name="options-text-editor-cc-formatting"></a>Opcje, edytor tekstu, C/C++, formatowanie

Te strony właściwości umożliwia zmianę domyślnego zachowania edytora kodu są programowania C lub C++.

[C++, formatowanie strony właściwości](media/cpp-formatting.png)

 Dostępu do tej strony, w **opcje** okno dialogowe, w lewym okienku rozwiń **Edytor tekstu**, rozwiń węzeł **C/C++**, a następnie kliknij przycisk **formatowanie** .

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Strona Ogólne

Ta strona zawiera opcje formatowania instrukcje i bloków w trakcie pisania.

**Visual Studio 2017 wersji 15.7 i nowszych**: strona zawiera również opcje dotyczące konfigurowania obsługi [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) w wersji 5.0. ClangFormat to narzędzie, które ułatwia stylu i formatowania kodu na podstawie zestawu reguł, które można skonfigurować w pliku formatu .clang lub _clang format.

### <a name="configuring-clangformat-options"></a>Konfigurowanie opcji ClangFormat

W Visual Studio 2017 wersji 15.7 i nowszych ClangFormat obsługa jest domyślnie włączona. Można określić, które z tych typowych konwersji formatowanie, aby zastosować do wszystkich projektów: LLVM, Google, chromu, Mozilla lub WebKit. Można także utworzyć plik formatu .clang lub _clang — Definicja formatu niestandardowego. Jeśli taki plik znajduje się w folderze projektu, Visual Studio używa jej do formatowania wszystkich plików kodu źródłowego w tym folderze i jego podfolderach. 

Domyślnie program Visual Studio clangformat.exe działa w tle stosuje formatowanie podczas pisania. Można również określić go tylko w przypadku ręcznie uruchomić wywołać polecenia formatowania **dokumentu w formacie (Ctrl + K, Ctrl + D)** lub **Wybieranie formatu (Ctrl + K, Ctrl + F)**.


## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Wcięcie, nowe wiersze, odstępy zawijania stron

Te strony włączyć różne dostosowania formatowania, ale są ignorowane, jeśli ClangFormat jest włączone.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)