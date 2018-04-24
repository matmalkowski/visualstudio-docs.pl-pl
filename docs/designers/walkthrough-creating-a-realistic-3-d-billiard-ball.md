---
title: 'Wskazówki: Tworzenie piłka realistyczne bilardowe 3D'
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bd12e380a9362a82ff890dd016e5469e30f136a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Wskazówki: Tworzenie piłka realistyczne bilardowe 3D

Ten przewodnik przedstawia sposób tworzenia piłka realistyczne bilardowe 3D przy użyciu projektanta programu do cieniowania i edytor obrazów programu Visual Studio. Wygląd 3D piłka bilardowe odbywa się przez połączenie z zasobami tekstury odpowiednie kilka technik programu do cieniowania.

## <a name="prerequisites"></a>Wymagania wstępne

Niezbędne są następujące składniki i umiejętności w tym przewodniku:

-   Narzędzie do zebrania tekstury w mapie modułu, takiego jak narzędzie tekstury DirectX, który znajduje się w czerwcu 2010 DirectX SDK.

-   Ponadto z edytor obrazów programu Visual Studio.

-   Znajomość projektanta programu do cieniowania w programie Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Utwórz podstawowe wygląd z kształtu i tekstury

W komputerze grafiki elementy basic większość wygląd to kształt i kolor. W symulacji komputera jest wspólne używa modelu 3D do reprezentowania kształtu obiektu rzeczywistych. Szczegóły koloru jest następnie stosowany do powierzchni modelu przy użyciu mapy tekstury.

Zazwyczaj może być konieczne poproszenie wykonawcy można utworzyć modelu 3D, którego można używać, ale ponieważ piłka bilardowe jest typowe (kuli), Projektant programu do cieniowania ma już odpowiedni model wbudowane.

Kuli jest domyślnego kształtu Podgląd w projektancie programu do cieniowania; Jeśli obecnie używasz inny kształt do podglądu programu do cieniowania, przełącz się do sfery.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Aby wyświetlić podgląd programu do cieniowania przy użyciu kuli

-   Na pasku narzędzi programu do cieniowania Designer wybierz **Podgląd o zakresie.**

 W następnym kroku utworzysz program cieniowania, który dotyczy tekstury modelu, ale najpierw należy utworzyć tekstury, którego można używać. W tym przewodniku pokazano, jak utworzyć tekstury za pomocą edytora obrazu, który jest częścią programu Visual Studio, ale można użyć dowolnego edytora obrazu, który można zapisać tekstury w odpowiednim formacie.

 Upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Aby utworzyć tekstury piłka bilardowe za pomocą edytora obrazów

1.  Utwórz tekstury do pracy z. Aby uzyskać informacje o sposobie dodawania tekstury do projektu, w sekcji wprowadzenie w [edytor obrazów](../designers/image-editor.md).

2.  Ustaw rozmiar obrazu, aby jego szerokość jest dwukrotnie wysokość; jest to konieczne ze względu na sposób, że tekstury jest mapowana na powierzchnię kulistego kuli bilardowe. Aby zmienić rozmiar obrazu, w **właściwości** okna, określ nowe wartości dla **szerokość** i **wysokość** właściwości. Na przykład ustawić szerokość 512 i wysokości do 256.

3.  Rysuj tekstury piłka bilardowe, pamiętając o jak tekstury jest mapowany na kuli.

     Tekstury powinny wyglądać podobnie do poniższego:

     ![Tekstury piłka bilardowe](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png "gfx_shader_demo_billiard_art_ball_texture")

4.  Opcjonalnie można zmniejszyć wymagania dotyczące magazynu z tej struktury. Możesz to zrobić, zmniejszając szerokość tekstury, aby dopasować wysokość. To kompresuje tekstury wzdłuż szerokości, ale ze względu na sposób, że tekstury jest mapowany na kuli, będą rozszerzane, podczas renderowania piłka bilardowe. Po zmianie rozmiaru, tekstury powinny wyglądać podobnie do poniższego:

     ![Tekstura bilardowe skompresowane w kwadrat](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png "gfx_shader_demo_billiard_art_ball_texture_square")

 Teraz można utworzyć programu do cieniowania, którego dotyczy ten tekstury modelu.

### <a name="to-create-a-basic-texture-shader"></a>Aby utworzyć cieniowania tekstury podstawowej

1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).

     Domyślnie wykres programu do cieniowania wygląda następująco:

     ![Wykres programu do cieniowania domyślne](../designers/media/gfx_shader_demo_billiard_step_0.png "gfx_shader_demo_billiard_step_0")

2.  Modyfikowanie domyślnego programu do cieniowania tak, aby dotyczył wartość próbki tekstury bieżącego piksela. Wykres programu do cieniowania powinien wyglądać następująco:

     ![Wykres programu do cieniowania stosowanego tekstury dla obiekt](../designers/media/gfx_shader_demo_billiard_step_1.png "gfx_shader_demo_billiard_step_1")

3.  Zastosuj tekstury, utworzony w poprzedniej procedurze, konfigurując właściwości tekstury. Ustaw wartość **tekstury** właściwość **próbki tekstury** węzeł, aby **Texture1**, a następnie wskaż plik tekstury za pomocą **Filename**właściwość **Texture1** grupy właściwości w tym samym oknie właściwości.

 Aby uzyskać więcej informacji dotyczących sposobu stosowania tekstury w sieci programu do cieniowania, zobacz [porady: Tworzenie podstawowego cieniowania tekstury](../designers/how-to-create-a-basic-texture-shader.md).

 Twoje piłka bilardowe powinna wyglądać podobnie do poniższego:

 ![Closeup kuli teksturą bilardowe](../designers/media/gfx_shader_demo_.png "gfx_shader_demo_")

## <a name="create-depth-with-the-lambert-lighting-model"></a>Utwórz głębokość z modelem oświetlenia Lambert

Po utworzeniu tej pory piłka bilardowe łatwo rozpoznać. Jednak pojawi się płaski i postrzegać — podobnie jak obraz kreskówki kuli bilardowe niż przekonująco repliki. Płaski wygląd jest wynikiem simplistic cieniowania, który zachowuje się tak samo światła odbiera każdego piksela na powierzchni piłka bilardowe.

 W świecie rzeczywistym jasny pojawi się najjaśniejsza na powierzchni, które bezpośrednio dostęp do źródła światła i pojawi się mniej jasny na powierzchni, które są pod kątem oblique do źródła światła. Jest to spowodowane energii w światła promienie będzie rozmieszczona na najmniejszą powierzchni po powierzchni bezpośrednio skierowany źródła światła. Podczas uruchamiania powierzchni po stronie źródła światła, takiego poziomu energii jest dystrybuowana do coraz większe powierzchni. Powierzchnię skierowany w kierunku od źródła światła odbiera nie światła energii na wszystkich powodujące całkowicie ciemny wyglądu. Ta wariancji w jasności po powierzchni obiektu jest ważne wizualnie pomaga wskazać kształtu obiektów. bez tego płaski wygląd obiektu.

 W komputerze grafiki *modeli oświetlenia*— uproszczony przybliżenia interakcje oświetlenia złożone, rzeczywistych — są używane do replikowania wygląd rzeczywistych oświetlenia. Ilość światła rozpraszająco odbite różni się w modelu oświetlenia Lambert po powierzchni obiektu zgodnie z opisem w poprzednim akapicie. Model oświetlenia Lambert można dodać do programu do cieniowania umożliwiają piłka bilardowe więcej przekonująco wygląd 3D.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Aby dodać oświetlenia Lambert do programu do cieniowania

-   Zmodyfikuj Twojego programu do cieniowania dostosowanie wartość próbki tekstury przez wartość Lambert oświetlenia. Wykresie programu do cieniowania powinien wyglądać następująco:

     ![Wykres programu do cieniowania oświetlenie Lambert dodane](../designers/media/gfx_shader_demo_billiard_step_2.png "gfx_shader_demo_billiard_step_2")

-   Opcjonalnie można dostosować zachowanie oświetlenia przez skonfigurowanie **MaterialDiffuse** właściwości wykres programu do cieniowania. Aby uzyskać dostęp do właściwości wykres programu do cieniowania, wybierz pustym obszarem powierzchni projektu, a następnie zlokalizuj właściwość, którą chcesz uzyskać dostęp w **właściwości** okna.

 Aby uzyskać więcej informacji dotyczących sposobu stosowania Lambert oświetlenia w sieci programu do cieniowania, zobacz [porady: Tworzenie podstawowego cieniowania Lambert](../designers/how-to-create-a-basic-lambert-shader.md).

 Oświetlenie Lambert zastosowane, Twoje piłka bilardowe powinny wyglądać podobnie do poniższego:

 ![Closeup kuli bilardowe teksturą i podświetlone](../designers/media/gfx_shader_demo_billiard_ball_2.png "gfx_shader_demo_billiard_ball_2")

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Ulepszanie wyglądu podstawowego z odblasków najważniejsze funkcje

Model oświetlenia Lambert zapewnia rozumieniu kształt i wymiarów, które były nieobecne w procesie tylko do tekstury. Jednak piłka bilardowe nadal ma nieco matowy wyglądu.

 Piłka rzeczywistych bilardowe ma zazwyczaj błyszczący zakończenia odzwierciedlający część światło, która znajduje się na nim. Niektóre zmiany zostaną uwzględnione powoduje światła odblasków najważniejsze funkcje, które symulować odbicia właściwości powierzchni. W zależności od właściwości zakończenia prezentuje może być zlokalizowana lub szerokie, intensywny lub niewielkie. Te odblasków odbić są modelowane przy użyciu relacji między źródła światła, orientację powierzchni i pozycji kamery — wyróżnienie jest najbardziej wymagających podczas orientację powierzchni odzwierciedla źródła światła bezpośrednio do kamera, i jest mniej intensywny gdy odbicie jest mniej bezpośredniego.

 Model oświetlenia Phong oparty na modelu oświetlenia Lambert uwzględnienie światła odblasków zgodnie z opisem w poprzednim akapicie. Model oświetlenia Phong można dodać do programu do cieniowania umożliwiają piłka bilardowe Zakończ symulowane, których wynikiem jest bardziej interesującego wyglądu.

### <a name="to-add-specular-highlights-to-your-shader"></a>Aby dodać światła odblasków do programu do cieniowania

1.  Zmodyfikuj Twojego programu do cieniowania do uwzględnienia przy użyciu dodatku mieszania udział odblasków. Wykresie programu do cieniowania powinien wyglądać następująco:

     ![Wykres programu do cieniowania z odblasków oświetlenia dodane](../designers/media/gfx_shader_demo_billiard_step_3.png "gfx_shader_demo_billiard_step_3")

2.  Opcjonalnie można dostosować sposób, który zachowuje odblasków przez skonfigurowanie właściwości odblasków (**MaterialSpecular** i **MaterialSpecularPower**) wykresu programu do cieniowania. Dostęp do właściwości wykresu programu do cieniowania, wybierz pusty obszar powierzchni projektu, a następnie w **właściwości** okna, odszukaj właściwość, którą chcesz uzyskać dostęp.

 Aby uzyskać więcej informacji dotyczących sposobu stosowania światła odblasków programu do cieniowania, zobacz [porady: Tworzenie podstawowego cieniowania Phong](../designers/how-to-create-a-basic-phong-shader.md).

 Wyróżnieniem odblasków zastosowane, Twoje piłka bilardowe powinny wyglądać podobnie do poniższego:

 ![Dodaje closeup kuli bilardowe z odblasków](../designers/media/gfx_shader_demo_billiard_ball_3.png "gfx_shader_demo_billiard_ball_3")

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Utwórz w pewnym sensie miejsca w czasie wykonywania odbicia środowiska

Z światła odblasków zastosowane Twoje piłka bilardowe wygląda bardzo przekonująco. Otrzymano właściwy kształt, zadania paint prawo i Zakończ prawo. Istnieje jednak nadal co więcej technika, który spowoduje, że Twoje piłka bilardowe wyglądu częścią jego środowiska.

 Należy zbadać piłka rzeczywistych bilardowe ściśle widać czy jego powierzchnię błyszczący nie tylko wykazują światła odblasków, ale również faintly odzwierciedla świata wokół obrazu. Można symulować tego odbicia jako teksturę przy użyciu obrazu środowiska i połączenie go z tekstury w modelu, aby określić ostateczny kolor każdego piksela. W zależności od rodzaju zakończenia, który ma, możesz łączyć bardziej lub mniej odbicie texture wraz z resztą programu do cieniowania. Na przykład użyć programu do cieniowania, która symuluje wysokiej odbicia powierzchni jak dublowania tylko tekstury odbicia, ale programu do cieniowania, która symuluje aspekty odbicia, takich jak znalezionego na kuli bilardowe może łączyć się tylko niewielką część odbicie wartość tekstury wraz z pozostałej części obliczenia programu do cieniowania.

 Oczywiście nie można po prostu zastosować odbite obrazu do modelu w taki sam sposób, że stosujesz mapy tekstury modelu. Jeśli tak, odbicie świecie były przenoszone z piłka bilardowe tak, jakby odbicie zostały zmiana koloru do niego. Ponieważ odbicie mogą pochodzić z dowolnym kierunku, należy sposobem Podaj wartość mapy odbicia dla dowolnego kąta i sposobem utrzymywania mapy odbicia ukierunkowane zgodnie ze świata. Aby spełnić te wymagania służy specjalny rodzaj mapy tekstury — o nazwie *mapy modułu*— zapewnia sześć tekstury rozmieszczone w formie strony modułu. Z wewnątrz tego modułu można wskazać w dowolnym kierunku, aby znaleźć wartości tekstury. Jeśli tekstury na każdej stronie modułu zawiera obrazów środowiska, poprzez próbkowanie właściwych lokalizacjach na powierzchni modułu można symulować żadnych odbicia. Utrzymywanie modułu wyrównane do środowiska, uzyskasz dokładnie odzwierciedla środowiska. Aby określić, gdzie będą próbkowane modułu, po prostu obliczyć odbicie wektor kamery poza powierzchni obiektu, a następnie użyć jej jako współrzędnych tekstury 3D. Za pomocą modułu mapowania w ten sposób jest typowe metody, która jest nazywany *mapowania środowiska*.

 Mapowanie środowiska zapewnia wydajne zbliżenia rzeczywistych odbić zgodnie z opisem w poprzednim akapicie. Wtopiły się odbić mapowane w środowisku, w sieci programu do cieniowania umożliwiają piłka bilardowe, który symulowane zakończenia dzięki piłka bilardowe prawdopodobnie więcej uziemione sceny.

 Pierwszym krokiem jest można utworzyć modułu mapy tekstury. W wielu różnych aplikacji zawartości mapy modułu nie muszą być idealne były skuteczne, szczególnie w przypadku odbicie jest delikatny lub nie zajmować wyraźne miejsca na ekranie. Na przykład wiele gier użyć wstępnie obliczonych modułu mapy do mapowania środowiska i użycia tylko jedną najbliższy każdego obiektu odbicia, mimo że oznacza to, że odbicie nie jest prawidłowy. Nawet nierównej zbliżenia często jest wystarczająca dla efektu przekonująco.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Aby utworzyć tekstury mapę środowiska przy użyciu edytora obrazów

1.  Utwórz tekstury do pracy z. Aby uzyskać informacje o sposobie dodawania tekstury do projektu, w sekcji wprowadzenie w [edytor obrazów](../designers/image-editor.md).

2.  Ustaw rozmiar obrazu, aby szerokość jest równa jego wysokości i jest potęgą liczby dwa rozmiar; jest to konieczne ze względu na sposób indeksowanego mapy modułu. Aby zmienić rozmiar obrazu, w **właściwości** okna, określ nowe wartości dla **szerokość** i **wysokość** właściwości. Na przykład, ustaw wartość **szerokość** i **wysokość** właściwości do 256.

3.  Wykorzystaj pełny kolor do wypełnienia tekstury. Ten tekstury będzie dołu Mapa modułu, która odpowiada powierzchni bilardowe tabeli. Pamiętać kolor, którego użyto do następnego tekstury.

4.  Utwórz drugi tekstury, który jest taki sam rozmiar jak pierwsze. Ta tekstury powtarza się z czterech stron mapy modułów, które odnoszą się do powierzchni i krawędzi tabeli bilardowe i do obszaru wokół tabeli bilardowe. Upewnij się, by narysować powierzchni tabeli bilardowe w tym tekstury przy użyciu tego samego koloru, tak jak tekstury dolnej. Tekstury powinny wyglądać podobnie do poniższego:

     ![Tekstura dla strony mapy sześciennej](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png "gfx_shader_demo_billiard_art_env_texture_side")

     Należy pamiętać, że mapa odbicia nie musi być photorealistic zadziałało; na przykład mapy modułu używany do tworzenia obrazów w tym artykule zawiera tylko cztery kieszeni zamiast sześć.

5.  Utwórz trzeci tekstury, który jest taki sam rozmiar jak innych. Ten tekstury będzie początku Mapa modułu, która odnosi się do limitu powyżej bilardowe tabeli. Aby ta część odbicie bardziej interesujące, można narysować narzutów światło wzmocnienie odblasków najważniejsze funkcje, które zostały dodane do programu do cieniowania w poprzedniej procedurze. Tekstury powinny wyglądać podobnie do poniższego:

     ![Tekstura najlepszych mapy sześciennej](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png "gfx_shader_demo_billiard_art_env_texture_top2")

 Teraz, po utworzeniu poszczególnych tekstury dla strony mapy modułu, można użyć narzędzia, aby połączyć je w mapy modułów, które mogą być przechowywane w jednym .dds tekstury. Można użyć dowolnego programu, aby utworzyć mapę modułu tak długo, jak może pomóc zaoszczędzić mapy modułu w formacie tekstury .dds. W tym przewodniku pokazano, jak utworzyć tekstury za pomocą narzędzia tekstury DirectX, które jest częścią 2010 czerwca zestawu SDK programu DirectX.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Aby utworzyć mapę modułu przy użyciu narzędzia tekstury DirectX

1.  W narzędziu tekstury DirectX w menu głównym wybierz **pliku**, **nowej tekstury**. **Nowej tekstury** zostanie wyświetlone okno dialogowe.

2.  W **typu tekstury** grupy, wybierz **tekstury mapy Sześciennej**.

3.  W **wymiarów** grupy, wprowadź prawidłową wartość dla **szerokość** i **wysokość**, a następnie wybierz pozycję **OK**. Zostanie wyświetlony nowy dokument tekstury. Domyślnie tekstury pokazywany jako pierwszy w dokumencie tekstury odpowiada **X dodatnią** modułu twarzy na obrazie.

4.  Ładowanie tekstury, utworzony dla strony modułu tekstury na powierzchni modułu. W menu głównym wybierz **pliku**, **otwarte na ten mapy Sześciennej krój**, wybierz utworzony dla strony modułu tekstury, a następnie wybierz pozycję **Otwórz**.

5.  Powtórz kroki od 4 do **ujemna X**, **Z dodatnią**, i **Z ujemną** modułu powierzchni. Aby to zrobić, możesz wyświetlić krój, który chcesz załadować. Aby wyświetlić inny moduł krój mapy, w menu głównym, wybierz **widoku**, **twarzy na obrazie mapy modułu**, a następnie wybierz krój, który chcesz wyświetlić.

6.  Dla **dodatnią Y** modułu krój, ładowanie tekstury, utworzony na początku modułu tekstury.

7.  Dla **ujemna Y** modułu krój, ładowanie tekstury, utworzonej dla dolnej części modułu tekstury.

8.  Zapisz tekstury.

 W pewnym sensie układ mapy modułu następująco:

 ![Układ mapy modułu środowiska](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png "gfx_shader_demo_billiard_art_env_texture_top")

 Obraz u góry jest dodatnią kroju modułu Y (+ Y); w środku, od lewej do prawej jest -X + Z, + X, a -Z modułu kroje; w dolnej części jest kroju modułu -Y.

 Teraz można zmodyfikować programu do cieniowania, aby dopasować próbki mapy modułu z pozostałą częścią programu do cieniowania.

### <a name="to-add-environment-mapping-to-your-shader"></a>Aby dodać środowiska mapowanie do programu do cieniowania

1.  Zmodyfikuj Twojego programu do cieniowania do uwzględnienia udziału mapowania środowiska przy użyciu dodatku mieszania. Wykresie programu do cieniowania powinien wyglądać następująco:

     ![Closeup zarówno rodzaj węzłach odbicia programu do cieniowania](../designers/media/gfx_shader_demo_billiard_step_4b.png "gfx_shader_demo_billiard_step_4b")

     Należy pamiętać, że można użyć **mnożenia dodać** węzeł, aby uprościć wykres programu do cieniowania.

     Poniżej przedstawiono bardziej szczegółowy widok węzłów programu do cieniowania, które implementuje mapowania środowiska:

     ![Wykres programu do cieniowania z mapowaniem środowiska dodane](../designers/media/gfx_shader_demo_billiard_step_4a.png "gfx_shader_demo_billiard_step_4a")

2.  Zastosuj utworzoną w poprzedniej procedurze przez skonfigurowanie właściwości tekstury modułu mapy tekstury. Ustaw wartość **tekstury** właściwość **próbki mapy Sześciennej** węzeł **Texture2**, a następnie wskaż plik tekstury za pomocą **Filename**właściwość **Texture2** grupy właściwości.

3.  Opcjonalnie można dostosować odbicia kuli bilardowe konfigurując **dane wyjściowe** właściwość **stałej** węzła. Dostęp do właściwości węzła, zaznacz go, a następnie w **właściwości** okna, odszukaj właściwość, którą chcesz uzyskać dostęp.

 Z mapowaniem środowiska zastosowane, Twoje piłka bilardowe powinny wyglądać podobnie do poniższego:

 ![Closeup środowiska mapowane piłka bilardowe](../designers/media/gfx_shader_demo_billiard_ball_4.png "gfx_shader_demo_billiard_ball_4")

 Do tego obrazu końcowego Zwróć uwagę, jak efekty, które zostały dodane grupuje utworzyć bardzo przekonująco piłka bilardowe. Kształt, tekstury i oświetlenia Tworzenie podstawowych wygląd obiektu 3D, a światła odblasków i odbić upewnij piłka bilardowe bardziej interesujące i wyglądać częścią jego środowiska.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Porady: zastosowanie programu do cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)