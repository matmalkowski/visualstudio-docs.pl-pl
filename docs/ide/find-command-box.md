---
title: "Polecenie Znajdź okno | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.findcommandbox
helpviewer_keywords: Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8bf4de0ff0dfb240f668ba3f6915268ee89e594
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="findcommand-box"></a>Find/Command — Pole
Możesz wyszukać tekst i uruchomić polecenia programu Visual Studio z **Find/Command** pole. **Find/Command** pole jest dostępna jako formantu paska narzędzi, ale nie jest już widoczna domyślnie. Można wyświetlić **Find/Command** pola, wybierając **Dodaj lub usuń przyciski** na **standardowe** narzędzi, a następnie wybierając **znaleźć**.  
  
 Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenia, należy poprzedzić go znakiem większości (>).  
  
 **Find/Command** pole zachowuje elementy 20 ostatnio wprowadzone i wyświetla je w listy rozwijanej. Listy można nawigować, wybierając klawiszy strzałek.  
  
 ![Znajdź &#47; Polecenie pole](../ide/media/findcommandbox.png "FindCommandBox")  
Find/Command — Pole  
  
## <a name="searching-for-text"></a>Wyszukiwanie tekstu  
 Domyślnie po określeniu tekstu w **Find/Command** polu i wybierz opcję Wprowadź klucz, Visual Studio wyszukuje bieżące okno dokumentu lub narzędzia, korzystając z opcji, które są określone w **Znajdź w plikach**okno dialogowe. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Wprowadzanie polecenia  
 Aby użyć **Find/Command** pole, aby wystawiać pojedynczy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenie lub alias zamiast wyszukiwania tekstu, wprowadź [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] polecenia poprzedzone symbolem większości (>). Na przykład:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Alternatywnie umożliwia także okno wiersza poleceń do wprowadzania i wykonywanie jednego lub wielu poleceń. Wprowadzona i wykonywane przez siebie; niektóre polecenia ani aliasów inne osoby mają odpowiednie argumenty w ich składni. Aby uzyskać listę poleceń, które mają argumentów, zobacz [Visual Studio — polecenia](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Znaki specjalne  
 Daszek (^) znaku w wierszu polecenia oznacza, że znak natychmiast po jej jest interpretowany jako literału, a nie jako znak kontrolny. Może być używany do osadzania cudzysłowy proste ("), spacji, wiodącego ukośniki, daszka lub innych literał znaków w wartości parametru lub przełącznikiem, z wyjątkiem nazwy przełącznika. Na przykład  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Daszek działa tak samo, czy wewnętrznej lub zewnętrznej znaki cudzysłowu. Jeśli daszek jest ostatni znak w wierszu, zostanie zignorowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno polecenia](../ide/reference/command-window.md)   
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)