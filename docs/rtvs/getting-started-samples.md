---
title: "Przykładowe projekty do R narzędzi dla programu Visual Studio | Dokumentacja firmy Microsoft"
description: "Indeks kolekcji próbek, aby rozpocząć korzystanie z języka R i Visual Studio."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: f8bf96d4fcfdb29fdaf79fa5adba9b99375aaddd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>R Tools for Visual Studio przykładowych projektach

Ta kolekcja przykładów pobiera pracę na R, R narzędzi dla programu Visual Studio (RTVS) i Microsoft R Server:

1. Pobierz [pliku zip przykłady](https://github.com/Microsoft/RTVS-docs/archive/master.zip) i wyodrębnij do wybranego folderu.
1. Otwórz `examples/Examples.sln` aby zobaczyć dwa foldery w projekcie:

    - *Pierwszy przyjrzyj R* daje łagodne wprowadzenie nowym do R.
    - *PANI a Machine Learning* przedstawiono przykłady użycia języka R i Microsoft R Server dla usługi machine learning.

## <a name="a-first-look-at-r"></a>Pierwszy przyjrzeć się R

W tym przykładzie przedstawiono szczegółowe wprowadzenie do języka R za pośrednictwem liczne komentarze w dwóch plikach źródłowych. Najlepsze środowisko, umieść kursor na początku pliku i naciśnij klawisze Ctrl + Enter, aby wysłać kod wiersza za-znajdują się na **R interakcyjne** okna. (Wiersze, które zainstalować pakiety może potrwać minutę lub dwie do ukończenia).

- `1-Getting Started with R.R`obejmuje wiele podstawy R, w tym za pomocą pakietów, ładowanie i analizowanie danych i kreślenia.

    ![Przykładowe dane wyjściowe z uruchomiono pobierania 1 R.R próbki](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R`wprowadza pakietu graficzne ggplot2 znane powierzchni atrakcyjność i proste składni. W tym przykładzie wizualizuje trzęsienie ziemi danych z Fidżi.

    ![Przykładowe dane wyjściowe z 2 — wprowadzenie do ggplot2. Przykładowe R](media/samples-ggplot-output.png)

## <a name="microsoft-r-server-and-machine-learning"></a>Serwer R firmy Microsoft i uczenia maszynowego

Ta kolekcja przykładów przedstawia sposób użycia R w celu tworzenia modeli uczenia maszyny i aby móc korzystać z [Microsoft R Server (PANI)](http://aka.ms/rtvs-msft-r). Zainstaluj PANI na uruchamianie skryptów z `MRS` w tytule i jeśli nie zaznaczono inaczej.

Zgodnie z przykładami dla wszystkich, otwórz plik, umieść kursor na początku, a następnie krokowo kodu wiersz po wierszu z klawiszy Ctrl + Enter. Pliki markdown w każdym folderze również zawierać dodatkowe szczegóły.

- `Benchmarks`uruchamiają uzyska kilka obliczeń znacznym, równoległe algebraiczną skali liniowej, aby Pokaż wydajności, które są możliwe przy użyciu Microsoft R otwarte i biblioteki jądra matematyczne firmy Intel (MKL). Z danymi symulowane wzorców specjalnie porównać macierzach w jednym wątku lub dwa.

    ![Przykład testu porównawczego kreślenia](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`Tworzy model prognozowania żądanie dzierżawy roweru na podstawie historycznych zestawu danych za pomocą programu Microsoft Server R. 

- `Data_Exploration`zawiera trzy skrypty:

  - `Import Data from URL.R`Pokazuje, jak załadować plik danych identyfikowane przez adres URL do R.
  - `Import Data from URL to xdf.R`Pokazuje, jak załadować plik danych identyfikowane przez adres URL do serwera R Microsoft jako xdf. (Wymaga PANI).
  - `Using ggplot2.R`jest rozszerzeniem `A First Look at R/2-Introduction to ggplot2.R` próbki nadanie szerszej Przewodnik po funkcji ggplot2 w tym interakcyjne kreślenia 3D.

      ![Dane wyjściowe przy użyciu ggplot2. Przykład R](media/samples-3d-interactive.png)

- `Datasets`zawiera trzy `.csv` pliki używane przez inne przykłady
- `Flight_Delays_Prediction_with_R`i `Flight_Delays_Prediction_with_MRS` pokazano, jak do prognozowania opóźnienia transmitowane przy użyciu języka R, uczenie maszynowe i na czas w przeszłości i pogody danych. 
- `Machine learning`zawiera trzy próbki do uczenia się przewidzieć transmitowane opóźnienia, ceny obudowie i wynajem roweru. Razem te przykłady pokazują stosowanie R-Gratulacje, do rzeczywistych problemów. One również opisano, jak użyć kilku modeli uczenia popularnych maszyny i wdrażania ich jako usługi sieci Web platformy Azure przy użyciu [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) obszaru roboczego.

- `R_MRO_MRS_Comparison`znajduje się porównanie sześciu części zawierającej podobieństwa i różnice R, otwórz R firmy Microsoft i Microsoft R Server z poleceniami, składni, konstrukcji i wydajności.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Co to jest specjalna o Microsoft R otwarte i Microsoft R Server?

[Otwórz R Microsoft](http://aka.ms/rtvs-r-open), dystrybucja firmy Microsoft R, różni się od [R sieci CRAN](https://cran.r-project.org/) na dwa sposoby ważne:

1. [Lepsza wydajność obliczeń](https://mran.revolutionanalytics.com/rro/#intelmkl1) w przypadku użycia z [biblioteki jądra matematyczne Intel](https://software.intel.com/intel-mkl). Biblioteki są dostępne do pobrania bezpłatnie przez firmę Microsoft do użycia z programem Microsoft R otwarte.

1. [Odtworzenia Toolkit R](https://mran.revolutionanalytics.com/rro/#reproducibility) zapewnia, że biblioteki używany do tworzenia R program są zawsze dostępne dla innych osób, które mają być wydrukowana.

[Serwer R Microsoft](http://aka.ms/rtvs-msft-r) jest rozszerzeniem R, która pozwala na obsługę większej ilości danych i jego obsługa szybciej. Udostępnia zaawansowane możliwości R dwóch:

1. Większych zestawów danych bez ograniczeń pamięci RAM. PANI może przetwarzać dane braku pamięci z różnych źródeł, łącznie z hurtowni danych, bazy danych i klastry Hadoop.

1. Przetwarzanie równoległe, procesorami wielordzeniowymi. PANI można efektywną dystrybucję obliczeń na zasoby obliczeniowe dysponuje. Na stacji roboczej osobistych lub w klastrze zdalnego PANI przebiega szybciej odpowiedzi.

Poniższe porównanie pokazuje, że PANI i MRO z MKL mają znacznie lepszą wydajność obliczeń związanych z niektórych obliczania macierzy niż R i MRO bez MKL. Symulowane danych jest używany w obliczeniu:

![Porównanie PANI i MRO z MKL r i MRO bez MKL](media/samples-speed-comparison.png)

Porównanie techniczne R z MRO-Gratulacje, zapoznaj się z [Lixun Zhang szczegółowe omówienie](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) tematu.

Poniższa ilustracja następnie porównuje czas w sekundach stosowanego w budowania modeli Regresja logistyczna do prognozowania opóźnienia transmitowane więcej niż 15 minut.  Czas, który upłynął używane w sieci CRAN R znacznie zwiększa zwiększenie niewielkiej liczby wierszy, gdy PANI zwiększa się tylko około dwa razy. Aby uzyskać szczegółowe informacje o tym testów porównawczych, zapoznaj się `Benchmarks/rxGlm_benchmark.R` przykład.

![rxGlm testu porównawczego](media/samples-rxGLM-benchmark.png)
