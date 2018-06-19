---
title: 'Porady: Korzystanie z wizualizatora drzewa WPF | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 290231b7b700a26945227ba04ddc2e97cdfe4299
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475470"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Porady: korzystanie z wizualizatora drzewa WPF
Można użyć z wizualizatora drzewa WPF, aby zapoznać się z drzewa wizualnego obiektu WPF i aby wyświetlić właściwości zależności WPF dla obiektów, które są zawarte w tym drzewie. Aby uzyskać więcej informacji na temat drzewa wizualnego, zobacz [drzewa WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Po otwarciu wizualizatora drzewa WPF zostanie wyświetlone dwa okienka: **drzewa wizualnego** po lewej stronie i **właściwości** *nazwa ***:*** typu* okienko po prawej stronie. Zaznacz dowolny obiekt w **drzewa wizualnego** okienku i **właściwości** *nazwa ***:*** typu* okienko zostanie automatycznie zaktualizowana do wyświetlenia właściwości tego obiektu.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Aby otworzyć z wizualizatora drzewa WPF  
  
1.  W etykietek danych **czujki** okna, **automatycznych** okna, lub **zmiennych lokalnych** okna obok nazwy obiektów WPF kliknij strzałkę obok ikonę lupy.  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2.  Kliknij przycisk **wizualizatora drzewa WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Aby przeszukać drzewo wizualne  
  
-   W **drzewa wizualnego** okienku, wpisz ciąg chcesz wyszukać w **wyszukiwania** pole.  
  
     Z wizualizatora drzewa WPF natychmiast znajduje pierwszy obiekt w drzewie wizualnym pasującej do ciągu wpisany. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.  
  
    -   Aby przejść do następnego dopasowania w obrębie drzewa wizualnego, kliknij przycisk **dalej**.  
  
    -   Aby powrócić do poprzedniego dopasowania, kliknij przycisk **Prev**.  
  
    -   Aby usunąć kryteria wyszukiwania, kliknij przycisk **wyczyść**.  
  
### <a name="to-search-the-properties-list"></a>Do listy właściwości wyszukiwania  
  
-   W **właściwości** *nazwa ***:*** typu* okienku, wpisz ciąg chcesz wyszukać w **filtru** pole.  
  
     Z wizualizatora drzewa WPF natychmiast wyszukuje właściwości, które zgodny z ciągiem, który został wpisany; teraz na liście zostaną wyświetlone tylko właściwości dopasowywania ciągu wpisany. Wpisz więcej znaków, aby znaleźć bardziej dokładne dopasowanie.  
  
    -   Aby usunąć kryteria wyszukiwania, kliknij przycisk **wyczyść**.  
  
### <a name="to-close-the-visualizer"></a>Aby zamknąć wizualizatora  
  
-   Kliknij przycisk **Zamknij** ikonę w prawym górnym rogu okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Utwórz niestandardowe Wizualizatory](../debugger/create-custom-visualizers-of-data.md)   
 [Drzewa na platformie WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Przegląd właściwości zależności](/dotnet/framework/wpf/advanced/dependency-properties-overview)