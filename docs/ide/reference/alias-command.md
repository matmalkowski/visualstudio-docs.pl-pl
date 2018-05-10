---
title: Alias — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41bddec00866f7c10140abc40c5ff12c623310d3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="alias-command"></a>Alias — Polecenie
Tworzy nowy alias pełne polecenie, pełny polecenia i argumentów lub inny alias.

> [!TIP]
> Wpisywanie `>alias` bez żadnych argumentów Wyświetla bieżącą listę aliasów i ich definicje.


## <a name="syntax"></a>Składnia

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
 `aliasname` Opcjonalne. Nazwa nowego aliasu. Jeśli żadna wartość nie jest dostarczony dla `aliasname`, zostanie wyświetlona lista aliasów bieżący oraz ich definicje.

 `aliasstring` Opcjonalne. Nazwa pełne polecenie lub istniejącego aliasu i wszelkie parametry, które ma zostać utworzony jako alias. Jeśli żadna wartość nie jest dostarczony dla `aliasstring`, nazwa aliasu i alias ciąg Wyświetla określony alias.

## <a name="switches"></a>Przełączniki
 / delete/del lub /d opcjonalne. Usuwa określony alias, usuwa ją z autocompletion.

 / reset opcjonalne. Resetuje listę wstępnie zdefiniowane aliasy pierwotne ustawienia. To, że wszystkie wstępnie zdefiniowane aliasy przywraca i usuwa wszystkie aliasy zdefiniowane przez użytkownika.

## <a name="remarks"></a>Uwagi
 Ponieważ aliasy stanowią poleceń, muszą one być znajduje się na początku wiersza polecenia.

 Po wykonaniu tego polecenia, należy uwzględnić przełączników natychmiast po poleceniu, nie po aliasy, w przeciwnym razie tego samego przełącznika dołączane jako część ciąg aliasu.

 `/reset` Przełącznika prosi o potwierdzenie przed aliasy zostaną przywrócone. Brak nie krótkiej formy `/reset`.

## <a name="examples"></a>Przykłady
 W tym przykładzie jest tworzony nowy alias `upper`, aby uzyskać pełną polecenia Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

 W tym przykładzie Usuwa alias, `upper`.

```cmd
>Tools.alias /delete upper
```

 W tym przykładzie wyświetla listę wszystkich bieżącego aliasy i definicje.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)