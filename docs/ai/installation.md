---
title: Instalowanie narzędzi AI programu Visual Studio
description: Instalacja narzędzi AI programu Visual Studio
keywords: AI, programu visual studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 4785bc8362d7e50b5fb48bf88df29313ddfcc0c8
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303112"
---
# <a name="installation"></a>Instalacja

Visual Studio Tools dla AI można zainstalować w systemie Windows 64-bitowych systemach operacyjnych.

## <a name="install-visual-studio-tools-for-ai"></a>Instalowanie narzędzi Visual Studio Tools for AI

To rozszerzenie współpracuje z programu Visual Studio 2015 i Visual Studio 2017, Community edition lub nowszy.

Aby zainstalować, Pobierz z [Visual Studio Marketplace](http://aka.ms/vstoolsforai) lub z poziomu programu Visual Studio

1. **Narzędzia** > **rozszerzenia i aktualizacje**

![Zainstaluj CUDA w systemie Windows](media\installation\extensions.png)

1. **Wyszukiwanie** w prawym górnym narożniku "Narzędzia dla AI"
2. Wybierz **Visual Studio Tools dla AI**
3. Kliknij przycisk **Pobierz**

## <a name="prepare-your-local-machine"></a>Przygotowanie komputera lokalnego

Przed szkolenia głębokie uczenia modele na komputerze lokalnym, który należy upewnić się, masz najnowsze odpowiednie wymagania wstępne zainstalowane. Dotyczy to również upewnić się, że najnowsze sterowniki i bibliotek NVIDIA GPU (jeśli istnieje). Należy również upewnić się, zainstalowano Python i Python biblioteki, takich jak NumPy, SciPy i odpowiednie bezpośrednich uczenia struktury, takich jak Microsoft kognitywnych Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch i/lub moduł, który planujesz użyć łańcucha w projekcie.

> [!NOTE]
> Wprowadzenie oprogramowania w poniższych podsekcjach jest fragmentem książki ich stron głównych.

### <a name="nvidia-gpu-driver"></a>Sterownik procesora GPU NVIDIA

Głębokie uczenia struktury zalet NVIDIA GPU, aby umożliwić maszyny informacje prędkością, dokładność i skalowanie na wartość true, analizy sztucznego. Jeśli komputer ma karty NVIDIA GPU, odwiedź stronę [tutaj](http://www.nvidia.com/Download/index.aspx) lub spróbuj przeprowadzić aktualizację systemu operacyjnego, aby zainstalować najnowszy sterownik.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) jest równoległego przetwarzania platformy i opracowana przez NVIDIA model programowania.
Umożliwia on znaczący wzrost przetwarzania danych wydajności przez wykorzystanie mocy procesora GPU.
Obecnie CUDA Toolkit 8.0 jest wymagany przez głębokie uczenia struktury.

Aby zainstalować CUDA

- Odwiedź witrynę [witryny](https://developer.nvidia.com/cuda-80-ga2-download-archive), Pobierz CUDA i zainstaluj go.
- Upewnij się, że do zainstalowania bibliotek środowiska uruchomieniowego CUDA, a następnie dodaj ścieżka binarna CUDA do % PATH % lub $Path zmiennej środowiskowej.
- W systemie Windows ta ścieżka jest "C:\Program Files\NVIDIA GPU obliczeniowych Toolkit\CUDA\v8.0\bin" domyślnie.

![Zainstaluj CUDA w systemie Windows](media\installation\install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (Biblioteka CUDA głębokie sieci neuronowe) to biblioteka przyspieszony GPU elementów podstawowych dla sieci neuronowej głębokość przez NVIDIA. cuDNN IPv6 jest wymagany przez najnowsze głębokie uczenia struktury.

Aby zainstalować cuDNN:

- Odwiedź stronę [NVIDIA Developer](https://developer.nvidia.com/rdp/cudnn-download) pobrać i zainstalować najnowszy pakiet.
- Upewnij się, aby dodać do katalogu zawierającego cuDNN binarnego na % % lub $Path zmiennej środowiskowej PATH.
- W systemie Windows możesz skopiować cudnn64_6.dll do "C:\Program Files\NVIDIA GPU obliczeniowych Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Poprzednie bezpośrednich uczenia struktury, takie jak CNTK 2.0 i TensorFlow 1.2.1 muszą cuDNN v5.1. Można jednak zainstalować wiele wersji cuDNN ze sobą.

### <a name="python"></a>Python

Python została podstawowy język programowania dla aplikacji do uczenia bezpośrednich. **64-bitowych** dystrybucję oprogramowania Python jest wymagana, i [Python 3.5.4](https://www.python.org/downloads/release/python-354/) zaleca się pod kątem zgodności.

### <a name="to-install-python-on-windows"></a>Aby zainstalować środowisko Python w systemie Windows

- Firma Microsoft sugeruje instalowanie uruchamiania Python tylko dla siebie i dodać Python do zmiennej środowiskowej % PATH %.
- Upewnij się, aby zainstalować narzędzia pip, który jest system zarządzania pakiet instalacji i zarządzaniu napisanych w języku Python pakietów oprogramowania.

Głębokie uczenia struktury polegają na pip ich instalacji.

![Instalowanie języka Python w systemie Windows](media\installation\install_python_win.png)

Następnie należy sprawdzić, czy Python 3.5 jest poprawnie zainstalowany, a następnie Uaktualnij pip do najnowszej wersji, wykonując następujące polecenia w terminalu:

- **Windows**
    ```cmd
    C:\Users\test>python -V
    Python 3.5.4

    C:\Users\test>pip3.5 -V
    pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

    C:\Users\test>python -m pip install -U pip
    ```

- **macOS**
    ```bash
    MyMac:~ test$ python3.5 -V
    Python 3.5.4

    MyMac:~ test$ pip3.5 -V
    pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

    MyMac:~ test$ python3.5 -m pip install -U pip
    ```

### <a name="python-on-visual-studio"></a>Python w programie Visual Studio

Python jest w pełni obsługiwany w programie Visual Studio za pomocą rozszerzeń.
Dowiedz się więcej na temat instalacji [języka Python dla programu Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) więcej szczegółów.

### <a name="numpy-and-scipy"></a>NumPy i SciPy

- **NumPy** jest ogólnego przeznaczenia pakietu przetwarzania tablicy umożliwia wydajne manipulowania dużych tablic wielowymiarowych dowolnego rekordów bez ograniczania zbyt dużo szybkość dla małych tablic wielowymiarowych.

- **SciPy** (Wymowa "Sigh kołowy") to oprogramowanie open source matematyce, nauki i zespołu inżynieryjnego, w zależności od NumPy. Począwszy od wersji 1.0.0, SciPy ma teraz pakiet wheel wbudowane oficjalnego dla systemu Windows.

Aby zainstalować NumPy i SciPy, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Powyżej uaktualnień polecenia istniejących starych lub nieoficjalny (np. pakiety innych firm z http://www.lfd.uci.edu/~gohlke/pythonlibs/ dla systemu Windows) NumPy i SciPy najnowsze te oficjalnego.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Kognitywnych zestaw narzędzi firmy Microsoft (CNTK)

[Kognitywnych zestaw narzędzi firmy Microsoft](https://cntk.ai) jest zestawem narzędzi learning bezpośrednich ujednoliconego opisuje sieci neuronowe jako serię kroków obliczeniową za pośrednictwem ukierunkowanego wykresu. CNTK obsługuje Python i BrainScript języków programowania.

> [!NOTE]
> CNTK nie obsługuje obecnie macOS.

Aby zainstalować pakiet języka Python CNTK, zobacz [jak zainstalować CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) Biblioteka oprogramowania typu open source do wartości liczbowych obliczeń przy użyciu wykresów przepływu danych. Zapoznaj się [tutaj](https://www.tensorflow.org/install/) szczegółowe instalacji.

> [!NOTE]
> Począwszy od wersji 1.2 TensorFlow już zapewnia obsługę GPU macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) to struktura lekkie, moduły i skalowalna learning bezpośrednich. Opierając się na oryginalnym Caffe, Caffe2 zaprojektowano z wyrażenia, szybkość i Modułowość zdanie.

Obecnie nie ma wbudowane pakietu kółka python Caffe2 dostępnej.

Odwiedź stronę [tutaj](https://caffe2.ai/docs/getting-started.html) do kompilacji z kodu źródłowego.

### <a name="mxnet"></a>MXNet

[Apache MXNet (pomocą inkubacji)](https://mxnet.incubator.apache.org/) to struktura głębokie nauki przeznaczony dla wydajność i elastyczność. Umożliwia on **mieszać** [programowania symboliczne i bezwzględne](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) do zwiększenia wydajności i produktywności.

Aby zainstalować MXNet, uruchom następujące polecenie w terminalu:

- Z procesora GPU
    ```bash
    pip3.5 install mxnet-cu80==0.12.0
    ```
- Bez procesora GPU
    ```bash
    pip3.5 install mxnet==0.12.0
    ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) to interfejs API sieci neuronowe wysokiego poziomu, napisany w języku Python i nadaje się do uruchamiania na górze CNTK, TensorFlow lub Theano. Został on opracowany z fokusem włączania szybkiego eksperymenty. Możliwość przejść z rozwiązaniem jest powoduje z opóźnieniem najniższe możliwe jest klucz do badania dobrej czynności.

Aby zainstalować Keras, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) biblioteka języka Python, która umożliwia definiowanie, optymalizacja i obliczać wyrażeń matematycznych wydajnie obejmujące tablic wielowymiarowych.

Aby zainstalować Theano, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](http://pytorch.org/) jest pakiet języka python, który zawiera dwie funkcje wysokiego poziomu:

- Obliczenia tensor (na przykład numpy) z silne przyspieszenie procesora GPU
- Głębokie sieci neuronowe oparty na systemie autograd opartej na taśmach

Aby zainstalować PyTorch, uruchom następujące polecenie w terminalu:

- **Windows**
    - Jeszcze nie będzie żadnych pakietu oficjalnego kółka. Możesz pobrać innych firm [Anaconda PyTorch pakietu](https://anaconda.org/pytorch/repo?type=all).
    - Dekompresja go do katalogu macierzystego, np. "C:\Users\test\pytorch".
    - Dodaj "C:\Users\test\pytorch\Lib\site-packages" do zmiennej środowiskowej % PYTHONPATH %.

- **macOS**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
    ```
    > [!NOTE]
    > System macOS plików binarnych nie obsługuje CUDA, zainstalować ze źródła, jeśli jest potrzebny CUDA

- **Linux**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
    ```
    > [!NOTE]
    > Pojedynczy pakiet obsługuje zarówno procesora GPU i procesora CPU.

Na koniec należy zainstalować torchvision z systemem innym niż Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Moduł łańcucha

[Moduł łańcucha](https://chainer.org/) to struktura opartych na języku Python głębokie learning zmierzających elastyczność. Umożliwia automatyczne rozróżnienie na podstawie interfejsów API **podejście zdefiniuj przez uruchomienie** () dynamiczne wykresy obliczeniową) oraz zorientowane obiektowo wysokiego poziomu interfejsów API, aby skompilować i uczenie sieci neuronowej.

Aby włączyć obsługę CUDA, zainstaluj [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> W systemie Windows, należy wersji 2015 [programu Visual Studio](https://visualstudio.microsoft.com/) lub [Microsoft Visual C++ kompilacji narzędzia](https://visualstudio.microsoft.com/visual-cpp-build-tools/) skompilować CuPy z CUDA 8.0.

Aby zainstalować moduł łańcucha, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install chainer==3.0.0
```