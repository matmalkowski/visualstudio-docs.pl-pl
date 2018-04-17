---
title: Dostosowywanie Eksploratora modelu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c69cdd822941fd81478fae0b62d509b64ef513da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-the-model-explorer"></a>Dostosowywanie Eksploratora modelu
Można zmienić wygląd i zachowanie Eksploratora dla z projektantem języka specyficznego dla domeny w następujący sposób:  
  
-   Zmień tytuł okna.  
  
-   Zmień ikonę tabulatora.  
  
-   Zmienić ikony dla węzłów.  
  
-   Ukryj węzłów.  
  
## <a name="changing-the-window-title"></a>Zmiana tytuł okna  
 Zmienić tytuł okna Eksploratora wygenerowanego, wybierz **zachowanie Explorer** w **DSL Explorer**, a następnie w **właściwości** ustaw  **Tytuł** tytuł chcesz dla właściwości.  
  
## <a name="changing-the-tab-icon"></a>Zmiana ikony kartę  
 Aby zmienić ikony kartę Eksploratora, użyj ikony 16 x 16 pikseli w pliku bmp. Umieść plik ikony w folderze \DslPackage\Resources\, a następnie zmień nazwę pliku, aby **ModelExplorerToolWindowBitmaps.bmp**. Na przykład można zmienić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico ikonę pliku w formacie BMP i zmienić jego nazwę na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Projektant wygenerowanego wyświetli tej ikony na karcie z Eksploratora zadokowany razem z **Eksploratora rozwiązań**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Ustawienie ikon niestandardowych w węzłach Explorer  
 Węzły w Eksploratorze programu można dostosować przy użyciu Eksploratora węzła ustawień. Poniższa procedura pokazuje, jak dodać ikony do węzła.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Aby dodać ikony do węzła explorer  
  
1.  Utwórz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązania przy użyciu szablonu rozwiązania przepływ zadań.  
  
2.  Umieść plik bmp, który zawiera ikona 16 x 16 pikseli, w **Dsl\Resources** folder w rozwiązaniu.  
  
3.  W **DSL Explorer**, kliknij prawym przyciskiem myszy **Explorer zachowanie** , a następnie kliknij przycisk **Dodaj nowe ustawienia węzła Explorer**.  
  
     **ExplorerNodeSettings** węzeł jest wyświetlany w obszarze **niestandardowych ustawień węzła** węzła.  
  
4.  Wybierz **ExplorerNodeSettings**, a następnie w **właściwości** ustaw **klasy** do **aktora**.  
  
5.  Ustaw **ikonę do wyświetlenia** do ścieżki pliku ikony.  
  
6.  Przekształć wszystkie szablony, a następnie skompilować i uruchomić rozwiązanie.  
  
7.  W Projektancie wygenerowanego Otwórz przykładowy diagram.  
  
     Eksplorator powinny być widoczne trzy **aktora** węzły, które mają jako ikony.  
  
> [!NOTE]
>  Jeśli ustawisz ikoną węzła elementów, które jest wyświetlana w Eksploratorze wygenerowanego, wszystkie węzły w Eksploratorze będzie wyświetlana ikona. Jeśli nie ustawiono bez ikony, węzły będzie wyświetlana ikona domyślna.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Zmiana nazwy wyświetlane w węźle Explorer  
 Można zmienić sposób wyświetlania nazw elementów modelu w Eksploratorze użytkownika. Poniższa procedura przedstawia sposób wyświetlania nazwę **zadań** , do którego odwołuje **komentarz** w węźle komentarza.  
  
#### <a name="to-display-a-property"></a>Aby wyświetlić właściwości  
  
1.  Otwórz rozwiązanie utworzonego w procedurze wcześniej.  
  
2.  Upewnij się, że **komentarz** odwołuje się tylko do klasy pojedynczej domeny przez ustawienie Liczebność roli o nazwie właściwości **tematy** do od 0 do 1. Nazwa właściwości powinny stać się **podmiotu**, i powinien być nazwa relacji **CommentReferencesSubject**.  
  
3.  W **DSL Explorer**, kliknij prawym przyciskiem myszy **Explorer zachowanie** , a następnie kliknij przycisk **Dodaj nowe ustawienia węzła Explorer**.  
  
     **ExplorerNodeSettings** węzeł jest wyświetlany w obszarze **niestandardowych ustawień węzła** węzła.  
  
4.  Wybierz **ExplorerNodeSettings**, a następnie w **właściwości** ustaw **klasy** do **komentarz**.  
  
5.  Kliknij prawym przyciskiem myszy **komentarz** węzeł, a następnie kliknij przycisk **dodać nową ścieżkę właściwości**.  
  
     Pojawi się nowy węzeł o nazwie **wyświetlane właściwości**.  
  
6.  Wybierz **wyświetlane właściwości**, a następnie w **właściwości** okna, kliknij pole wartości **właściwość Path**. Wybierz **komentarz**, następnie **CommentReferencesSubject**, następnie **FlowElement**. Ścieżka powinna wyglądać **CommentReferencesSubject.Subject/! Temat**.  
  
7.  W polu wartość **właściwości**, wybierz pozycję **nazwa**.  
  
8.  Przekształć wszystkie szablony, a następnie skompilować i uruchomić rozwiązania.  
  
9. W Projektancie wygenerowanego Otwórz przykładowy diagram.  
  
10. Rysuj **łącznika komentarz** między element komentarz i **Task1** elementu na diagramie.  
  
     Węzeł Explorer powinien być wyświetlany jako komentarz **Task1**.  
  
## <a name="hiding-nodes"></a>Ukrywanie węzłów  
 Węzeł w Eksploratorze sieci można ukryć przez dodanie ścieżki do **ukryte węzły** węzła **DSL Explorer**. Poniższa procedura pokazuje, jak ukryć **komentarz** węzłów.  
  
#### <a name="to-hide-an-explorer-node"></a>Aby ukryć węzeł explorer  
  
1.  Otwórz rozwiązanie utworzonego w procedurze wcześniej.  
  
2.  W **DSL Explorer**, kliknij prawym przyciskiem myszy **Explorer zachowanie** , a następnie kliknij przycisk **dodać nową ścieżkę domeny**.  
  
     A **ścieżka domeny** węzeł jest wyświetlany w obszarze **ukryte węzły**.  
  
3.  Wybierz **ścieżka domeny**, a następnie w **właściwości** okna, kliknij pole wartości **definicji ścieżki**. Wybierz **FlowGraph**, następnie **FlowGraphHasComments**. Ścieżka powinna wyglądać **FlowGraphHasComments.Comments**  
  
4.  Przekształć wszystkie szablony, a następnie skompilować i uruchomić rozwiązania.  
  
5.  W Projektancie wygenerowanego Otwórz przykładowy diagram.  
  
     Eksplorator powinny być widoczne tylko **podmiotów** węzeł i nie powinny być widoczne **komentarze** węzła.  
  
## <a name="see-also"></a>Zobacz także

[Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)