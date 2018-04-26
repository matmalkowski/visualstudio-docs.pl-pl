---
title: — Identyfikator LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c67b1b7d581a7e4b9d4309bfe432bf2a3298e4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Określa domyślny język używany do tekstu, waluty i inne wartości w ramach zintegrowane środowisko programistyczne (IDE).

## <a name="syntax"></a>Składnia

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argumenty
 `LocaleID` Wymagane. Identyfikator LCID (identyfikator ustawień regionalnych) wybranego języka.

## <a name="remarks"></a>Uwagi
 Ładuje IDE i ustawia domyślne języka naturalnego dla środowiska. Ta zmiana jest zachowywane między sesjami i odzwierciedlone na **ustawienia międzynarodowe** okienku **środowiska** opcje w **opcje** okno dialogowe w IDE.

 Jeśli określony język nie jest dostępna w systemie użytkownika, przełącznik/LCID jest ignorowany.

 W poniższej tabeli wymieniono LCID języków obsługiwanych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Język|LCID|
|--------------|----------|
|Chiński uproszczony|2052|
|Chiński (tradycyjny)|1028|
|Angielski|1033|
|Francuski|1036|
|niemiecki|1031|
|Włoski|1040|
|japoński|1041|
|koreański|1042|
|Hiszpański|3082|

## <a name="example"></a>Przykład
 W tym przykładzie ładuje IDE z ciągów zasobów w języku angielskim.

```
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Ustawienia międzynarodowe, środowisko, opcje — Okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)