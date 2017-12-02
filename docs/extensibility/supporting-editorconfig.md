---
title: "Rozszerzenie usługi języka aby obsługiwać EditorConfig w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111e53ad9beec3a5f5ef013b996a541ea0fa1e72
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2017
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Obsługa EditorConfig usługi języka

[EditorConfig](http://editorconfig.org/) pliki umożliwiają opisano typowe opcje edytora tekstu, na przykład rozmiar wcięcie na podstawie na projekt. Aby dowiedzieć się więcej na temat obsługi programu Visual Studio dla plików EditorConfig, zobacz [utworzyć ustawienia edytora przenośnych za pomocą EditorConfig](../ide/create-portable-custom-editor-options.md).

W większości przypadków podczas implementowania usługi języka Visual Studio, żadne dodatkowe czynności jest wymagane do obsługi EditorConfig uniwersalnych właściwości. Edytor core automatycznie wykrywa i odczytuje plik .editorconfig po otwarciu plików i ustawia opcje buforu i widoku odpowiedni tekst. Jednak do edycji, takie jak znaki tabulacji i spacje, niektóre usługi języka zdecydować się na użycie odpowiedni tekst kontekstowe opcji widoku, a nie za pomocą ustawień globalnych. W takich przypadkach usługi języka muszą zostać zaktualizowane do obsługi plików EditorConfig.

Poniżej przedstawiono zmiany, które są niezbędne do aktualizowania usługi języka do obsługi plików EditorConfig, zastępując globalnym _specyficzny dla języka_ opcję z _kontekstowe_ opcji:

## <a name="indent-style"></a>Styl wcięcie

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|! textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>! textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Wcięcie

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Rozmiar tabulatora

Opcje specyficzne dla języka | Opcje kontekstowe
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Zobacz także

[Tworzenie ustawień edytora przenośnych za pomocą EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Rozszerzenie usług edytora i język](../extensibility/extending-the-editor-and-language-services.md)