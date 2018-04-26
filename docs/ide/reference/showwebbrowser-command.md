---
title: ShowWebBrowser — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1396cd28244a655d18f6e09f4795dd099a11ca7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie
Wyświetla adres URL, określ w oknie przeglądarki sieci Web albo w ramach zintegrowane środowisko programistyczne (IDE) lub zewnętrzne względem programu IDE.

## <a name="syntax"></a>Składnia

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
 `URL`

 Wymagana. Adres URL (Uniform Resource Locator) dla witryny sieci Web.

## <a name="switches"></a>Przełączniki
 / new

 Opcjonalna. Określa, czy strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci Web.

 /ext

 Opcjonalna. Określa, czy strona jest wyświetlana w domyślnej przeglądarce sieci Web poza IDE.

## <a name="remarks"></a>Uwagi
 Alias **showwebbrowser —** polecenie jest **Przejdź** lub **nav**.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono MSDN Online strony głównej w przeglądarce sieci Web poza IDE. Jeśli wystąpienie przeglądarki sieci Web jest już otwarty, jest używany; w przeciwnym razie uruchamiane jest nowe wystąpienie.

```
>View.ShowWebBrowser http://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)