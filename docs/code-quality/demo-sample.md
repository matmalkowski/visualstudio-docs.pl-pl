---
title: "Pokaz przykładowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6ce56a055792d1360b78dda8295e9ee4d39a0b98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="demo-sample"></a>Przykład
Ten poniższe procedury pokazują, jak utworzyć przykładowy dla [wskazówki: analizowanie kodu C++ pod względem wad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Utwórz procedury:  
  
-   A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania o nazwie CppDemo.  
  
-   Projekt biblioteki statycznej o nazwie CodeDefects.  
  
-   Projekt biblioteki statycznej o nazwie adnotacji.  
  
 Procedury stanowią Ponadto kod pliki nagłówka i .cpp dla bibliotek statycznych.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Tworzenie rozwiązania CppDemo i CodeDefects projektu  
  
1.  Kliknij przycisk **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **typy projektów** drzewa listy, jeśli program Visual C++ nie jest domyślnym językiem w programie VS rozwiń **inne języki**.  
  
3.  Rozwiń węzeł **Visual C++**, a następnie kliknij przycisk **ogólne**.  
  
4.  W **szablony**, kliknij przycisk **pusty projekt**.  
  
5.  W **nazwa** polu tekstowym **CodeDefects**.  
  
6.  Wybierz **Utwórz katalog rozwiązania** pole wyboru.  
  
7.  W **Nazwa rozwiązania** polu tekstowym **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurowanie projektu CodeDefects jako biblioteki statycznej  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **CodeDefects** , a następnie kliknij przycisk **właściwości**.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** , a następnie kliknij przycisk **ogólne**.  
  
3.  W **ogólne** listy, zaznacz tekst, w kolumnie obok **rozszerzenie docelowego**, a następnie wpisz **.lib**.  
  
4.  W **domyślne projektu**, kliknij kolumnę obok **typu konfiguracji**, a następnie kliknij przycisk **statycznej Lib (lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Dodawanie pliku nagłówka i źródła do projektu CodeDefects  
  
1.  W Eksploratorze rozwiązań rozwiń **CodeDefects**, kliknij prawym przyciskiem myszy **pliki nagłówkowe**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kod**, a następnie kliknij przycisk **plik nagłówków (.h)**.  
  
3.  W **nazwa** wpisz **Bug.cpp** , a następnie kliknij przycisk **Dodaj**.  
  
4.  Skopiuj poniższy kod i wklej ją do **Bug.cpp** w pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliki źródłowe**, wskaż polecenie **nowy**, a następnie kliknij przycisk **nowy element**.  
  
6.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **plik C++ (.cpp)**  
  
7.  W **nazwa** wpisz **Bug.cpp** , a następnie kliknij przycisk **Dodaj**.  
  
8.  Skopiuj poniższy kod i wklej go do pliku Bug.h w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Kliknij przycisk **pliku** menu, a następnie kliknij przycisk **Zapisz wszystko**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Dodaj adnotacje projektu i skonfiguruj go jako biblioteki statycznej  
  
1.  W Eksploratorze rozwiązań kliknij **CppDemo**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego polu Rozwiń Visual C++, kliknij przycisk **ogólne**, a następnie kliknij przycisk **pusty projekt**.  
  
3.  W **nazwa** polu tekstowym **adnotacje**, a następnie kliknij przycisk **Dodaj**.  
  
4.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **adnotacje** , a następnie kliknij przycisk **właściwości**.  
  
5.  Rozwiń węzeł **właściwości konfiguracji** , a następnie kliknij przycisk **ogólne**.  
  
6.  W **ogólne** listy, zaznacz tekst, w kolumnie obok **rozszerzenie docelowego**, a następnie wpisz **.lib**.  
  
7.  W **domyślne projektu**, kliknij kolumnę obok **typu konfiguracji**, a następnie kliknij przycisk **statycznej Lib (lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Dodaj plik nagłówka i plik źródłowy do projektu adnotacji  
  
1.  W Eksploratorze rozwiązań rozwiń **adnotacje**, kliknij prawym przyciskiem myszy **pliki nagłówkowe**, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **plik nagłówków (.h)**.  
  
3.  W **nazwa** wpisz **annotations.h** , a następnie kliknij przycisk **Dodaj**.  
  
4.  Skopiuj poniższy kod i wklej ją do **annotations.h** w pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliki źródłowe**, wskaż polecenie **nowy**, a następnie kliknij przycisk **nowy element**.  
  
6.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kod** , a następnie kliknij przycisk **plik C++ (.cpp)**  
  
7.  W **nazwa** wpisz **annotations.cpp** , a następnie kliknij przycisk **Dodaj**.  
  
8.  Skopiuj poniższy kod i wklej ją do **annotations.cpp** w pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Kliknij przycisk **pliku** menu, a następnie kliknij przycisk **Zapisz wszystko**.