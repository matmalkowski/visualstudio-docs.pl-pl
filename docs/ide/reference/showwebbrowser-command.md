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
ms.openlocfilehash: 018d94f2952b8169890377410ff00baf1a80fd41
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176388"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser — Polecenie

Wyświetla adres URL w oknie przeglądarki sieci web w ramach zintegrowanego środowiska programistycznego (IDE) lub zewnętrznego dla IDE.

## <a name="syntax"></a>Składnia

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
 `URL`

 Wymagane. Adres URL (Uniform Resource Locator) dla witryny sieci Web.

## <a name="switches"></a>Przełączniki
 / Nowy

 Opcjonalna. Określa, czy strona jest wyświetlana w nowym wystąpieniu przeglądarki sieci web.

 /ext

 Opcjonalna. Określa, czy strona jest wyświetlana w domyślnej przeglądarce sieci web poza IDE.

## <a name="remarks"></a>Uwagi
 Alias **showwebbrowser —** polecenie jest **Przejdź** lub **nav**.

## <a name="example"></a>Przykład
 Poniższy przykład wyświetla MSDN Online strony głównej w przeglądarce sieci web poza IDE. Jeśli wystąpienie przeglądarki sieci web jest już otwarty, jest używany; w przeciwnym razie jest uruchamiana nowe wystąpienie.

```cmd
>View.ShowWebBrowser http://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Znajdź/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)