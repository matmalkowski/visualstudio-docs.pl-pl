---
title: "Wskazówki: Tworzenie zestawu SDK, w języku C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a4091506bcd16222ff02600bd924d3526d57c38
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Wskazówki: Tworzenie zestawu SDK, w języku C++
W tym przewodniku pokazano, jak do utworzenia natywnego C++ matematyczne biblioteki zestawu SDK, pakiet SDK jako Visual rozszerzenia Studio (VSIX), a następnie użyć jej do utworzenia aplikacji. Instruktaż jest podzielona na następujące kroki:  
  
-   [Aby utworzyć macierzystego i bibliotek środowiska uruchomieniowego systemu Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Aby utworzyć przykładową aplikację używającą biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>Aby utworzyć macierzystego i bibliotek środowiska uruchomieniowego systemu Windows  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C++**, **uniwersalnych systemu Windows**, a następnie wybierz **DLL (uniwersalnych aplikacji systemu Windows)** szablonu. W **nazwa** określ `NativeMath`, a następnie wybierz pozycję **OK** przycisku.  
  
3.  Zaktualizuj NativeMath.h odpowiadające poniższy kod.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Aktualizacja NativeMath.cpp odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów **rozwiązania "NativeMath"**, a następnie wybierz pozycję **Dodaj**, **nowy projekt**.  
  
6.  Na liście szablonów, rozwiń węzeł **Visual C++**, a następnie wybierz **składnika środowiska wykonawczego systemu Windows** szablonu. W **nazwa** określ `NativeMathWRT`, a następnie wybierz pozycję **OK** przycisku.  
  
7.  Aktualizacja Class1.h odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Aktualizacja Class1.cpp odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
##  <a name="createVSIX"></a>Aby utworzyć projekt rozszerzenia NativeMathVSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **rozwiązania "NativeMath"**, a następnie wybierz pozycję **Dodaj**, **nowy projekt**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C#**, **rozszerzalności**, a następnie wybierz **projektu VSIX**. W **nazwa** określ **NativeMathVSIX**, a następnie wybierz pozycję **OK** przycisku.
  
3.  W **Eksploratora rozwiązań**, otwórz menu skrótów **source.extension.vsixmanifest**, a następnie wybierz pozycję **kod widoku**.  
  
4.  Użyj następujących XML można zastąpić istniejącego pliku XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  W **Eksploratora rozwiązań**, otwórz menu skrótów **NativeMathVSIX** projektu, a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
6.  Na liście **Visual C# elementów**, rozwiń węzeł **danych**, a następnie wybierz **pliku XML**. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz pozycję **OK** przycisku.  
  
7.  Zastąp zawartość pliku za pomocą tego kodu XML:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. W **Eksploratora rozwiązań**w **NativeMathVSIX** projekt, utworzenie tej struktury folderów:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
9. W **Eksploratora rozwiązań**, otwórz menu skrótów **rozwiązania "NativeMath"**, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików**.  
  
10. W **Eksploratora plików**, skopiuj $SolutionRoot$\NativeMath\NativeMath.h, a następnie w **Eksploratora rozwiązań**w **NativeMathVSIX** projekt, wklej go w $SolutionRoot$ \ NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\ folder.  
  
     Skopiuj $SolutionRoot$\Debug\NativeMath\NativeMath.lib, a następnie wklej go w folderze $SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\.  
  
     $SolutionRoot$\Debug\NativeMath\NativeMath.dll skopiuj i wklej go w folderze $SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\.  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll skopiuj i wklej go w folderze $SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86.  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd skopiuj i wklej go w folderze $SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral.  
  
     $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri skopiuj i wklej go w folderze $SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral.  
  
11. W folderze $SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\ Utwórz plik tekstowy o nazwie NativeMathSDK.props, a następnie wklej poniższą zawartość w niej:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. Na pasku menu wybierz **widoku**, **inne okna**, **okna właściwości** (klawiatury: Wybierz klucz F4).  
  
13. W **Eksploratora rozwiązań**, wybierz pozycję **NativeMathWRT.winmd** pliku. W **właściwości** Zmień **Akcja kompilacji** właściwości **zawartości**, a następnie zmień **Include w pliku VSIX** właściwości  **Wartość true,**.  
  
     Powtórz ten proces dla **NativeMath.h** pliku.  
  
     Powtórz ten proces dla **NativeMathWRT.pri** pliku.  
  
     Powtórz ten proces dla **NativeMath.Lib** pliku.  
  
     Powtórz ten proces dla **NativeMathSDK.props** pliku.  
  
14. W **Eksploratora rozwiązań**, wybierz pozycję **NativeMath.h** pliku. W **właściwości** Zmień **Include w pliku VSIX** właściwości **True**.  
  
     Powtórz ten proces dla **NativeMath.dll** pliku.  
  
     Powtórz ten proces dla **NativeMathWRT.dll** pliku.  
  
     Powtórz ten proces dla **SDKManifest.xml** pliku.  
  
15. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
16. W **Eksploratora rozwiązań**, otwórz menu skrótów **NativeMathVSIX** projektu, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików**.  
  
17. W **Eksploratora plików**, przejdź do folderu \NativeMathVSIX\bin\Debug\ $ $SolutionRoot, a następnie uruchom NativeMathVSIX.vsix, aby rozpocząć instalację.  
  
18. Wybierz **zainstalować** przycisku, poczekaj na zakończenie instalacji, a następnie uruchom program Visual Studio.  
  
##  <a name="createSample"></a>Aby utworzyć przykładową aplikację używającą biblioteki klas  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C++**, **uniwersalnych systemu Windows**, a następnie wybierz **pusta aplikacja**. W **nazwa** określ **NativeMathSDKSample**, a następnie wybierz pozycję **OK** przycisku.  
  
3.  W **Eksploratora rozwiązań**, otwórz menu skrótów **NativeMathSDKSample** projektu, a następnie wybierz pozycję **Dodaj**, **odwołania**.  
  
4.  W **Dodaj odwołanie** okno dialogowe, na liście typów referencyjnych, rozwiń węzeł **uniwersalnych systemu Windows**, a następnie wybierz **rozszerzenia**. Na koniec wybierz **natywnego SDK matematyczne** pole wyboru, a następnie wybierz pozycję **OK** przycisku.
  
5.  Wyświetl właściwości projektu dla NativeMathSDKSample.  
  
     Właściwości zdefiniowane w NativeMathSDK.props zostały zastosowane podczas dodawania odwołania. Można to sprawdzić, przeglądając **katalogi VC ++** właściwości projektu **właściwości konfiguracji**.  
  
6.  W **Eksploratora rozwiązań**, otwórz MainPage.xaml, a następnie użyj następujących XAML, aby zastąpić jej zawartość:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  Aktualizacja Mainpage.xaml.h odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Aktualizacja MainPage.xaml.cpp odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Wybierz klawisz F5, aby uruchomić aplikację.  
  
10. W aplikacji, wprowadź wszelkie dwóch liczb, wybierz operację, a następnie wybierz  **=**  przycisku.  
  
     Zostanie wyświetlone prawidłowego wyniku.  
  
 W tym przewodniku pokazano, jak utworzyć i użyć zestawu SDK rozszerzenia do wywołania w [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki i niż[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki.  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)