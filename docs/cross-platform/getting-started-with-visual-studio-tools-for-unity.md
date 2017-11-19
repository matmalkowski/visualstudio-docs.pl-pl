---
title: "Wprowadzenie do narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: "10"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 03fd3a4cc84852ad922dec417850a0f4a0b1ea1c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Wprowadzenie do narzędzi Visual Studio Tools for Unity
W tej sekcji dowiesz się, jak zainstalować program Visual Studio Tools for Unity i skonfigurować projektu Unity do pracy z programem Visual Studio.  

> [!IMPORTANT]
>  Unity 5.2 dodaje wbudowana obsługa programu Visual Studio Tools for Unity 2.1, co upraszcza ustawienia projektu. Aby skorzystać z tego, musisz Unity wersji 5.2.0 lub nowszej w systemach Windows i programu Visual Studio Tools for Unity w wersji 2.1 lub wyższej.  

## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć programu Visual Studio Tools for Unity, potrzebne są:  

-   Wersja **programu Visual Studio** obsługującej rozszerzenia, takie jak Visual Studio Community, Professional, Premium lub Enterprise. Visual Studio Community można pobrać bezpłatnie.  

     [Pobierz program Visual Studio Community](http://www.visualstudio.com/downloads/download-visual-studio-vs)  

-   **Unity** wersji 4.0.0 lub wyższy. **Unity** wersji 5.2.0 lub nowszej, aby móc korzystać z wbudowaną obsługą dla programu Visual Studio Tools for Unity w wersji 2.1 lub wyższej.  

     [Pobierz Unity](https://unity3d.com/get-unity/download)  

## <a name="install-visual-studio-tools-for-unity"></a>Instalowanie narzędzi Visual Studio Tools for Unity  
 Pobierz i zainstaluj program Visual Studio Tools for Unity z galerii programu Visual Studio. Musisz zainstalować pakiet prawo dla używanej wersji programu Visual Studio. Upewnij się zainstalować narzędzia Visual Studio Tools for Unity w wersji 2.1 lub wyższej móc korzystać z wbudowaną obsługę pomocą rozszerzenia VSTU w Unity 5.2 lub wyższym.  

-   Dla programu Visual Studio Community 2015, Visual Studio 2015 Professional lub Visual Studio 2015 Enterprise:  

     [Pobierz program Visual Studio 2015 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  

-   Dla programu Visual Studio Community 2013, Visual Studio 2013 Professional lub Visual Studio 2013 — wersja Premium:  

     [Pobierz Visual Studio 2013 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  

-   Dla programu Visual Studio 2012 Professional lub Visual Studio 2012 Premium:  

     [Pobierz program Visual Studio 2012 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  

-   Dla programu Visual Studio Professional 2010 lub Visual Studio 2010 Premium:  

     [Pobierz program Visual Studio 2010 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  

> [!NOTE]
>  Wersji Express programu Visual Studio nie obsługuje rozszerzeń, takich jak program Visual Studio Tools for Unity. Visual Studio Community to bezpłatna wersja programu Visual Studio, która obsługuje program Visual Studio Tools for Unity i inne rozszerzenia. Dla większości użytkowników programu Visual Studio Community jest lepszym rozwiązaniem niż Express.  

> [!NOTE]
>  Dla programu Visual Studio 2017 r. pomocą rozszerzenia VSTU 3 zawiera obciążenie Unity, które są dostępne z Instalatora.  

## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Pierwszy projektu Unity za pomocą narzędzi Visual Studio Tools for Unity  
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz przystąpić do pierwszego projektu Unity z programem Visual Studio. Konfigurowanie projektu Unity różni się w zależności od tego, które wersje Unity i narzędzia Visual Studio Tools for Unity są instalowane. Wykonaj poniższe kroki dla wersji platformy Unity i narzędzia Visual Studio Tools for Unity, który został zainstalowany.  

### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5.2 i nowszej (wymaga pomocą rozszerzenia VSTU 2.1 lub wyższej)  
 Począwszy od platformy Unity 5.2, masz już do importowania unitypackage narzędzi programu Visual Studio do projektów. Jeśli projekt importuje ten unitypackage, Unity 5.2 ignoruje go i bezpośrednio ładuje z lokalizacji zainstalowanego programu Visual Studio Tools for Unity.  

#### <a name="1---create-a-unity-project"></a>1 — Tworzenie projektu platformy Unity  
 Jeśli już masz doświadczenia w pracy z Unity, możesz utworzyć nowy projekt lub załadować własny. Ładowania projektu, który zaimportował unitypackage narzędzi programu Visual Studio, aby użyć programu Visual Studio Tools for Unity przy pomocy poprzedniej wersji platformy Unity, zaleca się usunięcie przez usunięcie katalogu UnityVS.  

 W przeciwnym razie jeśli jesteś nowym użytkownikiem Unity, zacznij od czegoś małego z samouczka podstawowe. Odwiedź stronę Unity Dowiedz się, aby znaleźć samouczki, na przykład projektów, które można uruchomić z poziomu i lekcje, który można uzyskać z Tworzenie gry z Unity. Dowiedz się, Unity strona ma samouczki łatwe do wykonania w przypadku kilku różnych gier.  

 [Samouczki — strona Unity Dowiedz się więcej](http://unity3d.com/learn/tutorials/modules)  

#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 — Konfigurowanie Edytor platformy Unity do narzędzia Visual Studio Tools for Unity  
 Aby włączyć projektu do programu Visual Studio Tools for Unity, ustawić Visual Studio jako jego skryptu zewnętrznego edytora. W edytorze Unity menu głównego, wybierz polecenie **Edytuj preferencje**; a następnie na **preferencje Unity** okno dialogowe, wybierz **zewnętrznych narzędzi**. Następnie ustaw **zewnętrznego edytora skryptów** właściwości do wersji programu Visual Studio, którego chcesz użyć (dla tej wersji programu Visual Studio musi być zainstalowany program Visual Studio Tools dla Unity) i upewnij się, że **Dołączanieedytora** właściwość jest ustawiona.  

 Aby upewnić się, że wbudowana obsługa programu Visual Studio Tools dla Unity jest teraz włączony, zobacz **o Unity** okna dialogowego. W edytorze Unity w menu głównym wybierz **pomocy o Unity.** Jeśli Visual Studio Tools for Unity jest zainstalowana i poprawnie skonfigurowana, zobaczysz komunikat wyświetlany w lewym dolnym rogu **o Unity** okna dialogowego.  

 Ponadto upewnij się, ustawiono obiektu docelowego kompilacji za pomocą **ustawieniach kompilacji** strony oraz że **debugowanie skryptu** jest włączona.  

 ![Konfigurowanie ustawień kompilacji platformy Unity do debugowania. ] (../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")  

#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3 — uruchamianie programu Visual Studio z edytora Unity  
 Począwszy od Unity 5.2 **programu Visual Studio Tools** menu rozszerzenia nie jest już potrzebne do uruchomienia programu Visual Studio lub do konfigurowania programu Visual Studio Tools for Unity. Zamiast tego po Visual Studio jest skonfigurowany jako edytora skryptu zewnętrznego, wystarczy wybrać plik skryptu w edytorze Unity i kodu zostanie otwarty w programie Visual Studio.  

### <a name="previous-versions-of-unity-pre-52"></a>Poprzednie wersje jedności (pre-5.2)  
 Przed Unity 5.2 nie było żadnych wbudowana obsługa programu Visual Studio Tools for Unity. Zamiast tego należy zaimportować unitypackage Visual Studio Tools i skonfigurować inne ustawienia projektu, aby można było używać programu Visual Studio Tools for Unity musiał każdego projektu.  

#### <a name="1---create-a-unity-project"></a>1 — Tworzenie projektu platformy Unity  
 Jeśli już masz doświadczenia w pracy z Unity, możesz utworzyć nowy projekt lub załadować własny. Jeśli zaczynasz nowy projekt, należy zaimportować unitypackage Visual Studio Tools podczas jego tworzenia.  

 W przeciwnym razie jeśli jesteś nowym użytkownikiem Unity, zacznij od czegoś małego z samouczka podstawowe. Odwiedź stronę Unity Dowiedz się, aby znaleźć samouczki, na przykład projektów, które można uruchomić z poziomu i lekcje, który można uzyskać z Tworzenie gry z Unity. Dowiedz się, Unity strona ma samouczki łatwe do wykonania w przypadku kilku różnych gier.  

 [Samouczki — strona Unity Dowiedz się więcej](http://unity3d.com/learn/tutorials/modules)  

#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 — Konfigurowanie Edytor platformy Unity do narzędzia Visual Studio Tools for Unity  
 Jeśli zaczynasz z istniejącego projektu platformy Unity lub nie importować unitypackage Visual Studio Tools, podczas tworzenia projektu, należy zaimportować unitypackage teraz. W edytorze Unity w menu głównym wybierz **zasobów, importowanie pakietu Visual Studio 2015 Tools** (powinien zostać wyświetlony opcję dla używanej wersji programu Visual Studio zainstalowany).  

 ![Importuj pakiet pomocą rozszerzenia VSTU do projektu platformy Unity. ] (../cross-platform/media/vstu_configure_unity_import_vstu.png "vstu_configure_unity_import_vstu")  

 Ponadto upewnij się, ustawiono obiektu docelowego kompilacji za pomocą **ustawieniach kompilacji** strony oraz że **debugowanie skryptu** jest włączona.  

 ![Konfigurowanie ustawień kompilacji platformy Unity do debugowania. ] (../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")  

#### <a name="3---launch-visual-studio-from-unity-editor"></a>3 — uruchamianie programu Visual Studio z edytora Unity  
 Ostatnim krokiem jest uruchomienie programu Visual Studio z Unity. Tworzy rozwiązanie Visual Studio dla projektu, a następnie zostanie otwarty w programie Visual Studio.  

 W edytorze Unity w menu głównym wybierz **programu Visual Studio Tools, Otwórz w programie Visual Studio**.  

 ![Otwórz projekt środowiska unity w programie Visual Studio. ] (../cross-platform/media/vstu_configure_open_in_visual_studio.png "vstu_configure_open_in_visual_studio")  

## <a name="next-steps"></a>Następne kroki  

 Aby dowiedzieć się, jak pracować z i debugowania projektu środowiska Unity w programie Visual Studio, zobacz [za pomocą narzędzi Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).  

## <a name="see-also"></a>Zobacz też  
 [Strona główna Unity](http://unity3d.com)
