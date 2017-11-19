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
ms.openlocfilehash: bc30e3236f81f558f3794bb459f6da3edbdaa63d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
  
2.  Na liście szablonów, rozwiń węzeł **Visual C++**, **Sklepu Windows**, a następnie wybierz **DLL (aplikacje ze Sklepu Windows)** szablonu. W **nazwa** określ `NativeMath`, a następnie wybierz pozycję **OK** przycisku.  
  
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
  
2.  Na liście szablonów, rozwiń węzeł **Visual C#**, **rozszerzalności**, a następnie wybierz **pakietu VSIX**. W **nazwa** określ **NativeMathVSIX**, a następnie wybierz pozycję **OK** przycisku.  
  
3.  Gdy pojawi się projektanta manifestu VSIX, należy go zamknąć.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **source.extension.vsixmanifest**, a następnie wybierz pozycję **kod widoku**.  
  
5.  Użyj następujących XML można zastąpić istniejącego pliku XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  W **Eksploratora rozwiązań**, otwórz menu skrótów **NativeMathVSIX** projektu, a następnie wybierz pozycję **Dodaj**, **nowy element**.  
  
7.  Na liście **Visual C# elementów**, rozwiń węzeł **danych**, a następnie wybierz **pliku XML**. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz pozycję **OK** przycisku.  
  
8.  Zastąp zawartość pliku za pomocą tego kodu XML:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. W **Eksploratora rozwiązań**w **NativeMathVSIX** projekt, utworzenie tej struktury folderów:  
  
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
  
10. W **Eksploratora rozwiązań**, otwórz menu skrótów **rozwiązania "NativeMath"**, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików**.  
  
11. W **Eksploratora plików**, skopiuj \NativeMath\NativeMath.h, a następnie w **Eksploratora rozwiązań**w **NativeMathVSIX** projektu, wklej go w \DesignTime\ CommonConfiguration\Neutral\Include\ folder.  
  
     Skopiuj \Debug\NativeMath\NativeMath.lib, a następnie wklej go w folderze \DesignTime\Debug\x86\.  
  
     \Debug\NativeMath\NativeMath.dll skopiuj i wklej go w folderze \Redist\Debug\x86\.  
  
     DebugNativeMathWRTNativeMathWRT.dll skopiuj i wklej go w folderze RedistDebugx86.  
  
     DebugNativeMathWRTNativeMathWRT.winmd skopiuj i wklej go w folderze ReferencesCommonConfigurationNeutral.  
  
     DebugNativeMathWRTNativeMathWRT.pri skopiuj i wklej go w folderze ReferencesCommonConfigurationNeutral.  
  
12. W folderze \DesignTime\Debug\x86\ Utwórz plik tekstowy o nazwie NativeMathSDK.props, a następnie wklej poniższą zawartość w niej:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na pasku menu wybierz **widoku**, **inne okna**, **okna właściwości** (klawiatury: Wybierz klucz F4).  
  
14. W **Eksploratora rozwiązań**, wybierz pozycję **NativeMathWRT.winmd** pliku. W **właściwości** Zmień **Akcja kompilacji** właściwości **zawartości**, a następnie zmień **Include w pliku VSIX** właściwości  **Wartość true,**.  
  
     Powtórz ten proces dla **SimpleMath.pri** pliku.  
  
     Powtórz ten proces dla **NativeMath.Lib** pliku.  
  
     Powtórz ten proces dla **NativeMathSDK.props** pliku.  
  
15. W **Eksploratora rozwiązań**, wybierz pozycję **NativeMath.h** pliku. W **właściwości** Zmień **Include w pliku VSIX** właściwości **True**.  
  
     Powtórz ten proces dla **NativeMath.dll** pliku.  
  
     Powtórz ten proces dla **NativeMathWRT.dll** pliku.  
  
     Powtórz ten proces dla **SDKManifest.xml** pliku.  
  
16. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
17. W **Eksploratora rozwiązań**, otwórz menu skrótów **NativeMathVSIX** projektu, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików**.  
  
18. W **Eksploratora plików**, przejdź do folderu \bin\Debug\, a następnie uruchom NativeMathVSIX.vsix, aby rozpocząć instalację.  
  
19. Wybierz **zainstalować** przycisku, poczekaj na zakończenie instalacji i ponownym uruchomieniu programu Visual Studio.  
  
##  <a name="createSample"></a>Aby utworzyć przykładową aplikację używającą biblioteki klas  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Na liście szablonów, rozwiń węzeł **Visual C++**, **Sklepu Windows**, a następnie wybierz **pusta aplikacja**. W **nazwa** określ **NativeMathSDKSample**, a następnie wybierz pozycję **OK** przycisku.  
  
3.  W **Eksploratora rozwiązań**, otwórz menu skrótów **NativeMathSDKSample** projektu, a następnie wybierz pozycję **Dodaj**, **odwołania**.  
  
4.  Na **wspólnych właściwości**, **Framework i odwołania** strony właściwości, na liście typów referencyjnych, rozwiń węzeł **Windows**, a następnie wybierz **rozszerzenia** . W okienku szczegółów wybierz **natywnego SDK matematyczne** rozszerzenia, a następnie wybierz **Dodaj nowe odwołanie** przycisku.  
  
5.  W **Dodaj odwołanie** okno dialogowe, wybierz opcję **natywnego SDK matematyczne** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
6.  Wyświetl właściwości projektu dla NativeMathSDKSample.  
  
     Właściwości zdefiniowane w NativeMathSDK.props zostały zastosowane podczas dodawania odwołania. Można to sprawdzić, przeglądając **katalogi VC ++** właściwości projektu **właściwości konfiguracji**.  
  
7.  W **Eksploratora rozwiązań**, otwórz MainPage.xaml, a następnie użyj następujących XAML, aby zastąpić jej zawartość:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Aktualizacja Mainpage.xaml.h odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Aktualizacja MainPage.xaml.cpp odpowiadające ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Wybierz klawisz F5, aby uruchomić aplikację.  
  
11. W aplikacji, wprowadź wszelkie dwóch liczb, wybierz operację, a następnie wybierz  **=**  przycisku.  
  
     Zostanie wyświetlone prawidłowego wyniku.  
  
 W tym przewodniku pokazano, jak utworzyć i użyć zestawu SDK rozszerzenia do wywołania w [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki i niż[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki.  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md)