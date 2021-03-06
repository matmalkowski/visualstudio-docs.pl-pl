---
title: Dostosowywanie Eksploratora modelu
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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1455c0e1d4d5ff0aae952294ef3ee127a0d325a3
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859903"
---
# <a name="customizing-the-model-explorer"></a>Dostosowywanie Eksploratora modelu
Możesz zmienić wygląd i zachowanie Eksploratora dla projektanta języka specyficznego dla domeny w następujący sposób:

-   Zmienianie tytułu okna.

-   Zmień ikonę na karcie.

-   Zmiana ikony dla węzłów.

-   Aby ukryć węzły.

## <a name="changing-the-window-title"></a>Zmienianie tytułu okna
 Aby zmienić tytuł okna Eksploratora wygenerowane, wybierz **zachowanie Eksploratora** w **Eksplorator DSL**, a następnie w polu **właściwości** oknie  **Tytuł** właściwości tytułu ma.

## <a name="changing-the-tab-icon"></a>Zmiana ikony karty
 Aby zmienić ikony kartę dla Eksploratora, użyj ikony 16 x 16 pikseli w pliku .bmp. Umieść plik ikony w folderze \DslPackage\Resources\, a następnie zmień nazwę pliku, aby **ModelExplorerToolWindowBitmaps.bmp**. Na przykład można zmienić pliku ikony programu Visual Studio setup.ico bmp format i zmień jej nazwę na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Wygenerowanego projektanta będzie ta ikona jest wyświetlana na karcie Eksplorator usługi, gdy jest zadokowany wraz z **Eksploratora rozwiązań**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Ustawienia niestandardowe ikony na węzłach Explorer
 Węzły w Eksploratorze można dostosować za pomocą ustawienia węzła Eksploratora. Poniższa procedura pokazuje, jak dodać ikonę do węzła.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Aby dodać ikonę do węzła Eksploratora

1.  Utwórz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązania za pomocą szablonu rozwiązania przepływu zadań.

2.  Umieść plik .bmp, który zawiera ikonę 16 x 16 pikseli **Dsl\Resources** folder w rozwiązaniu.

3.  W **Eksplorator DSL**, kliknij prawym przyciskiem myszy **zachowanie Eksploratora** a następnie kliknij przycisk **Dodaj nowe ustawienia węzła Eksploratora**.

     **ExplorerNodeSettings** pojawia się pod węzłem **niestandardowe ustawienia węzła** węzła.

4.  Wybierz **ExplorerNodeSettings**, a następnie w polu **właściwości** oknie **klasy** do **aktora**.

5.  Ustaw **ikonę do wyświetlenia** ścieżkę pliku ikony.

6.  Transformuj wszystkie szablony, a następnie, skompiluj i uruchom rozwiązanie.

7.  Otwórz przykładowy diagram w wygenerowanym projektancie.

     Eksplorator powinny być widoczne trzy **aktora** węzły, które mają ikona.

> [!NOTE]
>  Jeśli zostały ustawione ikoną węzła dla każdego elementu wyświetlanego w Eksploratorze wygenerowane, wszystkie węzły w Eksploratorze zostanie wyświetlona ikona. Jeśli nie ustawiono żadnej ikony, węzły, zostanie wyświetlona ikona domyślna.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Zmiana nazwy wyświetlane w węźle Explorer
 Możesz zmienić sposób wyświetlania nazwy elementów modelu w Eksploratorze. Poniższa procedura przedstawia sposób wyświetlania nazwy **zadań** która odwołuje się do niej **komentarz** w węźle komentarz.

#### <a name="to-display-a-property"></a>Aby wyświetlić właściwości

1.  Otwórz rozwiązanie, który został utworzony we wcześniejszej procedurze.

2.  Upewnij się, że **komentarz** odwołuje się do klasy pojedynczej domeny przez ustawienie Liczebność roli o nazwie właściwości **przedmioty** się od 0 do 1. Nazwa właściwości, powinny stać się **podmiotu**, a Nazwa relacji powinna stać się **CommentReferencesSubject**.

3.  W **Eksplorator DSL**, kliknij prawym przyciskiem myszy **zachowanie Eksploratora** a następnie kliknij przycisk **Dodaj nowe ustawienia węzła Eksploratora**.

     **ExplorerNodeSettings** pojawia się pod węzłem **niestandardowe ustawienia węzła** węzła.

4.  Wybierz **ExplorerNodeSettings**, a następnie w polu **właściwości** oknie **klasy** do **komentarz**.

5.  Kliknij prawym przyciskiem myszy **komentarz** węzłem, a następnie kliknij przycisk **Dodaj nową ścieżkę właściwości**.

     Pojawi się nowy węzeł o nazwie **właściwość wyświetlana**.

6.  Wybierz **właściwość wyświetlana**, a następnie w polu **właściwości** okna, kliknij pole wartości **właściwości ścieżki**. Wybierz **komentarz**, następnie **CommentReferencesSubject**, następnie **FlowElement**. Ścieżka wynikowa powinien przypominać **CommentReferencesSubject.Subject/! Temat**.

7.  W polu wartość **właściwość**, wybierz opcję **nazwa**.

8.  Transformuj wszystkie szablony, a następnie Skompiluj i uruchom swoje rozwiązanie.

9. Otwórz przykładowy diagram w wygenerowanym projektancie.

10. Rysowanie **łącznika komentarz** między elementem komentarz i **Task1** elementu na diagramie.

     Węzła Eksploratora powinien być wyświetlany w komentarzu jako **Task1**.

## <a name="hiding-nodes"></a>Ukrywanie węzłów
 Można ukryć węzeł w Eksploratorze przez dodanie jego ścieżki do **ukrytych węzłów** węźle **Eksplorator DSL**. Poniższa procedura pokazuje, jak ukrywać **komentarz** węzłów.

#### <a name="to-hide-an-explorer-node"></a>Aby ukryć węzeł Eksploratora

1.  Otwórz rozwiązanie, który został utworzony we wcześniejszej procedurze.

2.  W **Eksplorator DSL**, kliknij prawym przyciskiem myszy **zachowanie Eksploratora** a następnie kliknij przycisk **Dodaj nową ścieżkę domeny**.

     A **ścieżka domeny** pojawia się pod węzłem **ukrytych węzłów**.

3.  Wybierz **ścieżka domeny**, a następnie w polu **właściwości** okna, kliknij pole wartości **definicja ścieżki**. Wybierz **FlowGraph**, następnie **FlowGraphHasComments**. Ścieżka wynikowa powinien przypominać **FlowGraphHasComments.Comments**

4.  Transformuj wszystkie szablony, a następnie Skompiluj i uruchom swoje rozwiązanie.

5.  Otwórz przykładowy diagram w wygenerowanym projektancie.

     Eksplorator powinny pokazywać tylko **aktorów** węzeł i nie powinien być wyświetlony **komentarze** węzła.

## <a name="see-also"></a>Zobacz także

- [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)