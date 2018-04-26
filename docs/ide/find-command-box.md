---
title: Polecenie Znajdź okno
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50c93c2d77f62fe22c682240b879b85af8040974
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="findcommand-box"></a>Find/Command — Pole

Możesz wyszukać tekst i uruchomić polecenia programu Visual Studio z **Find/Command** pole. **Find/Command** pole jest dostępna jako formantu paska narzędzi, ale nie jest już widoczna domyślnie. Można wyświetlić **Find/Command** pola, wybierając **Dodaj lub usuń przyciski** na **standardowe** narzędzi, a następnie wybierając **znaleźć**.

Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenia, należy poprzedzić go z więcej niż (**>**) logowania.

**Find/Command** pole zachowuje elementy 20 ostatnio wprowadzone i wyświetla je w listy rozwijanej. Listy można nawigować, wybierając **klawiszy strzałek**.

![Znajdź&#47;polecenia pole](../ide/media/findcommandbox.png "FindCommandBox")

## <a name="searching-for-text"></a>Wyszukiwanie tekstu

Domyślnie po określeniu tekstu w **Find/Command** polu, a następnie wybierz pozycję **Enter** klucza, Visual Studio wyszukuje bieżące okno dokumentu lub narzędzia, korzystając z opcji, które są określone w **Znajdź w plikach** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Wprowadzanie polecenia

Do używania **Find/Command** pole, aby wystawiać pojedynczy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenie lub alias zamiast wyszukiwania tekstu, należy poprzedzić polecenie z większy niż (**>**) symbolu. Na przykład:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Alternatywnie można również użyć **polecenia** okno, aby wprowadzić i wykonywanie jednego lub wielu poleceń. Wprowadzona i wykonywane przez siebie; niektóre polecenia ani aliasów inne osoby mają odpowiednie argumenty w ich składni. Aby uzyskać listę poleceń, które mają argumentów, zobacz [programu Visual Studio — polecenia](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Znaki specjalne

Daszek (**^**) znaków w poleceniu oznacza, że znak natychmiast po jej jest interpretowany jako literału, a nie jako znak kontrolny. To może służyć do osadzenia cudzysłowy proste (**"**), spacji wiodących ułamkowe, daszka lub innych literał znaków w parametr lub przełącznika wartość, z wyjątkiem nazwy przełącznika. Na przykład:

```
>Edit.Find ^^t /regex
```

Daszek działa tak samo, czy wewnętrznej lub zewnętrznej znaki cudzysłowu. Jeśli daszek jest ostatni znak w wierszu, zostanie zignorowany.

## <a name="see-also"></a>Zobacz także

- [Okno polecenia](../ide/reference/command-window.md)
- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)