---
title: 'Porady: tłumienie ostrzeżeń przy użyciu elementu Menu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: be62471a950dc794bc3b9ff704cb187bbc943ce1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630709"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Porady: tłumienie ostrzeżeń przy użyciu elementu menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: pomijanie ostrzeżeń przy użyciu elementu Menu](https://docs.microsoft.com/visualstudio/code-quality/how-to-suppress-warnings-by-using-the-menu-item).  
  
UWAGA]
>  W źródle pomijanie nie jest obsługiwana dla projektów witryny sieci web.  
  
 Okno analizy kodu na pomijanie ostrzeżeń analizy kodu. Pomijanie ostrzeżenie nie jest taka sama jak wyłączenie go. Gdy możesz pominąć ostrzeżenia, ma zastosowanie tylko do konkretnego wystąpienia naruszenia. Inne naruszenia tego samego ostrzeżenia nadal będą raportowane w oknie Lista błędów.  
  
 Po uruchomieniu analizy kodu, można określić, że jeden lub więcej ostrzeżeń analizy kodu, które są wyświetlane w oknie analizy kodu nie mają zastosowania do aplikacji. Na przykład można określić, czy kod jest poprawna, ponieważ jest. Lub może być tak, że niektóre naruszeń są — niski priorytet, a nie zostanie rozwiązany w bieżącym cyklu tworzenia oprogramowania. Niezależnie od przyczyny jest często przydatny wskazać, że ostrzeżenie nie ma zastosowania aby umożliwić członkom zespołu, wiadomo, że kod został zrecenzowany i ustalenie, czy można pominąć to ostrzeżenie. W źródle pomijania jest przydatne, ponieważ dzięki temu można umieścić pomijanie blisko której generowane jest ostrzeżenie.  
  
 Możesz wybrać, czy pomijanie pojawi się w kodzie źródłowym lub w pliku pominięć globalnych. Niektóre pominięcia muszą być umieszczone w pliku pominięć globalnych. Jeśli tak, jest **w źródłowej** opcja zostanie wyłączona.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Aby pominąć ostrzeżenie przy użyciu elementu menu  
  
1.  Na **analizy** menu, wybierz **Windows** , a następnie wybierz **analizy kodu**.  
  
2.  W **analizy kodu** okna, wybierz opcję Pomiń ostrzeżenia.  
  
3.  Wybierz akcje, a następnie wybierz **Pomijaj komunikaty**, a następnie wybierz **w źródłowej** lub **w pliku pominięć projektu**.  
  
     Pomijane jest szczególne ostrzeżenie i ostrzeżenie jest wyświetlane w oknie analizy kodu za pomocą przekreślenia.  
  
> [!NOTE]
>  Ograniczeń, które nie mają na celu pojawiają się w pliku pominięć globalnych.



