---
title: "Visual Studio Tools for Unity przygotowanie wskazówki Azure | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 92f85e39d0f643e896457cae48ab10aa0446dfcd
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="prepare-the-development-environment"></a>Przygotuj Środowisko deweloperskie

Brak niektórych wymagań wstępnych przy użyciu zestawu SDK klienta usługi Azure Mobile w Unity.

## <a name="download-and-install-unity-2017"></a>Pobierz i zainstaluj Unity 2017

Unity 2017.1 lub nowszy jest wymagany. Wszystkie plany Unity pracy z przewodnikiem, łącznie z planu free osobistych. Pobierz Unity z https://store.unity.com/.

## <a name="download-and-install-visual-studio-2017"></a>Pobierz i zainstaluj program Visual Studio 2017 r.

Instruktaż wymaga programu Visual Studio 2017 15 ustęp 3 lub nowszym, wraz z rozwojem gier z Unity obciążenia. Wszystkie wersje programu Visual Studio 2017 pracy z przewodnikiem, w tym bezpłatna wersja Community.

1. Pobierz program Visual Studio 2017 na https://www.visualstudio.com/.

2. Instalowanie programu Visual Studio 2017 i upewnij się, że **gier programowanie z Unity** obciążenie jest włączona.

 ![Wybieranie obciążenia Unity](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Jeśli jest już zainstalowany program Visual Studio 2017 r, możesz można wyświetlać i modyfikować obciążeń, uruchamiając Instalator programu Visual Studio.

## <a name="create-a-new-3d-unity-project"></a>Utwórz nowy projekt platformy Unity 3D

Uruchom Unity i Utwórz nowy projekt 3D.

![Utwórz nowy projekt platformy Unity](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Ustaw Edytor skryptów do programu Visual Studio w wersji zapoznawczej 2017

Wybrano jego możliwości już Visual Studio 2017 r edytorem skryptu zewnętrznego dla Unity, że jest zapewnienie 15.3 wersji zapoznawczej.

1. Z jednolitości **Edytuj** menu, wybierz **Edytuj > Preferencje...** .

  ![Otwórz menu Preferencje](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Gdy okno Preferencje Unity wyskakującej, wybierz **zewnętrznych narzędzi** karcie po lewej stronie.

3. W **Edytor skryptów zewnętrzne** menu rozwijanego wybierz **programu Visual Studio 2017**.

  ![Zestaw skryptu zewnętrznego edytora](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Zmiany środowiska uruchomieniowego skryptów Unity 4.6 .NET
Instruktaż wymaga .NET 4.6, aby można było używać zestawu SDK klienta usługi Azure Mobile i jego zależności.

1. Z jednolitości **pliku** menu, wybierz **Plik > Ustawienia kompilacji...** .

  ![Otwórz ustawienia kompilacji](media/vstu_azure-prepare-dev-environment-image4.png)

2. Kliknij przycisk **ustawienia odtwarzacza...**  przycisku.

  ![Otwórz ustawienia odtwarzacza](media/vstu_azure-prepare-dev-environment-image5.png)

3. Ustawienia odtwarzacza zostanie otwarty w oknie Inspektora Unity. W obszarze **konfiguracji** kliknij pozycję **wersji środowiska wykonawczego skryptów** listy rozwijanej i wybierz **eksperymentalne (odpowiada 4.6 .NET)**. Wyświetla okno dialogowe z pytaniem o ponowne uruchomienie Unity. Wybierz **ponownego uruchomienia**.

  ![Wybierz .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Dodaj odwołanie do System.Net.Http.dll

Unity .NET 4.6 równoważne skryptów środowiska uruchomieniowego umożliwia korzystanie z pakietu System.Net.Http, co jest wymagane przez zestaw SDK klienta usługi Azure Mobile. Plik DLL znajduje się w Unity, jednak należy dodać odwołanie z niego korzystać.

1. W oknie projektu Edytor platformy Unity **kliknij prawym przyciskiem myszy** **zasoby** i wybierz polecenie **Pokaż w Eksploratorze**.

  ![Pokaż zasoby folder w Eksploratorze](media/vstu_azure-prepare-dev-environment-image7.png)

2. W oknie Eksploratora, które pojawia się, kliknij dwukrotnie **zasoby** katalogu, aby go otworzyć.

3. W katalogu zasobów **kliknij prawym przyciskiem myszy** i wybierz **nowy > Dokument tekstowy**.

4. Otwórz nowy dokument tekstowy w edytorze tekstów i Dodaj wiersz:`-r:System.Net.Http.dll`

5. Zapisz dokument i zamknij go.

4. Zmień nazwę nowy dokument tekstowy do "**mcs.rsp**" i należy je usunąć z rozszerzeniem txt.

  * Jeśli masz ukryte rozszerzenia plików, należy zmienić opcje Widok folderu ich wyświetlania.
  * Otwórz menu i typu "folderu opcje uruchamiania" do wyszukania. Wybierz opcję "**opcje Eksploratora plików**".
  * Wybierz **widoku** i w ustawieniach zaawansowanych upewnij się, "**Ukryj rozszerzenia znanych typów plików**" nie jest zaznaczone.

    ![Pokaż zasoby folder w Eksploratorze](media/vstu_azure-prepare-dev-environment-image8.png)

Po wykonaniu tych kroków powinny mieć plik o nazwie **mcs.rsp** z linią `r:System.Net.Http.dll` w katalogu głównym projektu Unity **zasoby** katalogu.

>[!NOTE]
> Funkcji odwołania wymaga Visual Studio Tools dla Unity 3.3 i powyżej, który znajduje się w Visual Studio 15 ustęp 3 + obciążenia Unity. Ten krok nie działa dla Ciebie, upewnij się, że masz pomocą rozszerzenia VSTU zainstalowana właściwa wersja.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Dodaj pakiet Newtonsoft.Json NuGet do projektu

Zestaw SDK klienta usługi Azure Mobile wymaga pakiet Newtonsoft.Json. Niestety Unity nie obsługuje NuGet. Otwórz projekt środowiska Unity w programie Visual Studio, Dodaj pakiet nuget Unity spowoduje usunięcie go przy następnym otwarciu projektu w edytorze Unity. Niemniej jednak pakiety NuGet można ręcznie dodać do projektu platformy Unity.

1. Utwórz nowy folder w katalogu zasobów projektu Unity o nazwie "**pakietów NuGet**". Jest to tylko organizacji.

2. Przejdź do https://www.nuget.org/packages/Newtonsoft.Json/ i kliknij przycisk **pobieranie ręczne** przycisku. Pobierz plik .nupkg.

  ![Pokaż zasoby folder w Eksploratorze](media/vstu_azure-prepare-dev-environment-image9.png)

3. Zlokalizuj nowo pobrany plik i zmień rozszerzenie pliku z .nupkg do **.zip**. Powinno to umożliwić można wyświetlać i wyodrębniać dołączonych plików, takich jak dowolnego innego pliku zip.

4. Otwórz lub Wyodrębnij katalogu zip i przejdź do **\lib\net45**.

5. Kopiuj **Newtonsoft.Json.dll** plik do projektu Unity **pakiety Assets\NuGet** katalogu.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Dodaj pakiet NuGet zestawu SDK klienta usługi Azure Mobile do projektu

Zestaw SDK klienta usługi Azure Mobile zawiera funkcje, które łatwo odczytu i zapisu do łatwego tabel Azure.

1. Przejdź do https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ i kliknij przycisk **pobieranie ręczne** przycisku. Pobierz plik .nupkg.

2. Zlokalizuj nowo pobrany plik i zmień rozszerzenie pliku z .nupkg do **.zip**. Powinno to umożliwić można wyświetlać i wyodrębniać dołączonych plików, takich jak dowolnego innego pliku zip.

3. Otwórz lub Wyodrębnij katalogu zip i przejdź do **\lib\net45**.

4. Kopiuj **Microsoft.Azure.Mobile.Client.dll** plik do projektu Unity **pakiety Assets\NuGet** katalogu.

>[!WARNING]
> Po wykonaniu tych kroków upewnij się ponownie uruchomić Unity i Visual Studio lub InteliSense nie może rozpoznać nowo dodanego pakietów.

## <a name="conclusion"></a>Wniosek

Po wykonaniu tych kroków, Unity projektu należy Instalatora, aby użyć zestawu SDK klienta usługi Azure Mobile. Należy przetestować środowiska deweloperskiego tworzenia nowego skryptu C# w projekcie platformy Unity, otwierając go w programie Visual Studio i wpisując następujące instrukcje using u góry:
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Jeśli InteliSense wykrywa te instrukcje using, instalacja została ukończona poprawnie. Jeśli wystąpią jakieś błędy lub InteliSense nie rozpoznaje te pakiety, ponowne uruchomienie Unity i Visual Studio. Jeśli nadal nie działa, należy ponownie powyższe kroki.

## <a name="next-step"></a>Następny krok

* [Tworzenie klasy modelu danych](visual-studio-tools-for-unity-azure-data.md)
