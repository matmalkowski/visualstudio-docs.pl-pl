---
title: REPL IPython w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: d33765a2c70f6c58759e2722b04d770b6f8822a6
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="using-ipython-in-the-interactive-window"></a>W oknie interaktywnym przy użyciu IPython

Okno interaktywne programu Visual Studio w trybie IPython jest zaawansowane środowisku jeszcze przyjazną dla użytkownika interaktywnego programowanie funkcje interaktywne przetwarzania równoległego. Ten temat przeprowadzi Cię przez przy użyciu IPython w okno interaktywne programu Visual Studio, w którym wszystkie zwykłej [okna interaktywnego](interactive-repl.md) funkcje są również dostępne.

W tym przewodniku powinny mieć [Anaconda](https://www.continuum.io) środowisko jest zainstalowane, w tym IPython i wymagane biblioteki.

> [!Note]
> IronPython nie obsługuje IPython, mimo że możesz wybrać je w formularzu Opcje interakcyjne. Aby uzyskać więcej informacji, zobacz [żądanie funkcji](https://github.com/Microsoft/PTVS/issues/84).

1. Otwórz program Visual Studio, Przełącz do okna środowiska Python (**Widok > inne okna > środowiska Python**) i wybierz środowisko Python, które wystąpiły podczas uruchamiania IPython.

1. Przyjrzyj się **pakiety** (lub **pip**) i upewnij się, że `IPython` i `matplotlib` są wyświetlane. Jeśli nie, zainstaluj je tutaj.

1. Wybierz **omówienie** i wybierz **IPython używany tryb interaktywny.** (W programie Visual Studio 2015, wybierz **skonfigurować opcje interakcyjne** można otworzyć **opcje** okna dialogowego, a następnie ustaw **trybie interaktywnym** IPython i wybierz **OK** ).

1. Wybierz **Otwórz okno interaktywne** można wyświetlić okno interaktywne w trybie IPython. Może być konieczne zresetowanie okna, jeśli zmienione zostały właśnie trybie interakcyjnym; może być również konieczne naciśnij klawisz Enter, jeśli tylko >>> pojawi się monit.

    ![Okno interaktywne w trybie IPython](media/ipython-repl-03.png)

1. Wprowadź następujący kod:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Po wprowadzeniu ostatniego wiersza, powinien zostać wyświetlony wykres wbudowany (które można zmienić rozmiar przez przeciągnięcie w prawym dolnym rogu) w razie potrzeby.

    ![Wykres wbudowany w oknie interaktywnym](media/ipython-repl-04.png)

1. Zamiast wpisywać w REPL, zamiast tego można napisać kod w edytorze, zaznacz go, kliknij prawym przyciskiem myszy i wybierz **wysłać do interaktywnego** polecenia (lub naciśnij klawisze Ctrl-Enter). Spróbuj wkleić poniższy kod do nowego pliku w edytorze, wybierając ją z Ctrl-A, a następnie wysyłanie do okna interaktywnego. (Należy pamiętać, Visual Studio i wysyła kodu jako jedna całość, aby uniknąć, umożliwiając wykresy pośredniego lub jego część. Należy również zauważyć, że jeśli nie masz otworzyć za pomocą innego środowiska wybrany projekt języka Python, Visual Studio otworzy interaktywnego okna dla niezależnie od środowiska jest wybrany jako domyślnego w **środowiska Python** okna.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![Wysyłanie kodu z edytora do okna interaktywnego](media/ipython-repl-05.png)

1. Aby zobaczyć wykresy poza okno interaktywne, uruchom kod zamiast przy użyciu **Debuguj > Uruchom bez debugowania** polecenia.

IPython ma wiele innych przydatnych funkcji, takich jak anulowanie powłoki systemu, podstawienie zmiennej przechwytywanie danych wyjściowych, itd. Zapoznaj się [dokumentacji IPython](http://ipython.org/documentation.html) Aby uzyskać więcej informacji.

## <a name="related-topics"></a>Tematy pokrewne

- Aby łatwo i bez konieczności instalacji Jupyter, spróbuj wolnych [usługi hostowanej platformy Azure, komputery przenośne](https://notebooks.azure.com/) umożliwia przechowywać i udostępniać innym użytkownikom notesy.

- Można również uruchomić Jupyter (wcześniej znane jako IPython) na własną maszynę wirtualną systemu Windows lub Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [tworzenie Azure maszyny Wirtualnej. Instalowanie Jupyter i działających na platformie Azure notesu Jupyter](/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).
