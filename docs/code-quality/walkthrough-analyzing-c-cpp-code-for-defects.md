---
title: "Wskazówki: Analizowanie kodu C++ pod względem wad | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c95d03201fe9c84e01e83e7fd55bef83755337e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Wskazówki: analizowanie kodu C++ pod względem wad
W tym przewodniku pokazano, jak analiza kodu C/C++ pod względem wad kodu potencjalnych przy użyciu narzędzia do analizy kodu dla kodu C/C++.  
  
 W tym przewodniku krok w procesie za pomocą analizy kodu do analizy kodu C/C++ pod względem wad kodu potencjalnych.  
  
 Zostanie wykonaj następujące czynności:  
  
-   Uruchom analizę kodu dla kodu natywnego.  
  
-   Przeanalizuj ostrzeżenia wad kodu.  
  
-   Traktuj ostrzeżenia jako błędy.  
  
-   Dodawanie adnotacji kodu źródłowego, aby poprawić kod — analiza wady.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]lub [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Kopię [próbka Demo](../code-quality/demo-sample.md).  
  
-   Podstawową wiedzę na temat C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Do uruchomienia kod — analiza usterką w kodzie natywnym  
  
1.  Otwórz rozwiązanie pokaz w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Rozwiązanie pokaz teraz wypełnia **Eksploratora rozwiązań**.  
  
2.  Na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.  
  
     Buduje rozwiązanie bez żadnych błędów lub ostrzeżeń.  
  
3.  W **Eksploratora rozwiązań**, wybierz projekt CodeDefects.  
  
4.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Strony właściwości CodeDefects** zostanie wyświetlone okno dialogowe.  
  
5.  Kliknij przycisk **analiza kodu**.  
  
6.  Kliknij przycisk **Włącz analizę kodu dla C/C++ podczas kompilacji** pole wyboru.  
  
7.  Skompiluj ponownie projekt CodeDefects.  
  
     Ostrzeżenia analizy kodu są wyświetlane w **listy błędów**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Do analizowania ostrzeżenia wad kodu  
  
1.  Na **widoku** menu, kliknij przycisk **listy błędów**.  
  
     W zależności od wybranego w profilu developer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], może być konieczne wskaż **inne okna** na **widoku** menu, a następnie kliknij przycisk **listy błędów**.  
  
2.  W **listy błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6230: niejawne rzutowanie pomiędzy różnymi semantycznie typami: użycie HRESULT w kontekście Boolean.  
  
     Edytor kodu wyświetla wiersz, który spowodował ostrzeżenia w funkcji `bool``ProcessDomain()`. To ostrzeżenie oznacza, że HRESULT jest używana w instrukcji "if" gdzie jest oczekiwany wynik będący wartością logiczną.  
  
3.  Popraw to ostrzeżenie, za pomocą makra zakończyło się pomyślnie. Kod powinien wyglądać następujący kod:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  W **listy błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6282: niepoprawny operator: przypisanie stałej w kontekście testu. Został == zamierzone?  
  
5.  Testowanie pod kątem równości, aby poprawić to ostrzeżenie. Kod powinien wyglądać podobnie do poniższego kodu:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Aby Traktuj ostrzeżenia jako błędy  
  
1.  W pliku Bug.cpp, Dodaj następujący `#pragma` instrukcji na początku pliku do Traktuj ostrzeżenie C6001 jako błąd:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Skompiluj ponownie projekt CodeDefects.  
  
     W **listy błędów**, C6001 jest teraz wyświetlany jako błąd.  
  
3.  Popraw błędy C6001 dwóch pozostałych w **listy błędów** przez inicjowanie `i` i `j` na 0.  
  
4.  Skompiluj ponownie projekt CodeDefects.  
  
     Tworzy projekt bez żadnych ostrzeżeń ani błędów.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Aby rozwiązać ostrzeżenia adnotacji kodu źródłowego w annotation.c  
  
1.  W Eksploratorze rozwiązań wybierz projekt adnotacji.  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Strony właściwości adnotacji** zostanie wyświetlone okno dialogowe.  
  
3.  Kliknij przycisk **analiza kodu**.  
  
4.  Wybierz **Włącz analizę kodu dla C/C++ podczas kompilacji** pole wyboru.  
  
5.  Skompiluj ponownie projekt adnotacji.  
  
6.  W **listy błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6011: dereferencji wskaźnika NULL "newNode".  
  
     To ostrzeżenie oznacza błąd przez obiekt wywołujący, aby sprawdzić wartość zwrotną. W tym przypadku wywołanie **AllocateNode** może zwrócić wartości NULL (zobacz plik nagłówka annotations.h deklaracja funkcji AllocateNode).  
  
7.  Otwórz plik annotations.cpp.  
  
8.  Aby usunąć to ostrzeżenie, należy użyć instrukcji "if", aby przetestować wartości zwracanej. Kod powinien wyglądać następujący kod:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Skompiluj ponownie projekt adnotacji.  
  
     Tworzy projekt bez żadnych ostrzeżeń ani błędów.  
  
### <a name="to-use-source-code-annotation"></a>Aby użyć adnotacji kodu źródłowego  
  
1.  Adnotuj formalnych parametrów i zwraca wartość funkcji `AddTail` za pomocą warunków przed i po, jak pokazano w poniższym przykładzie:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Skompiluj ponownie projekt adnotacji.  
  
3.  W **listy błędów**, kliknij dwukrotnie następujące ostrzeżenie:  
  
     Ostrzeżenie C6011: usuwania odwołań wskaźnik NULL "węzła".  
  
     To ostrzeżenie oznacza, że węzła przekazanego do funkcji mogą mieć wartości null i wskazuje numer wiersza, w którym został zgłoszony ostrzeżenia.  
  
4.  Aby usunąć to ostrzeżenie, należy użyć instrukcji "if", aby przetestować wartości zwracanej. Kod powinien wyglądać następujący kod:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Skompiluj ponownie projekt adnotacji.  
  
     Tworzy projekt bez żadnych ostrzeżeń ani błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Analizowanie kodu zarządzanego pod kątem defektów](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)