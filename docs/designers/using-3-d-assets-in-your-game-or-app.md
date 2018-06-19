---
title: Korzystanie z zasobów 3D w aplikacji lub gry
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9ed78375438dd699959ce40a3427692ae1649af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917110"
---
# <a name="use-3d-assets-in-your-game-or-app"></a>Użyj 3D zasobów w aplikacji lub gry

W tym artykule opisano sposób korzystania programu Visual Studio do przetwarzania 3D zasobów i uwzględnić je w kompilacjach.

Po użyciu narzędzi w programie Visual Studio Utwórz zasoby 3D, następnym krokiem jest użycie ich w aplikacji. Ale przed użyciem, zasobów musi zostać przekształcone w formacie, który można poznać DirectX. W celu zmiany zasobów, program Visual Studio udostępnia dostosowania kompilacji dla każdego rodzaju zawartości, który może go utworzyć. Uwzględnienie zasoby w kompilacji, musisz wykonać będzie skonfigurować projekt użyj opcji dostosowania kompilacji, dodać zasoby do projektu i skonfigurować zasoby, używać dostosowania kompilacji poprawne. Po wykonaniu tej można załadować zasoby do aplikacji i używać ich tworzenie i wypełnianie zasobów DirectX, tak jak w dowolnej aplikacji DirectX.

## <a name="configure-your-project"></a>Konfigurowanie projektu

Przed wdrożeniem 3D zasobów w ramach kompilacji programu Visual Studio musi wiedzieć o rodzaju zasoby, które mają zostać wdrożone. Visual Studio zna już wielu popularnych typów plików, ale niektóre rodzaje aplikacji używają 3D zasoby, Visual Studio nie zakłada, że projekt zostanie skompilowany tych typów plików. Można określić, Visual Studio czy Twoja aplikacja korzysta z tego rodzaju zasoby przy użyciu *kompilacji dostosowania*— pliki, których program Visual Studio sposobu przetwarzania różnych typów plików w przystępny sposób — są dostarczane dla każdego typu zasobu. Ponieważ te dostosowania są stosowane na podstawie na projekt, musisz wykonać będzie Dodaj odpowiednie dostosowania do projektu.

### <a name="to-add-the-build-customizations-to-your-project"></a>Aby dodać do projektu dostosowania kompilacji

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **zależności kompilacji**, **kompilacji dostosowania**. **Pliki dostosowania kompilacji C++ Visual** zostanie wyświetlone okno dialogowe.

2.  W obszarze **dostępne pliki dostosowania kompilacji**, zaznacz pola wyboru, które odpowiadają typów zasobów, które ma być używany w projekcie, zgodnie z opisem w poniższej tabeli:

    |Typ zasobu|Nazwa dostosowania kompilacji|
    |----------------|------------------------------|
    |Tekstury i obrazów|**ImageContentTask (.targets, .props)**|
    |Modele 3D|**MeshContentTask (.targets, .props)**|
    |Programów do cieniowania|**ShaderGraphContentTask (.targets, .props)**|

3.  Wybierz **OK** przycisku.

## <a name="include-assets-in-your-build"></a>Obejmują zasoby w kompilacji
 Teraz, gdy projekt zna różnych rodzajów 3D zasobów, których chcesz użyć, następnym krokiem jest poinformuj go, które pliki są zasoby 3D i jakie rodzaje zasoby są.

### <a name="to-add-an-asset-to-your-build"></a>Aby dodać zasobu do kompilacji

1.  W **Eksploratora rozwiązań**w projekcie, otwórz menu skrótów zasób, a następnie wybierz **właściwości**. Element zawartości **strony właściwości** zostanie wyświetlone okno dialogowe.

2.  Upewnij się, że **konfiguracji** i **platformy** właściwości są ustawione na wartości, które mają zmiany dotyczą.

3.  W obszarze **właściwości konfiguracji**, wybierz **ogólne**, a następnie w siatce właściwości, w obszarze **ogólne**, ustaw **typu elementu** właściwości do typu elementu odpowiedniej zawartości potoku. Na przykład w pliku obrazu lub tekstury, wybierz opcję **potoku zawartości obrazu**.

    > [!IMPORTANT]
    > Domyślnie Visual Studio zakłada, że wiele rodzajów pliki obrazów powinny skategoryzowane przy użyciu **obrazu** elementu typu, który jest wbudowany w program Visual Studio. W związku z tym należy zmienić **typu elementu** właściwości każdego obrazu, który ma być przetwarzane przez potok zawartości obrazu. Innych typów zawartości w plikach źródłowych dla modeli 3D i domyślne grafiki visual programu do cieniowania do poprawnego potoku **typu elementu**.

4.  Wybierz **OK** przycisku.

Poniżej przedstawiono trzy typy plików, typy elementów zawartości potoku i ich skojarzonych źródłowych i danych wyjściowych.

|Typ elementu|Typy plików źródła|Format pliku wyjściowego|
|---------------|-----------------------|------------------------|
|**Potok zawartości obrazu**|Portable Network Graphics (.png)<br /><br /> JPEG (jpg, JPEG, jpe, JFIF)<br /><br /> Bezpośrednie powierzchni rysowania (.dds)<br /><br /> GIF (.gif)<br /><br /> Mapa bitowa (bmp, dib)<br /><br /> Format TIF (tif, TIFF)<br /><br /> Targa (.tga)|DirectDraw Surface (.dds)|
|**Potok zawartości siatki**|Plik AutoDesk FBX Interchange File (fbx)<br /><br /> Plik Collada DAE (DAE)<br /><br /> Plik OBJ czoła fali (.obj)|Plik siatki 3D (.cmo)|
|**Potok zawartości programu do cieniowania**|Wykres Visual programu do cieniowania (dgsl)|Dane wyjściowe programu do cieniowania skompilowanych (.cso)|

## <a name="configure-asset-content-pipeline-properties"></a>Skonfiguruj właściwości potoku zawartości zasobów

Można ustawić właściwości zawartości potoku, każdego pliku zasobów, dzięki czemu zostanie skompilowany w określony sposób.

### <a name="to-configure-content-pipeline-properties"></a>Aby skonfigurować właściwości zawartości potoku

1.  W **Eksploratora rozwiązań**w projekcie, otwórz menu skrótów dla pliku elementu zawartości, a następnie wybierz **właściwości**. Element zawartości **strony właściwości** zostanie wyświetlone okno dialogowe.

2.  Upewnij się, że **konfiguracji** i **platformy** właściwości są ustawione na wartości, które mają zmiany dotyczą.

3.  W obszarze **właściwości konfiguracji**, wybierz węzeł zawartości potoku — na przykład **potoku zawartości obrazu** tekstury i obrazów trwałych — a następnie w siatce właściwości ustaw właściwości odpowiednie wartości. Na przykład aby wygenerować mipmapy trwałego tekstury w czasie kompilacji, należy ustawić **Generowanie Mips** właściwości **tak**.

4.  Wybierz **OK** przycisku.

### <a name="image-content-pipeline-configuration"></a>Konfiguracja zawartości potoku obrazu

Korzystając z narzędzia potoku zawartości obrazu do tworzenia zasobów tekstury, można skompresować tekstury na różne sposoby, określają, czy poziomów Mipmapy powinny być generowane w czasie kompilacji, a następnie zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Kompresuj**|Określa typ kompresji używanej do pliku wyjściowego.<br /><br /> Dostępne opcje to:<br /><br /> -   **Brak kompresji**<br />-   **Kompresja BC1_UNORM**<br />-   **Kompresja BC1_UNORM_SRGB**<br />-   **Kompresja BC2_UNORM**<br />-   **Kompresja BC2_UNORM_SRGB**<br />-   **Kompresja BC3_UNORM**<br />-   **Kompresja BC3_UNORM_SRGB**<br />-   **Kompresja BC4_UNORM**<br />-   **Kompresja BC4_SNORM**<br />-   **Kompresja BC5_UNORM**<br />-   **Kompresja BC5_SNORM**<br />-   **Kompresja BC6H_UF16**<br />-   **Kompresja BC6H_SF16**<br />-   **Kompresja BC7_UNORM**<br />-   **Kompresja BC7_UNORM_SRGB**<br /><br /> Aby uzyskać informacje o kompresji, które są obsługiwane formaty w różnych wersjach programu DirectX, zobacz [przewodnik programowania w języku dla DXGI](http://go.microsoft.com/fwlink/p/?LinkId=246265).|
|Konwertuj na wstępnie pomnożonych format alfa|**Tak** konwersji obrazu wstępnie pomnożonych format alfa w pliku wyjściowym; w przeciwnym razie **nr**. Tylko plik wyjściowy zostanie zmieniona, obraz źródłowy jest bez zmian.|
|**Generowanie Mips**|**Tak** aby wygenerować pełny łańcuch MCI w czasie kompilacji i uwzględnić go w pliku wyjściowym; w przeciwnym razie **nr**. Jeśli **nr**i łańcuch mipmap zawiera już plik źródłowy plik wyjściowy będzie zawierał łańcuch MCI; w przeciwnym razie plik wyjściowy nie odniesie żaden łańcuch Mipmapy.|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:** zmiana rozszerzenia nazwy pliku wyjściowego pliku nie ma wpływu na jego format pliku.|

### <a name="mesh-content-pipeline-configuration"></a>Konfiguracja zawartości potoku siatki

Korzystając z narzędzia zawartości potoku siatka tworzenie zasobów sieci, można zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:** zmiana rozszerzenia nazwy pliku wyjściowego pliku nie ma wpływu na jego format pliku.|

### <a name="shader-content-pipeline-configuration"></a>Konfiguracja zawartości potoku programu do cieniowania

Korzystając z narzędzia potoku zawartości programu do cieniowania do tworzenia zasobów programu do cieniowania, można zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:** zmiana rozszerzenia nazwy pliku wyjściowego pliku nie ma wpływu na jego format pliku.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Załadować zasoby i używaj ich 3D w czasie wykonywania

### <a name="use-textures-and-images"></a>Użyj tekstury i obrazów

Direct3D udostępnia funkcje tworzenia zasobów tekstury. Programu Direct3D 11 Biblioteka narzędzi D3DX11 zapewnia dodatkowe funkcje do tworzenia widoków zasobów i zasoby tekstury bezpośrednio z plikami obrazów. Aby uzyskać więcej informacji na temat tworzenia zasobu tekstury programu Direct3D 11, zobacz [tekstury](http://go.microsoft.com/fwlink/p/?LinkID=246267). Aby uzyskać więcej informacji o sposobie używania biblioteki D3DX11 do utworzenia zasobu tekstury lub widok zasobów z pliku obrazu, zobacz [porady: Inicjowanie z pliku tekstury](http://go.microsoft.com/fwlink/p/?LinkId=246268).

### <a name="use-3d-models"></a>Modele 3D

Direct3D 11 nie zapewnia funkcje tworzenia zasobów z modeli 3D. Zamiast tego trzeba napisać kod odczytuje plik modelu 3D, a następnie tworzy wierzchołka i pod indeksem buforów, które reprezentują modelu 3D i wszystkie zasoby, które wymaga modelu — na przykład tekstury lub programów do cieniowania.

### <a name="use-shaders"></a>Użyj programów do cieniowania

Direct3D udostępnia funkcje tworzenia zasobów programu do cieniowania i powiązania ich do potoku grafiki programowalny. Aby uzyskać więcej informacji dotyczących sposobu tworzenia zasobów programu do cieniowania w Direct3D i powiązać go z potoku, zobacz [przewodnik programowania w języku dla HLSL](http://go.microsoft.com/fwlink/p/?LinkID=261521).

W potoku grafiki programowalny każdego etapu w potoku mogą dać kolejnego etapu w potoku wyników w taki sposób, który może zrozumieć formacie. Ponieważ projektanta programu do cieniowania można tworzyć tylko programów do cieniowania pikseli, to oznacza, że jest do aplikacji w taki sposób, aby upewnić się, że odbiera dane są w formacie, który oczekuje. Kilka etapów program cieniowania wystąpić przed programu do cieniowania pikseli i wykonania przekształcenia geometrycznych — programu do cieniowania wierzchołków, cieniowania powłoki programu do cieniowania domeny i programu do cieniowania geometrycznego. Etap tworzenia mozaiki nieprzewidywalnych występuje także przed programu do cieniowania pikseli. Niezależnie od tego, która z tych etapów bezpośrednio poprzedza programu do cieniowania pikseli musi udzielić jej wynik, w następującym formacie:

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

W zależności od używanych w sieci programu do cieniowania węzłów projektanta programu do cieniowania może być również konieczne udostępniać dodatkowe dane w formacie zgodnie z tych definicji:

```
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: eksportowanie tekstury zawierającej mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Informacje dotyczące używania potoku zawartości obrazu, aby wyeksportować tekstury, który zawiera wstępnie obliczonych mipmapy.|
|[Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Informacje dotyczące używania potoku zawartości obrazu, aby wyeksportować tekstury, zawierający wstępnie przemnożone wartości alfa.|
|[Instrukcje: eksportowanie tekstury do użycia z Direct2D lub aplikacjami JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Opisuje sposób eksportowania tekstury, które mogą być używane w aplikacji Direct2D lub JavaScript za pomocą potoku zawartości obrazu.|
|[Praca z zasobami 3D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera opis narzędzi edycji programu Visual Studio do tworzenia i manipulowania 3D zasoby, które obejmują tekstury i obrazów, modeli 3D i programów do cieniowania.|
|[Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)|Opisuje sposób eksportowania do cieniowania przy użyciu projektanta programu do cieniowania.|